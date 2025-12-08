## DDL

**creating tables**


CREATE TABLE FARMERS (
    farmer_id NUMBER PRIMARY KEY,
    national_id VARCHAR2(50) UNIQUE NOT NULL,
    names VARCHAR2(100) NOT NULL,
    phone VARCHAR2(20),
    district VARCHAR2(50),
    sector VARCHAR2(50),
    cell VARCHAR2(50),
    village VARCHAR2(50),
    farm_size_hectares NUMBER,
    primary_crops VARCHAR2(100),
    registration_date DATE,
    credit_score NUMBER
);

CREATE TABLE CROPS (
    crop_id NUMBER PRIMARY KEY,
    crop_name VARCHAR2(100) UNIQUE NOT NULL,
    category VARCHAR2(50),
    avg_shelf_life_days NUMBER,
    optimal_storage_temp NUMBER,
    seasonal_pattern VARCHAR2(100),
    min_price NUMBER,
    max_price NUMBER,
    current_market_price NUMBER
);

CREATE TABLE STORAGE_FACILITIES (
    storage_id NUMBER PRIMARY KEY,
    location VARCHAR2(100),
    capacity_kg NUMBER,
    current_occupancy NUMBER,
    temperature NUMBER,
    humidity_level NUMBER,
    facility_type VARCHAR2(50),
    cost_per_day NUMBER
);

CREATE TABLE HARVESTS (
    harvest_id NUMBER PRIMARY KEY,
    farmer_id NUMBER NOT NULL,
    crop_id NUMBER NOT NULL,
    quantity_kg NUMBER,
    quality_grade VARCHAR2(20),
    harvest_date DATE,
    expected_spoilage_date DATE,
    storage_location VARCHAR2(100),
    storage_id NUMBER,
    status VARCHAR2(30),
    CONSTRAINT fk_harvests_farmers FOREIGN KEY (farmer_id) REFERENCES FARMERS(farmer_id),
    CONSTRAINT fk_harvests_crops FOREIGN KEY (crop_id) REFERENCES CROPS(crop_id),
    CONSTRAINT fk_harvests_storage FOREIGN KEY (storage_id) REFERENCES STORAGE_FACILITIES(storage_id)
);

CREATE TABLE MARKET_PRICES (
    price_id NUMBER PRIMARY KEY,
    crop_id NUMBER NOT NULL,
    market_location VARCHAR2(100),
    price_per_kg NUMBER,
    date_recorded DATE,
    demand_level VARCHAR2(30),
    supply_level VARCHAR2(30),
    price_trend VARCHAR2(30),
    CONSTRAINT fk_marketprices_crops FOREIGN KEY (crop_id) REFERENCES CROPS(crop_id)
);

CREATE TABLE BUYERS (
    buyer_id NUMBER PRIMARY KEY,
    buyer_name VARCHAR2(100),
    buyer_type VARCHAR2(50),
    phone VARCHAR2(20),
    location VARCHAR2(100),
    preferred_crops VARCHAR2(100),
    payment_reliability_score NUMBER
);

CREATE TABLE TRANSACTIONS (
    transaction_id NUMBER PRIMARY KEY,
    harvest_id NUMBER NOT NULL,
    buyer_id NUMBER NOT NULL,
    quantity_kg NUMBER,
    agreed_price NUMBER,
    transaction_date DATE,
    payment_status VARCHAR2(30),
    delivery_status VARCHAR2(30),
    quality_rating NUMBER,
    farmer_rating NUMBER,
    buyer_rating NUMBER,
    CONSTRAINT fk_transactions_harvests FOREIGN KEY (harvest_id) REFERENCES HARVESTS(harvest_id),
    CONSTRAINT fk_transactions_buyers FOREIGN KEY (buyer_id) REFERENCES BUYERS(buyer_id)
);

CREATE TABLE WEATHER_Info (
    weather_id NUMBER PRIMARY KEY,
    district VARCHAR2(50),
    weather_date DATE,
    temperature NUMBER,
    rainfall_mm NUMBER,
    humidity NUMBER,
    forecast_next_7days VARCHAR2(255)
);
commit;



## DML

**Inserting data**


INSERT INTO FARMERS (farmer_id, national_id, names, phone, district, sector, cell, village, farm_size_hectares, primary_crops, registration_date, credit_score) 
VALUES (1, '123456789', 'John Doe', '0788123456', 'Kicukiro', 'Gikondo', 'Kigarama', 'Nyamirambo', 2.5, 'Tomato, Maize', TO_DATE('2023-01-15', 'YYYY-MM-DD'), 750);

