The Sales OLAP Analytics System is a complete business intelligence system that implements Online Analytical Processing (OLAP) functionality in SQLite and Pandas. The system provides multidimensional analysis of sales data through three distinct OLAP architectures: ROLAP, MOLAP, and HOLAP. The implementation demonstrates basic OLAP operations like slicing, dicing, roll-up, and drill-down, providing actionable insights for sales performance analysis along multiple dimensions.

Database Schema Design
The system adopts a star schema pattern with one fact table and two dimension tables for analytical query performance optimization.

### Fact Table: sales
- sale_id: Unique identifier for each sales transaction (INTEGER, Primary Key)
- date: Date of sales transaction (DATE, Foreign Key)
- product_id: Product identifier (INTEGER, Foreign Key)
- quantity: Number of units sold (INTEGER)
- revenue: Total revenue generated from sale (DECIMAL)

### Dimension Tables

#### products Dimension
- product_id: Unique product identifier (INTEGER, Primary Key)
- category: Product classification category (TEXT)
- name: Product name (TEXT)
- price: Unit price of product (DECIMAL)

#### dates Dimension
- date: Calendar date (DATE, Primary Key)
- year: Year component (INTEGER)
- quarter: Quarter number (INTEGER)
- month: Month number (INTEGER)

## OLAP Architecture Implementations

### ROLAP (Relational)

The ROLAP implementation leverages SQL queries directly on the relational database to perform OLAP-style aggregations. Three key analytical queries were implemented:

1. **Average Revenue by Product Category**
   - Calculates the mean revenue across different product categories
   - Provides insights into category profitability

2. **Total Sales by Year**
   - Aggregates sales quantity and revenue by calendar year
   - Enables year-over-year performance analysis

3. **Best-selling Product in Each Category**
   - Identifies top-performing products within each category using window functions
   - Supports product performance benchmarking

### MOLAP (Multidimensional)

The MOLAP implementation utilizes Pandas pivot tables to create in-memory multidimensional cubes:

- **Revenue Cube**: Constructs a two-dimensional matrix with product categories as rows and years as columns
- **Aggregation Method**: Sums revenue values across the category-year intersections
- **Storage**: Maintains the cube in memory for fast analytical operations

### HOLAP (hybrid)

The HOLAP approach combines the strengths of both ROLAP and MOLAP architectures:

- **ROLAP Component**: Executes SQL queries to extract detailed transactional data
- **MOLAP Component**: Uses Pandas for in-memory aggregation and multidimensional analysis
- **Integration**: Provides both detailed record access and fast aggregated analysis

## OLAP Operations Implementation

### Slice Operation
Implementation: Fixed the time dimension to isolate sales data for the year 2024 only.
Purpose: Enables focused analysis on a specific time period by reducing dimensionality.

### Dice Operation
Implementation: Applied multiple concurrent filters including year (2024), quarter (Q1), and product category (Electronics).
Purpose: Creates a focused data subcube with specific constraints across multiple dimensions.

### Roll-Up Operation
Implementation: Demonstrated hierarchical aggregation through three levels:
1. Product-level detail 
2. Category-level aggregation
3. Year-level summary 
Purpose: Enables progressive data summarization along dimension hierarchies.

### Drill-Down Operation
Implementation: Navigated temporal hierarchy from year view to quarter view to month view.
Purpose: Provides progressive detail exploration from summarized to granular data.

## Visualization Components
1. **Category Revenue Analysis**: Bar chart displaying average revenue distribution across product categories
2. **Sales Cube Heatmap**: Visual representation of the MOLAP cube showing revenue patterns across category-year combinations
3. **Temporal Trend Analysis**: Line chart illustrating revenue trends across years
4. **Comparative Analysis**: Multi-series bar chart comparing category performance across different years

## Technical Architecture

### Data Layer
- SQLite database for persistent storage
- Star schema design optimized for analytical queries
- Foreign key relationships maintaining referential integrity

### Processing Layer
- Pandas DataFrame operations for in-memory processing
- SQL query execution for database operations
- Pivot table construction for multidimensional analysis

### Presentation Layer
- Matplotlib and Seaborn for data visualization
- Structured console output for query results
- Formatted analytical summaries

## Implementation Details

### Data Generation
The system includes synthetic sales data spanning multiple years with realistic distribution across product categories. The dataset includes:
- Multiple product categories i.e Electronics, Clothing, Books
- Temporal coverage across different years and quarters
- Varied sales quantities and revenue amounts

### Query Optimization
- Utilized SQL aggregate functions for efficient ROLAP operations
- Implemented window functions for ranking and comparative analysis
- Employed Pandas groupby operations for flexible data aggregation

### Performance Considerations
- IFor MOLAP operations, in-memory processing guarantees quick reaction times.

- Join operations are optimized by database indexing on dimension keys.

- Repeated analytical operations are improved by pivot table caching.


## Business Applications

 - Several business intelligence use cases are supported by this OLAP system:

 -Tracking sales performance for various product categories

 -Analysis of temporal trends for strategic planning

- Benchmarking of product performance

- Identification of seasonal sales patterns

- Forecasting revenue using past trends

##QUERIES
<img width="832" height="571" alt="image" src="https://github.com/user-attachments/assets/73f4ae78-8854-45b5-b136-227c055247c2" />
<img width="968" height="419" alt="image" src="https://github.com/user-attachments/assets/abbdb232-768f-406f-bace-ebf91ccff5a2" />

##PLOTS
<img width="859" height="545" alt="image" src="https://github.com/user-attachments/assets/6c647376-877f-4688-977d-de61a401ef12" />
<img width="658" height="545" alt="image" src="https://github.com/user-attachments/assets/493b05e1-b1ec-45f5-a98f-414df5e99ed3" />
<img width="859" height="545" alt="image" src="https://github.com/user-attachments/assets/e96d5d42-ea54-4e2c-99e1-9bd417ed78a5" />
<img width="859" height="545" alt="image" src="https://github.com/user-attachments/assets/c7ad0aa1-ebdd-4130-a41d-75e1e7932a5d" />






