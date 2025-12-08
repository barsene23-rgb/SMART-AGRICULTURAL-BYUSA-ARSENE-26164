## Database Structure
This is an Agricultural Management System that connects farmers with markets, tracks harvest production, manages storage facilities, monitors market prices, and records transactions. The system helps optimize the agricultural supply chain from farm to buyer while incorporating weather data for better planning.

 *FARMERS*

Stores farmer profiles including identification, contact details, location (district/sector/cell/village), farm size, crop preferences, and creditworthiness for financial assessment.


<img width="959" height="480" alt="farmers" src="https://github.com/user-attachments/assets/b01d901f-d111-4f49-9bda-8d45d662ff1b" />

*CROPS*

Maintains a catalog of crop types with their characteristics, storage requirements, shelf life, seasonal patterns, and price ranges to support inventory and pricing decisions.

<img width="954" height="238" alt="crops" src="https://github.com/user-attachments/assets/d475668f-6502-4cc4-8ac4-52a0a60500a9" />


*STORAGE_FACILITIES*

Tracks warehouse and storage locations with capacity, current usage, environmental conditions (temperature/humidity), facility type, and daily storage costs.

<img width="959" height="368" alt="storage facility" src="https://github.com/user-attachments/assets/abd9b80e-d3a1-4e5e-b6b9-c3fbfddde3c3" />


*HARVESTS*

Records each harvest batch from farmers, linking crops to storage facilities while tracking quantity, quality grade, harvest date, expected spoilage timeline, and current status

<img width="957" height="356" alt="harvest" src="https://github.com/user-attachments/assets/125dd47e-3e36-4cce-bf62-42575a381c79" />


*MARKET_PRICES*

Monitors real-time and historical crop prices across different markets, including demand/supply levels and price trends for market analysis.

<img width="957" height="413" alt="marketprice" src="https://github.com/user-attachments/assets/09af4dbb-b796-4dbe-975d-ecc0880e3579" />


*BUYERS*

Contains buyer information including type (wholesaler/retailer/processor), contact details, location, crop preferences, and payment reliability scores.

<img width="950" height="475" alt="buyers" src="https://github.com/user-attachments/assets/4eb977da-843a-454e-92a3-a477e79dbef8" />


*TRANSACTIONS*

Documents all sales transactions between harvests and buyers, tracking quantities, pricing, payment/delivery status, and mutual ratings for quality assurance.

<img width="959" height="358" alt="transaction" src="https://github.com/user-attachments/assets/915738b4-4916-4584-9783-a3c37c71c3d8" />

*WEATHER_INFO*

Captures weather data by district including temperature, rainfall, humidity, and 7-day forecasts to help farmers plan harvesting and storage activities.

<img width="943" height="272" alt="weather info" src="https://github.com/user-attachments/assets/52696afe-68df-4b86-bd8e-1f48be694304" />


 **ER Diagaram**
This Entity-Relationship Diagram shows how the Agricultural Management System connects farmers, crops, storage, and buyers. The diagram illustrates the flow from farm to market: FARMERS produce HARVESTS of CROPS, stored in STORAGE_FACILITIES, and sold via TRANSACTIONS to BUYERS. MARKET_PRICES tracks crop pricing trends, while WEATHER_INFO supports planning decisions. Lines between entities show relationships, with primary keys (PK) identifying records and foreign keys (FK) linking related tables.

<img width="461" height="229" alt="er diagram" src="https://github.com/user-attachments/assets/7fdcd2e1-c127-4093-93bc-52bb200dc656" />


## test results

*testing price analytics package*

<img width="950" height="458" alt="price analytics" src="https://github.com/user-attachments/assets/1b50d4ec-3159-4dc1-b5c3-3d332fbcb0fc" />

*testing credit_scores packages*

<img width="959" height="494" alt="creditscore" src="https://github.com/user-attachments/assets/3da6ed9b-4423-4ce8-ad18-20a84fd64753" />


*testing matching engines packages*

<img width="959" height="506" alt="matching engines" src="https://github.com/user-attachments/assets/bac5f31e-ed51-485b-a965-a962836cbe4e" />


*testing spoilage monitor package* 

<img width="959" height="458" alt="spoilage" src="https://github.com/user-attachments/assets/179af411-13f6-49fb-9b2f-776a63393653" />


*testing report generator package*

<img width="959" height="446" alt="report generator" src="https://github.com/user-attachments/assets/704d7c6c-1f21-42ce-ae67-adf565f285bf" />