INSERT INTO FARMERS (farmer_id, national_id, names, phone, district, sector, cell, village, farm_size_hectares, primary_crops, registration_date, credit_score) 
VALUES (2, '987654321', 'Jane Smith', '0788765432', 'Gasabo', 'Kimironko', 'Kimisagara', 'Remera', 1.8, 'Beans', TO_DATE('2023-03-20', 'YYYY-MM-DD'), 680);

INSERT INTO FARMERS (
    farmer_id, national_id, names, phone, district, sector, cell, village,
    farm_size_hectares, primary_crops, registration_date, credit_score
) VALUES (
    3, 'NID003', 'Alice Johnson', '0788234567', 'Rwamagana', 'Sector C', 'Cell Z', 'Village 3',
    1.8, 'Irish Potatoes', DATE '2023-03-10', 720
);

INSERT INTO FARMERS (
    farmer_id, national_id, names, phone, district, sector, cell, village,
    farm_size_hectares, primary_crops, registration_date, credit_score
) VALUES (
    4, 'NID004', 'Bob Brown', '0788345678', 'Kirehe', 'Sector D', 'Cell W', 'Village 4',
    4.2, 'Cassava', DATE '2023-04-05', 690
);

INSERT INTO FARMERS (
    farmer_id, national_id, names, phone, district, sector, cell, village,
    farm_size_hectares, primary_crops, registration_date, credit_score
) VALUES (
    5, 'NID005', 'Clara White', '0788456789', 'Nyamagabe', 'Sector E', 'Cell V', 'Village 5',
    2.0, 'Coffee', DATE '2023-05-18', 710
);


-- Insert sample data into CROPS
INSERT INTO CROPS (crop_id, crop_name, category, avg_shelf_life_days, optimal_storage_temp, seasonal_pattern, min_price, max_price, current_market_price)
VALUES (1, 'Tomato', 'Vegetable', 7, 10, 'Seasonal', 200, 400, 350);

INSERT INTO CROPS (crop_id, crop_name, category, avg_shelf_life_days, optimal_storage_temp, seasonal_pattern, min_price, max_price, current_market_price)
VALUES (2, 'Maize', 'Grain', 180, 15, 'Annual', 150, 300, 250);

INSERT INTO CROPS (crop_id, crop_name, category, avg_shelf_life_days, optimal_storage_temp, seasonal_pattern, min_price, max_price, current_market_price)
VALUES (3, 'Beans', 'Legume', 90, 12, 'Biannual', 300, 500, 450);

INSERT INTO CROPS (
    crop_id, crop_name, category, avg_shelf_life_days, optimal_storage_temp,
    seasonal_pattern, min_price, max_price, current_market_price
) VALUES (
    4, 'Cassava', 'Root Crop', 30, 18, 'Rainy Season', 150, 300, 280
);

INSERT INTO CROPS (
    crop_id, crop_name, category, avg_shelf_life_days, optimal_storage_temp,
    seasonal_pattern, min_price, max_price, current_market_price
) VALUES (
    5, 'Coffee', 'Cash Crop', 180, 20, 'Harvest Season', 1000, 1500, 1200
);



-- Insert sample data into STORAGE_FACILITIES
INSERT INTO STORAGE_FACILITIES (storage_id, location, capacity_kg, current_occupancy, temperature, humidity_level, facility_type, cost_per_day)
VALUES (1, 'Kicukiro Warehouse', 10000, 5000, 12, 70, 'Cold Storage', 100);

INSERT INTO STORAGE_FACILITIES (storage_id, location, capacity_kg, current_occupancy, temperature, humidity_level, facility_type, cost_per_day)
VALUES (2, 'Gasabo Dry Storage', 8000, 2000, 20, 50, 'Dry Storage', 50);

INSERT INTO STORAGE_FACILITIES (
    storage_id, location, capacity_kg, current_occupancy, temperature,
    humidity_level, facility_type, cost_per_day
) VALUES (
    3, 'Rwamagana Warehouse', 12000, 7000, 18, 65, 'Dry Storage', 4000
);

