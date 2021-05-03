# Get Started with the SAP HANA Cloud (SAP Developers Mission)

This repository is based on the SAP Developers Mission "Get Started with the SAP HANA Cloud"

Source: https://developers.sap.com/mission.hana-cloud-get-started.html


# Prerequisites:

## Create plain schema

    CREATE SCHEMA "PLAIN";
    CREATE USER PLUSR PASSWORD "HanaRocks01" SET USERGROUP DEFAULT;
      ALTER USER PLUSR DISABLE PASSWORD LIFETIME;
    
    CREATE ROW TABLE "PLAIN"."REGIONS" (	REGION NVARCHAR(5), 	DESCRIPTION NVARCHAR(100) );
    
    CREATE ROLE CCROLE;
    grant  SELECT, UPDATE, INSERT, DELETE, EXECUTE, SELECT METADATA ON SCHEMA "PLAIN" TO CCROLE with grant option;
    grant  CCROLE to PLUSR with admin option;

Import plain.csv data into "PLAIN"."REGIONS".

Details see https://developers.sap.com/tutorials/hana-cloud-access-cross-container-schema.html#3acab07e-02a5-4d5d-bc32-59ddbc48e6b5

## Create user provided services

    cf cups CC_ACCESS -p "{\"user\":\"PLUSR\",\"password\":\"HanaRocks01\",\"tags\":[\"hana\"] , \"schema\" : \"PLAIN\" }"



https://developers.sap.com/tutorials/hana-cloud-access-cross-container-schema.html#df3855dd-79fb-42b0-94ae-2f1e9402f268
