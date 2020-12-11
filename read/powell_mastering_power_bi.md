# Mastering Microsoft Power BI: Expert techniques for effective data analytics and business intelligence
### Brett Powell <!-- omit in toc -->
### 1788297237 <!-- omit in toc -->

- [Mastering Microsoft Power BI: Expert techniques for effective data analytics and business intelligence](#mastering-microsoft-power-bi-expert-techniques-for-effective-data-analytics-and-business-intelligence)
  - [Chapter 1 - Planning Power BI Projects](#chapter-1---planning-power-bi-projects)
  - [Chapter 2 - Connecting to Sources and Transforming Data with M](#chapter-2---connecting-to-sources-and-transforming-data-with-m)
  - [Chapter 3 - Designing Import and DirectQuery Data Models](#chapter-3---designing-import-and-directquery-data-models)
  - [Chapter 4 - Developing DAX Measures and Security Roles](#chapter-4---developing-dax-measures-and-security-roles)
  - [Chapter 5 - Creating and Formatting Power BI Reports](#chapter-5---creating-and-formatting-power-bi-reports)
  - [Chapter 6 - Applying Custom Visuals, Animation, and Analytics](#chapter-6---applying-custom-visuals-animation-and-analytics)
  - [Chapter 7 - Designing Power BI Dashboards and Architectures](#chapter-7---designing-power-bi-dashboards-and-architectures)
  - [Chapter 8 - Managing Application Workspaces and Content](#chapter-8---managing-application-workspaces-and-content)
  - [Chapter 9 - Managing the On-Premises Data Gateway](#chapter-9---managing-the-on-premises-data-gateway)
  - [Chapter 10 - Deploying the Power BI Report Server](#chapter-10---deploying-the-power-bi-report-server)
  - [Chapter 11 - Creating Power BI Apps and Content Distribution](#chapter-11---creating-power-bi-apps-and-content-distribution)
  - [Chapter 12 - Administering Power BI for an Organization](#chapter-12---administering-power-bi-for-an-organization)
  - [Chapter 13 - Scaling with Premium and Analysis Services](#chapter-13---scaling-with-premium-and-analysis-services)

## Chapter 1 - Planning Power BI Projects

- Power BI Desktop (PBID) shares the same data retrieval and modeling engines as SQL Server Analysis Services (SSAS) and Azure Analysis Services
- Discussion over data set and visualization ownership:
  - Each component can be owned by IT or business and has trade-offs
  - The more IT, the more secure and standard, the more business, the more flexibility and speed in creation
- It is most efficient (other than in Proof of Concept) to assign individuals to one of three groups:
  - Dataset designers: to create DAX measures, model table relations, access the data directly
  - Report Authors: to create reports and visualizations, interact with admins, prepare content distribution
  - Power BI Admins: interact with business, maintain security, allocate licensing
- Pro vs. Free licenses table on pg. 20
- Granularity of fact tables tends to be the biggest determiner of query speed and end user interactivity (more granular, more dimensions, slower)
- If the transformations from the original data to the final become increasingly complex, it is advantageous to push that processing to the data warehouse (dw) rather than Power BI (PBI) queries, DAX measures, or DAX calculated tables/columns
- One method for compatibility is to use SQL server views as the source of PBI queries, this will likely reduce the changes that break imports and can reduce complexity
- Import vs. DirectQuery:
  - Import: generally preferred if the dataset is ill-equipped to handle high volumes of analytical queries or if multiple resources are required and cannot be consolidated in DirectQuery directly
  - DirectQuery: near real time analytics
  - Some questions to guide the decision:
    - Is there a single source that supports DirectQuery?
      - If yes, is this source capable of handling the analytical volume?
    - Is an import mode feasible given the size of the dataset?
      - Limited to 10GB in import mode
        - If far larger, DirectQuery will be needed (or a Live connection to Analysis Services)
      - Premium offers 48 refreshes daily, Pro offers 8
- Import:
  - Stores a snapshot of the data in cloud service, and stores a compressed model in in memory for speed
  - SQL, M, and views modifications are made during the scheduled execution, thus speeding up the viewing on the front end after loaded
- DirectQuery:
  - Limited to a single data source
  - Eliminates the cloud snapshot and leverages the computing resources of the source

## Chapter 2 - Connecting to Sources and Transforming Data with M

- Import mode allows for the scaling of arithmetic operators as it takes advantage of the xVelocity storage engine's multithreaded processes
- DirectQuery DAX expressions should limit data transformations as the resulting SQL may negatively impact performance
- Import mode dataset queries:
  - Depending on the source resources, well-designed retrieval processes can benefit greatly from the compression algorithms applied to import mode datasets
  - If M queries can be translated into equivalent SQL statement, the model can use source resources during the query folding process
    - If not, they will either be evaluated by the on-premises data gateway using the in memory M engine or by Power BI Premium capacity hardware
  - M queries may be only partially folded, as is the case when SQL is used for simple transformations like filtering and M is used for more complex, subsequent steps like a custom function
- DirectQuery dataset queries:
  - Only run upon the single source's resources, and as such do not support the same level of folding and complex transformations
  - Common functions like data type conversion and sorting can cause significant performance degradation
- Data sources that are in beta should only be used for testing as changes in the design of the connector may lead to substantial functional changes
- Authentication credential are saved for each connection in Power BI, but are not stored in the .pbix file, rather on the local machine
- Data source settings menu allows access to all the current connection credentials and privacy levels (and the saved permissions for all the user's .pbix files)
- Privacy levels:
  - This are defined per connection and can dramatically affect the execution path
    - E.g. a local, sensitive .csv and a public database. Although merging and computing on the database is likely faster, maybe the data cannot be sent out of the organization. As such, you could define the .csv as private and the database as a public level
  - Public: cannot accept private or organizational sources, but may be transferred to an organizational source. Accessible to other public sources
  - Organizational: isolated from public data but visible to those in the same level
  - Private: isolated from all other sources, cannot transfer to other sources nor can it accept public sources
  - None: inherited from the source if it is already defined, or not applied if not defined
  - Default is to the none level
- CURRENT FILE options:
  - Set per .pbix file and are important for dataset creation
  - Allows for options like Auto Datetime and Parallel Loading
- It is often preferable to create SQL views and then write your queries to access these views rather than the database tables themselves
- Data retrieval should strive to leverage data source resources
  - This will lead to faster queries and remove the resource constraint on the data gateway or other local hardware
- Standardizing data sources and pushing simple transformations back to the data source allows for greater interoperability in other use cases and a single organizational source of truth
- Mark As Date function can only mark a column as the date column if it has:
  - No null values
  - No duplicate values
  - Contiguous date values from start date to end date
- Data Source Parameters:
  - Parameters are M queries that function like global variables do in many other languages
  - Used to define a specific scalar or individual value (like date, or a database name)
  - Typically these are not loaded into the data model, but they can be loaded as a single column table and then referenced with DAX as normal
- Staging Queries:
  - Can accept parameters (like a database name) and expose objects, file paths, and other simple calculations to then be used by the fact and dimension tables
  - Sometimes it is preferable to keep this in M queries (such as fast prototyping and rapid iteration), while other times it is preferable to keep the calculations (like date filters) in the SQL views themselves for speed and resource allocation
- Data Types:
  - PBI data types are determined automatically when importing from structured data sources like SQL
    - E.g. a SQL type of integer would result in a PBI type of whole number
- Bridge tables can be created from other tables in the data model and can be hidden from the user
  - E.g. a product sales table may have 100 item numbers each with 5 sales, the bridge table can select the distinct item numbers and act as the unique side of a one-to-many
- Query folding is limited by the data source that is being accessed, databases like SQL Server and Oracle DB offer the most, while .csv and Excel offer none
- R scripts can be run from the Power Query editor and called out in M functions
  - Datasets must be set to public, and as such may not be suitable for all applications
- Visual Studio and VSCode offer integration with the M query language for editing purposes
  - VS can also run the .pq file that is generated inside the IDE once the SDK is installed

## Chapter 3 - Designing Import and DirectQuery Data Models

- Three main layers of a dataset:
  - M Queries:
    - Data access and data transformation
  - Data Model:
    - Relationships and metadata
  - DAX queries:
    - Calculation logic and security filters
- PBI datasets are an SSAS Data Model internally, and as such are different from PI reports
- Three main views: Relationship, Data, and Fields (as seen on the left hand side of the program)
- By not importing all columns and imbedding calculation logic with DAX queries, you can reduce the storage and import cost (at the expense of processing the DAX later on)
  - Keep in mind the cardinality of such columns, less cardinality the better the storage will be and scanning will be improved as well
- For simple DAX expressions (like sale price = quantity * unit price) it is advantageous in import mode to remove the calculated columns and bring the calculations into PBI, whereas DirectQuery benefits from placing the calculations in the data source
- Special attention should be paid to the numeric data types, if they can be whole number then default to that, if they are always a certain length then a fixed length decimal should be used, etc.
- _USERELATIONSHIP()_ : DAX function to use alternative relationships between fact - dimension tables, even those that are set as inactive
  - This can be used to do things like repurpose a date table for multiple relationships (like sales by due date, ship date, and posted date)
- Assume referential integrity:
  - Critical for DirectQuery performance
  - If enabled, _INNER JOIN_ statements will be sent to the source for those queries which rely on information from both tables
  - If disabled, _OUTER JOIN_ statements will be sent to the source to ensure that all necessary rows from the fact table are retrieved
- Return to pg. 122 for hierarchy discussion
- You can also set a custom sort order using a specified column from the dimension table (like month number rather than month text, that way you see the logical flow of dates rather than by alphabetical ordering)
- Measure groups can be created by:
  - Making a new table
  - Creating one or more dummy columns
  - Removing them from the report view
  - Adding measures as desired
- Once the report group has been made, DAX expressions can be stored therein, thus eliminating the need to put them on single dimension or fact tables. This has the benefit of grouping similar functions or those functions that rely on multiple tables
- DAX measures have a Home Table that is defined in the header
- It may be necessary or useful to base DAX expressions on other DAX expressions for more robust functionality
  - E.g. a sun of sales figures expression can be based on another expression that defines the granularity of the figures (such as by month). In this way, if the user selects a date and not the month as a whole, it will return blank as intended
- Relationships must have one side with uniqueness and must be unambiguous (i.e. cannot split to two tables then back to one and use both filters at the same time)
- In general, most relationships are single-direction and are typically the best choice
  - This can be overridden for bidirectional relationships, but there are DAX functions like _CROSSFILTER()_ that can do much the same without creating more complexity
- It is best practice to reduce "connecting flights" and to try to get single, direct relationships
  - This has a performance boosting effect as there are less scans needed
  - Typically means removing bridge or intermediary tables
- ``` CROSSFILTER('Table1'[Column1], 'Table2'[Column1], method) ```
  - Method can be OneWay, Both, or None
- Web URL Data Category can be used for tasks like sending emails to specific users
- Image URL Data Category can be used to expose images to report visualizations
- Barcode Data Category can be used on mobile devices to scan barcode items
- DMVs can be used in the same manner as SSAS to analyze memory and resource use
- HTAP: hybrid transactional and analytical processing

## Chapter 4 - Developing DAX Measures and Security Roles

- In order to test DAX performance you must use DAX Studio to see resource utilization
- Many of these topics are addressed in the "The Definitive Guide to DAX: Business…" book
- Security roles apply filter context to the data shown, and cannot be overridden by DAX
- You can test how a report will look with different report filters by using the View as roles command on the Modeling tab in Desktop
- Azure Active Directory (AAD) can be used to define the user security roles as needed
- Dynamic row-level security (DRLS) can also be used by calling the _USERPRINCIPALNAME()_ function
  - This function allows definition of a table that can be used as a filter context for dimension filtering
  - E.g. a user dimension table can be defined so User1 can only see Country1's data, this table will then be referenced when the function is called and they won't be able to see the Country2 data
- Tracing PBI with DAX Studio can be found on pg. 197

## Chapter 5 - Creating and Formatting Power BI Reports

- Report planning steps:
  - Identify the users or consumers of the report
  - Define the business question(s) that the report should answer or support
  - Confirm the dataset supports the business questions
  - Determine how the report will be accessed and the nature of any user interactivity
  - Draw a sketch of the report layout
- If a report is to have multiple pages, the first should be a summary with KPIs and the like, while subsequent pages are detailed analysis (3-4 pages should be the maximum)
- Reports can be created in the PBI Desktop app using the Live connection to PBI service datasets. This allows the user to create entirely new reports on the same dataset and when published it will run in parallel with any other reports that use the same dataset.
- Visualization best practices:
  - Avoid clutter and nonessential details
  - Provide simple, clear titles on visuals and pages
  - Position and group visuals to provide logical navigation across the canvas
  - Use soft, natural colors where possible
  - Avoid large blank spaces
- What-if Parameters:
  - Can be used to add a parameter for users to define and modify visuals
  - Defined in the Modeling tab
  - Can be used in the place of calculated columns and the like, but must be included in measures in order to be useful
- Custom slicer parameters:
  - A new table can be used to define a slicer visual
  - The user selected value can then be used in DAX measures as a parameter
  - For example, the user can select YTD, MTD, or Day and the measure will return the correct calculation based on the date type selected
  - _SELECTEDVALUE()_ and _SWITCH()_ can be used for such cases
  - This selected values could also be its own measure and then called in other functions, hence eliminating the need for each measure to have a ``` var = SELECTEDVALUE() ``` type logic before the remainder of the calculation
- Report page tooltips:
  - Can define an entire page for more interesting/useful tooltips infographics

## Chapter 6 - Applying Custom Visuals, Animation, and Analytics

- Drill-through report pages:
  - Can be defined to include extra information depending on the selection of the user, such as item cost and margin when the user selects a product
  - Add drill-through filters in the page in which will become a drill-through and include the fields that you wish to allow the drill-through on
    - These fields can be required to be unique or aggregated
- Bookmarks:
  - Can save a specified set of filters and drilldowns so other users can use the same view when they select the bookmark
  - Report specific, not user specific
  - The Selection Pane can help to hide pieces of information based on the bookmarks chosen (like hiding 3 text boxes and only showing 1 at a time as the correct bookmark is chosen to filter the report, thus giving it a title)
  - Spotlight can also be enabled by bookmark, thus giving a clear visual that is directly related to the bookmark (make sure to give it an intuitive name)
  - Custom visuals can be used to reference a bookmark by using the Link field in the Formatting pane
    - This allows the user to click on something like an image and the bookmark filters the report as the designer wishes
- View mode:
  - Cycles through the bookmarks like a presentation
- Some visualizations contain animation features like the scatter plot, this field is called Play Axis
- The custom visual Pulse Chart by Microsoft also has a Play Axis and allows for annotations during that play time, and also has a counter called Runner Counter that can be selected
  - Use a DAX measure to define the Runner Counter value (like Sales YTD)

## Chapter 7 - Designing Power BI Dashboards and Architectures

- Detailed comparison of Dashboards vs. Reports on pg. 328
- The standard KPI visual offers less configuration options than the Power KPI does and although it is more complex, it is preferred for its flexibility
- Layout:
  - Most important info should be positioned in the top-left with supporting tiles to the right and below
  - Maximize available space, whitespace is wasted
  - Try to minimize the user's need to scroll up-down or left-right
- Trailing months example using case:
  - ``` CASE WHEN DATEDIFF(MONTH, datetable.[Date], GETDATE()) IN (1,2,3) THEN 'Trailing 1-3 Months' ... ```
- Tiles can have custom links made to direct the user experience:
  - Accessible under the Edit Details
  - Select external link or what PBI object you wish to open
- Custom tiles can be added directly to the dashboard without pinning them from a report
  - Video, images, external links, text, etc.
- SSRS offers support for charts, maps, etc. once set up correctly
- Excel offers a plugin for PBI support as well and may be used to pin content, but it is recommended to transition data models to PBI
- An entire report can be pinned to a dashboard, including the slicers and drill-through capabilities
- Dashboards also can be configured for mobile viewing, allowing for two formats of the same data depending on device

## Chapter 8 - Managing Application Workspaces and Content

- Return to pg. 378 for information on REST API calls and usage
  - Requires and Azure Active Directory account and access
- Dashboards can be assigned a data classification (such as public, confidential, etc.) in the admin portal and custom defined (and linked to an external URL for additional info)
- Version Control:
  - PBI does not currently have versioning systems and is not likely to gain them soon
  - OneDrive for Business offers versioning history
    - This allows one active file with all versions accessible in history
  - M and DAX can be stored as .pq files and saved in a git repository or similar
- Fields can also include descriptions
  - Visible in the report editor
  - Modifiable in the Field Properties
- If connecting to a PBI file to DAX Studio, you can query against measures to see descriptions, names, definitions, etc.

## Chapter 9 - Managing the On-Premises Data Gateway

- Planning questions:
  - Where is the data that is being used by the PBI dataset?
  - Is the source available with a generally available data connector?
  - Is the data being imported to the service or directly accessed?
  - Will it require an on-prem gateway or a personal gateway?
- Admin questions:
  - Who will administer the gateway?
  - Which authentication will be used?
  - Which users are authorized to access the gateway?
  - Where will the recovery key be stored?
  - Who will be responsible for regular updates?
- Return to chapter for in depth setup information and guide

## Chapter 10 - Deploying the Power BI Report Server

- Not applicable to TGW, return if necessary
- 447-484

## Chapter 11 - Creating Power BI Apps and Content Distribution

- There are many methods of content distribution for Power BI:
  - Power BI apps
    - An app can only contain data from its related workspace, but needn't expose all the content
    - Return to pg. 488 for deep dive into deployment (already tested myself)
    - Can use AAD (Azure Active Directory) security groups
      - This is preferable to single user assignments
  - Embedded in custom applications
  - Sharing distinct dashboards or reports
    - If you share a dashboard, you also are automatically sharing the underlying reports that are pinned
  - Embedded in SharePoint Online
    - Requires Pro or Premium for users to view content
  - Email subscriptions
  - Data alerts
    - Allow the user to create custom email alerts based on information in a dashboard card (like going above a threshold)
  - Publish to web
  - Analyze in Excel
  - Live connections in Power BI Desktop
  - Windows Cortana
  - Microsoft Teams integration
- Microsoft Flow can also be used for sharing the same data alert across a team or set of individuals
  - Allows for custom templates and actions as well

## Chapter 12 - Administering Power BI for an Organization

- Skimmed chapter
- Currently administered in Austria (TGW) and thus is not necessary for now

## Chapter 13 - Scaling with Premium and Analysis Services

- Skimmed chapter
- Currently administered in Austria (TGW) and thus is not necessary for now
- Tips for data model optimization on pg. 582
-

14