INSERT INTO STORAGE_FACILITIES (
    storage_id, location, capacity_kg, current_occupancy, temperature,
    humidity_level, facility_type, cost_per_day
) VALUES (
    4, 'Kirehe Depot', 5000, 1000, 20, 70, 'Dry Storage', 3500
);

INSERT INTO STORAGE_FACILITIES (
    storage_id, location, capacity_kg, current_occupancy, temperature,
    humidity_level, facility_type, cost_per_day
) VALUES (
    5, 'Nyamagabe Storage', 15000, 12000, 10, 50, 'Cold Storage', 6000
);



## Advanced implementation

**Price_Analytics package**

The Price Analytics package analyzes crop market prices to help farmers make better selling decisions. It calculates moving averages, updates current market prices, and identifies trends. It can also alert farmers when prices reach their target or favorable levels.

**codes**


CREATE OR REPLACE PACKAGE BODY price_analytics AS

  FUNCTION get_moving_avg_price(p_crop_id IN NUMBER, p_days IN NUMBER) RETURN NUMBER IS
    v_avg_price NUMBER;
  BEGIN
    SELECT AVG(price_per_kg)
    INTO v_avg_price
    FROM market_prices
    WHERE crop_id = p_crop_id
      AND date_recorded >= SYSDATE - p_days;

    RETURN NVL(v_avg_price, 0);
  EXCEPTION
    WHEN NO_DATA_FOUND THEN
      RETURN 0;
  END get_moving_avg_price;

  PROCEDURE update_market_prices(p_days IN NUMBER) IS
    TYPE crop_price_rec IS RECORD (
      crop_id CROPS.crop_id%TYPE,
      moving_avg NUMBER,
      demand_score NUMBER,
      supply_score NUMBER,
      seasonal_factor NUMBER,
      new_price NUMBER
    );

    TYPE crop_price_tab IS TABLE OF crop_price_rec;
    v_crop_prices crop_price_tab;

    TYPE t_crop_ids IS TABLE OF NUMBER;
    v_crop_ids t_crop_ids;

    v_demand_weight CONSTANT NUMBER := 0.4;
    v_supply_weight CONSTANT NUMBER := 0.3;
    v_season_weight CONSTANT NUMBER := 0.3;

    v_seasonal_factor NUMBER;

  BEGIN
    -- First just collect crop ids
    SELECT crop_id BULK COLLECT INTO v_crop_ids FROM crops;

    -- Extend main record collection to match size
    v_crop_prices := crop_price_tab();
    v_crop_prices.EXTEND(v_crop_ids.COUNT);

    FOR i IN 1 .. v_crop_ids.COUNT LOOP
      v_crop_prices(i).crop_id := v_crop_ids(i);

      v_crop_prices(i).moving_avg := get_moving_avg_price(v_crop_prices(i).crop_id, p_days);

      -- demand & supply scoring
      SELECT NVL(AVG(CASE demand_level WHEN 'High' THEN 3 WHEN 'Medium' THEN 2 ELSE 1 END),2),
             NVL(AVG(CASE supply_level WHEN 'Low' THEN 3 WHEN 'Medium' THEN 2 ELSE 1 END),2)
      INTO v_crop_prices(i).demand_score, v_crop_prices(i).supply_score
      FROM market_prices
      WHERE crop_id = v_crop_prices(i).crop_id
        AND date_recorded >= SYSDATE - p_days;

      -- seasonal factor
      SELECT CASE
               WHEN LOWER(seasonal_pattern) LIKE '%annual%' THEN 1
               WHEN LOWER(seasonal_pattern) LIKE '%seasonal%' THEN
                 CASE WHEN TO_CHAR(SYSDATE,'MM') IN ('11','12','01','02') THEN 1.2 ELSE 0.8 END
               ELSE 1
             END
      INTO v_seasonal_factor
      FROM crops
      WHERE crop_id = v_crop_prices(i).crop_id;

      v_crop_prices(i).seasonal_factor := v_seasonal_factor;

      -- weighted new price
      v_crop_prices(i).new_price :=
        v_crop_prices(i).moving_avg *
        (1 + v_demand_weight * (v_crop_prices(i).demand_score - 2)/2
           - v_supply_weight * (v_crop_prices(i).supply_score - 2)/2)
           * v_crop_prices(i).seasonal_factor;

      -- clamp price
      DECLARE
        v_min NUMBER;
        v_max NUMBER;
      BEGIN
        SELECT min_price, max_price INTO v_min, v_max
        FROM crops
        WHERE crop_id = v_crop_prices(i).crop_id;

        IF v_crop_prices(i).new_price < v_min THEN
          v_crop_prices(i).new_price := v_min;
        ELSIF v_crop_prices(i).new_price > v_max THEN
          v_crop_prices(i).new_price := v_max;
        END IF;
      END;
    END LOOP;

    -- Bulk update
    FORALL i IN INDICES OF v_crop_prices
      UPDATE crops
      SET current_market_price = v_crop_prices(i).new_price
      WHERE crop_id = v_crop_prices(i).crop_id;

    COMMIT;
  END update_market_prices;

  PROCEDURE check_price_alerts IS
    CURSOR c_farmers_targets IS
      SELECT f.farmer_id, f.names, c.crop_id, c.crop_name, c.current_market_price, h.status
      FROM farmers f
      JOIN harvests h ON f.farmer_id = h.farmer_id
      JOIN crops c ON h.crop_id = c.crop_id
      WHERE h.status = 'Stored';

    TYPE t_alerts IS TABLE OF c_farmers_targets%ROWTYPE;
    v_alerts t_alerts;

  BEGIN
    OPEN c_farmers_targets;
    FETCH c_farmers_targets BULK COLLECT INTO v_alerts;
    CLOSE c_farmers_targets;

    FOR i IN 1 .. v_alerts.COUNT LOOP
      DECLARE
        v_target NUMBER;
      BEGIN
        SELECT min_price INTO v_target FROM crops WHERE crop_id = v_alerts(i).crop_id;

        IF v_alerts(i).current_market_price >= v_target THEN
          DBMS_OUTPUT.PUT_LINE('Price Alert: '||v_alerts(i).names||' - '||
                               v_alerts(i).crop_name||' now at '||
                               v_alerts(i).current_market_price);
        END IF;
      END;
    END LOOP;
  END check_price_alerts;

