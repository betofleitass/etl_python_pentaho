## ETL with Python and Pentaho

This code is an ETL (Extract, Transform and Load) process for global commodity trade data. It extracts trade data from a PostgreSQL database, as well as country and product code data from JSON and CSV files, respectively. It then transforms the product codes and countries data to make them consistent with the trade data and merges all the data into a single DataFrame. 
Finally, it creates dimensions for quantity, flow and year and merges them with the trade data. 
The final output, a clean DataFrame of global commodity trade data, is the facts table, as it contains the measurable data about the trade transactions such as the quantity, value, and weight of the commodities traded, as well as the trade flow direction and the time period of the trade. 
Finally the data is ready to be loaded into a data warehouse for further analysis.

<a><img src="https://user-images.githubusercontent.com/95726794/226501281-ca78a013-21bc-4f3e-89ce-147d13f00976.png" width="50%" height="70%"></a>
<br></br>
<a><img src="https://user-images.githubusercontent.com/95726794/226502139-9c43ad64-a86b-4d4f-859c-4af6536e35dd.png" width="70%" height="70%"></a>

## Table of Contents:
- [ETL with Python and Pentaho](#etl-with-python-and-pentaho)
- [Table of Contents:](#table-of-contents)
- [Requirements:](#requirements)
- [Installation](#installation)
- [Run it locally](#run-it-locally)
- [Contributing](#contributing)
- [Authors](#authors)
- [License](#license)

## Requirements:
Python 3.10, Pentaho, Docker

## Installation
    
  1. Clone or download the repository:  
  ` git clone https://github.com/betofleitass/etl_python_pentaho`

  2. Go to the project directory  
  ` cd etl_python_pentaho`

  3. Create a virtual environment:  
  
  PowerShell:
  ```
   python -m venv venv
   venv\Scripts\Activate.ps1
  ```  
  Linux:
  ```
  python3 -m venv venv
  source venv/bin/activate
  ```

  4. Install dependencies:  
  ` pip install -r requirements.txt`
  
  5. This project requires to have Docker
  [Get Docker](https://docs.docker.com/get-docker/)
  
## Run it locally

1. Go to the project directory: `cd etl_python_pentaho`

2. Run the container  
` docker-compose -f docker-compose.yml up` 

3. Connect to the database  
` docker exec -it postgres psql -U my_user -d etl_python --password` 

4. Run the script, it may take up to 20 minutes  
` \i /sources/public_trades.sql` 

5. Create a new database for the transformed data  
` create database trades;` 

6. Change to the new database  
` \c trades` 

7. Run the script to create the tables  
` \i /sources/script_tables.sql` 

8. Create a new database for pentaho
` create database trades_pentaho;` 

9. Change to the new database  
` \c trades_pentaho` 

10. Run the script to create the tables  
` \i /sources/script_tables.sql` 

11. To execute the ETL process, there are two options available.  
The first option is to run the Notebook etl.ipynb, which contains the code and instructions on how to run the ETL process.  
The second option is to import the Pentaho file and execute it.
## Contributing
- Fork this repository;
- Create a branch with your feature: `git checkout -b my-feature`;
- Commit your changes: `git commit -m "feat: my new feature"`;
- Push to your branch: `git push origin my-feature`.

## Authors
- [@betofleitass](https://www.github.com/betofleitass)

##  License
This project is under [MIT License.](https://choosealicense.com/licenses/mit/)

[Back to top ⬆️](#etl_python_pentaho)