END price_analytics;
/
SET SERVEROUTPUT ON;
BEGIN
  price_analytics.update_market_prices(7); -- update prices based on last 7 days
  price_analytics.check_price_alerts;      -- check and output price alerts
END;
/
commit;

**Spoilage_Monitor Package**

The Spoilage Monitor package tracks and predicts the shelf life of harvested crops. It calculates how long crops will remain fresh, forecasts potential spoilage, and helps farmers take timely actions to reduce losses. It can also generate alerts or reports on crop quality over time.

**Codes**

CREATE OR REPLACE PACKAGE spoilage_monitor AS
  PROCEDURE calculate_shelf_life;
  PROCEDURE predict_spoilage_and_notify(p_threshold NUMBER := 70);
  PROCEDURE reallocate_storage;
END spoilage_monitor;
/

CREATE OR REPLACE PACKAGE BODY spoilage_monitor AS

  -- 1. Real-time shelf life calculation
  PROCEDURE calculate_shelf_life IS
    v_shelf_life NUMBER;
  BEGIN
    FOR rec IN (
      SELECT h.harvest_id,
             h.quantity_kg,
             h.storage_id,
             h.harvest_date,
             c.avg_shelf_life_days,
             s.temperature,
             s.humidity_level
      FROM harvests h
      JOIN crops c ON h.crop_id = c.crop_id
      JOIN storage_facilities s ON h.storage_id = s.storage_id
      WHERE h.status = 'Stored'
    ) LOOP

      -- Adjust shelf life based on storage conditions using simple decay model
      v_shelf_life := rec.avg_shelf_life_days * 
                      CASE 
                        WHEN rec.temperature > 20 THEN 0.8
                        WHEN rec.temperature BETWEEN 15 AND 20 THEN 0.9
                        ELSE 1
                      END *
                      CASE 
                        WHEN rec.humidity_level > 70 THEN 0.85
                        ELSE 1
                      END;

      DBMS_OUTPUT.PUT_LINE(
        'Harvest ID: ' || rec.harvest_id ||
        ', Adjusted Shelf Life: ' || ROUND(v_shelf_life,2) || ' days'
      );
    END LOOP;
  END calculate_shelf_life;

  -- 2. Predict spoilage and send urgent notifications
  PROCEDURE predict_spoilage_and_notify(p_threshold NUMBER := 70) IS
    v_spoilage_rate NUMBER;
  BEGIN
    FOR rec IN (
      SELECT h.harvest_id,
             h.quantity_kg,
             h.storage_id,
             h.harvest_date,
             c.avg_shelf_life_days,
             s.temperature,
             s.humidity_level,
             f.names AS farmer_name
      FROM harvests h
      JOIN crops c ON h.crop_id = c.crop_id
      JOIN storage_facilities s ON h.storage_id = s.storage_id
      JOIN farmers f ON h.farmer_id = f.farmer_id
      WHERE h.status = 'Stored'
    ) LOOP

      -- Adjusted shelf life
      v_spoilage_rate := (TRUNC(SYSDATE - rec.harvest_date) /
                          (rec.avg_shelf_life_days *
                          CASE 
                            WHEN rec.temperature > 20 THEN 0.8
                            WHEN rec.temperature BETWEEN 15 AND 20 THEN 0.9
                            ELSE 1
                          END *
                          CASE 
                            WHEN rec.humidity_level > 70 THEN 0.85
                            ELSE 1
                          END)) * 100;

      DBMS_OUTPUT.PUT_LINE(
        'Harvest ID: ' || rec.harvest_id ||
        ', Spoilage Rate: ' || ROUND(v_spoilage_rate,2) || '%'
      );

      -- Urgent sale notification
      IF v_spoilage_rate >= p_threshold THEN
        DBMS_OUTPUT.PUT_LINE(
          '⚠️ URGENT SALE ALERT! Farmer: ' || rec.farmer_name ||
          ', Harvest ID: ' || rec.harvest_id ||
          ', Spoilage risk: ' || ROUND(v_spoilage_rate,2) || '% exceeds threshold'
        );
      END IF;

    END LOOP;
  END predict_spoilage_and_notify;

  -- 3. Suggest storage reallocation
  PROCEDURE reallocate_storage IS
  BEGIN
    FOR rec IN (
      SELECT h.harvest_id,
             h.quantity_kg,
             h.storage_id,
             s.capacity_kg,
             s.current_occupancy,
             s.facility_type
      FROM harvests h
      JOIN storage_facilities s ON h.storage_id = s.storage_id
      WHERE h.status = 'Stored'
    ) LOOP
      IF rec.current_occupancy / rec.capacity_kg > 0.8 THEN
        DBMS_OUTPUT.PUT_LINE(
          'Harvest ID: ' || rec.harvest_id ||
          ' is in crowded storage (' || ROUND(rec.current_occupancy/rec.capacity_kg*100,2) || '% full). Consider reallocation to a facility with lower occupancy.'
        );
      END IF;
    END LOOP;
  END reallocate_storage;

END spoilage_monitor;
/

SET SERVEROUTPUT ON;
BEGIN
  -- 1. Calculate shelf life
  spoilage_monitor.calculate_shelf_life;

  -- 2. Predict spoilage and notify if >= threshold (default 70%)
  spoilage_monitor.predict_spoilage_and_notify;

  -- 3. Check for crowded storage
  spoilage_monitor.reallocate_storage;
END;
/


**Credit_Engine Package**

The Credit Engine package evaluates a farmer’s creditworthiness using transaction history, harvest quality, buyer ratings, and payment consistency. It automatically determines loan eligibility and assigns risk categories. It also generates credit reports and supports informed financial decisions for lending or risk management.

**Codes**

CREATE OR REPLACE PACKAGE credit_engine IS

  -- Record type for credit report summary
  TYPE credit_report_rec IS RECORD (
    farmer_id           FARMERS.farmer_id%TYPE,
    farmer_name         FARMERS.names%TYPE,
    total_transactions  NUMBER,
    avg_quality_rating  NUMBER,
    avg_payment_status_score NUMBER,
    avg_buyer_rating    NUMBER,
    credit_score        FARMERS.credit_score%TYPE,
    loan_eligibility    VARCHAR2(40),  -- increased size
    risk_category       VARCHAR2(40)   -- increased size
  );

  -- Cursor type for credit report
  TYPE credit_report_cur IS REF CURSOR RETURN credit_report_rec;

  -- Function to calculate credit score for a given farmer
  FUNCTION calculate_credit_score(p_farmer_id IN NUMBER) RETURN NUMBER;

  -- Procedure to update farmer credit score based on calculation
  PROCEDURE update_farmer_credit_score(p_farmer_id IN NUMBER);

  -- Function to assess loan eligibility and risk category based on credit score
  FUNCTION assess_loan_eligibility(p_credit_score IN NUMBER) RETURN VARCHAR2;

  -- Procedure to generate credit report cursor for all farmers
  PROCEDURE generate_credit_report(p_report OUT credit_report_cur);

END credit_engine;
/


CREATE OR REPLACE PACKAGE BODY credit_engine IS

  -- Helper function to convert payment_status to numeric score
  FUNCTION payment_status_score(p_status VARCHAR2) RETURN NUMBER IS
  BEGIN
    IF p_status = 'Paid' THEN
      RETURN 1;
    ELSIF p_status = 'Pending' THEN
      RETURN 0.5;
    ELSE
      RETURN 0;
    END IF;
  END payment_status_score;

  FUNCTION calculate_credit_score(p_farmer_id IN NUMBER) RETURN NUMBER IS
    v_total_transactions NUMBER := 0;
    v_avg_quality_rating NUMBER := 0;
    v_avg_payment_score  NUMBER := 0;
    v_avg_buyer_rating   NUMBER := 0;
    v_credit_score       NUMBER := 0;
  BEGIN
    -- Aggregate transaction data for farmer
    SELECT COUNT(t.transaction_id),
           NVL(AVG(t.quality_rating),0),
           NVL(AVG(CASE WHEN t.payment_status = 'Paid' THEN 1 WHEN t.payment_status = 'Pending' THEN 0.5 ELSE 0 END),0),
           NVL(AVG(t.buyer_rating),0)
      INTO v_total_transactions, v_avg_quality_rating, v_avg_payment_score, v_avg_buyer_rating
      FROM TRANSACTIONS t
      JOIN HARVESTS h ON t.harvest_id = h.harvest_id
      WHERE h.farmer_id = p_farmer_id;

    -- Weight parameters for credit score calculation
    -- Weights: transactions 25%, quality_rating 25%, payment_score 30%, buyer_rating 20%
    v_credit_score := 
      LEAST(1000, -- cap max score
        ROUND(
          (v_total_transactions * 25) * 0.01 + 
          (v_avg_quality_rating * 25) + 
          (v_avg_payment_score * 30 * 100) + 
          (v_avg_buyer_rating * 20)
        )
      );

    RETURN v_credit_score;
  END calculate_credit_score;

  PROCEDURE update_farmer_credit_score(p_farmer_id IN NUMBER) IS
    v_score NUMBER;
  BEGIN
    v_score := calculate_credit_score(p_farmer_id);
    UPDATE FARMERS
       SET credit_score = v_score
     WHERE farmer_id = p_farmer_id;
    COMMIT;
  END update_farmer_credit_score;

  FUNCTION assess_loan_eligibility(p_credit_score IN NUMBER) RETURN VARCHAR2 IS
  BEGIN
    IF p_credit_score >= 750 THEN
      RETURN 'Eligible - Low Risk';
    ELSIF p_credit_score >= 600 THEN
      RETURN 'Eligible - Medium Risk';
    ELSE
      RETURN 'Not Eligible - High Risk';
    END IF;
  END assess_loan_eligibility;

  PROCEDURE generate_credit_report(p_report OUT credit_report_cur) IS
  BEGIN
    OPEN p_report FOR
      SELECT 
        f.farmer_id,
        f.names AS farmer_name,
        NVL(t.tx_count,0) AS total_transactions,
        NVL(t.avg_quality_rating,0) AS avg_quality_rating,
        NVL(t.avg_payment_score,0) AS avg_payment_status_score,
        NVL(t.avg_buyer_rating,0) AS avg_buyer_rating,
        NVL(f.credit_score,0) AS credit_score,
        CASE 
          WHEN NVL(f.credit_score,0) >= 750 THEN 'Eligible - Low Risk'
          WHEN NVL(f.credit_score,0) >= 600 THEN 'Eligible - Medium Risk'
          ELSE 'Not Eligible - High Risk'
        END AS loan_eligibility,
        CASE 
          WHEN NVL(f.credit_score,0) >= 750 THEN 'Low'
          WHEN NVL(f.credit_score,0) >= 600 THEN 'Medium'
          ELSE 'High'
        END AS risk_category
      FROM FARMERS f
      LEFT JOIN (
        SELECT 
          h.farmer_id,
          COUNT(t.transaction_id) AS tx_count,
          AVG(t.quality_rating) AS avg_quality_rating,
          AVG(CASE WHEN t.payment_status = 'Paid' THEN 1 WHEN t.payment_status = 'Pending' THEN 0.5 ELSE 0 END) AS avg_payment_score,
          AVG(t.buyer_rating) AS avg_buyer_rating
        FROM TRANSACTIONS t
        JOIN HARVESTS h ON t.harvest_id = h.harvest_id
        GROUP BY h.farmer_id
      ) t ON f.farmer_id = t.farmer_id;
  END generate_credit_report;

END credit_engine;
/




SET SERVEROUTPUT ON;

DECLARE
  -- Variables for direct credit score & eligibility checks
  v_farmer_id    NUMBER := 10;
  v_score        NUMBER;
  v_eligibility  VARCHAR2(50);

  -- Cursor variables for full credit report
  v_report   credit_engine.credit_report_cur;
  v_record   credit_engine.credit_report_rec;

BEGIN
  DBMS_OUTPUT.PUT_LINE('==============================');
  DBMS_OUTPUT.PUT_LINE(' STEP 1: UPDATE A SPECIFIC FARMER');
  DBMS_OUTPUT.PUT_LINE('==============================');

  -- Update the farmer's credit score
  credit_engine.update_farmer_credit_score(v_farmer_id);

  DBMS_OUTPUT.PUT_LINE('Updated credit score for farmer ID ' || v_farmer_id);


  DBMS_OUTPUT.PUT_LINE(CHR(10) || '==============================');
  DBMS_OUTPUT.PUT_LINE(' STEP 2: CALCULATE CREDIT SCORE DIRECTLY');
  DBMS_OUTPUT.PUT_LINE('==============================');

  -- Get the calculated score directly
  v_score := credit_engine.calculate_credit_score(v_farmer_id);

  DBMS_OUTPUT.PUT_LINE('Calculated credit score for farmer ' || v_farmer_id || ': ' || v_score);


  DBMS_OUTPUT.PUT_LINE(CHR(10) || '==============================');
  DBMS_OUTPUT.PUT_LINE(' STEP 3: ASSESS LOAN ELIGIBILITY');
  DBMS_OUTPUT.PUT_LINE('==============================');

  v_eligibility := credit_engine.assess_loan_eligibility(v_score);

  DBMS_OUTPUT.PUT_LINE('Loan Eligibility for Farmer ' || v_farmer_id || ': ' || v_eligibility);


  DBMS_OUTPUT.PUT_LINE(CHR(10) || '==============================');
  DBMS_OUTPUT.PUT_LINE(' STEP 4: UPDATE ALL FARMERS (BATCH)');
  DBMS_OUTPUT.PUT_LINE('==============================');

  -- Update all farmers in the system
  FOR f IN (SELECT farmer_id FROM farmers)
  LOOP
    credit_engine.update_farmer_credit_score(f.farmer_id);
  END LOOP;

  DBMS_OUTPUT.PUT_LINE('All farmer credit scores updated successfully.');


  DBMS_OUTPUT.PUT_LINE(CHR(10) || '==============================');
  DBMS_OUTPUT.PUT_LINE(' STEP 5: GENERATE FULL CREDIT REPORT');
  DBMS_OUTPUT.PUT_LINE('==============================');

  -- Open the cursor with the credit report
  credit_engine.generate_credit_report(v_report);

  -- Loop and print the full credit report
  LOOP
    FETCH v_report INTO v_record;
    EXIT WHEN v_report%NOTFOUND;

    DBMS_OUTPUT.PUT_LINE(
      'Farmer ID: ' || v_record.farmer_id ||
      ' | Name: ' || v_record.farmer_name ||
      ' | Transactions: ' || v_record.total_transactions ||
      ' | Avg Quality: ' || NVL(TO_CHAR(v_record.avg_quality_rating), '0') ||
      ' | Avg Buyer Rating: ' || NVL(TO_CHAR(v_record.avg_buyer_rating), '0') ||
      ' | Payment Score: ' || NVL(TO_CHAR(v_record.avg_payment_status_score), '0') ||
      ' | Credit Score: ' || v_record.credit_score ||
      ' | Eligibility: ' || v_record.loan_eligibility ||
      ' | Risk: ' || v_record.risk_category
    );
  END LOOP;

  CLOSE v_report;

  DBMS_OUTPUT.PUT_LINE(CHR(10) || 'CREDIT REPORT COMPLETED.');

END;
/
