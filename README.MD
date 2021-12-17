# Export Google Sheets to Separate Excel Files

**Author: Valentin Ghica**
**Website: https://danvaly.ro**

Tool to connect to Google Sheet and fill separate forms in XLSX format for each row.
Follow the steps bellow to use this tool.

## Tool Credentials
In order to use this tool you need Google Cloud API Desktop credentials from here: https://developers.google.com/workspace/guides/create-credentials


Installation: 
- Install last version of  Python 3.X
- Install the required packages ``` pip install -r requirements``` 
- Run after you copy the credentials and config the mapping ``` python pyexport.py ```

On first run you need to authenticate with Google.

## Json Config

For configuration you need to creat a JSON file **config.json**

Example:

```json 
{
  "template": "template.xlsx",
  "sheetId": "sdasdjaslkdjaslkjdlskajdlksjalkdjslakjdsjaldjsklajdlkasd",
  "workbook": "Sheet1",
  "range": "Sheet 1!A2:BF100",
  "map": [
    {
      "column": 1,
      "index": "B7",
    },
    {
      "column": 15,
      "index": "F21",
      "format": "substring",
      "start": 0,
      "end": 1
    },
    {
      "column": 15,
      "index": "G26",
      "format": "substring",
      "start": 0,
      "end": 1,
      "indexCondition": [
        ["D","B21"],
        ["O","C21"],
        ["M","D21"],
        ["E","E21"]
      ]
    }
  ]
}
```

Keys:
- **template** : Template filename 
- **sheetId** : Google Sheet document ID taken from the link
- **workbook** : The workbook to write into template
- **range** : Data range from Google Spreadsheet Ex: A2:B2 will extract only cels A2 & B2
- **map** : Map of the values

Mapping values:
- **column**: Google Sheet column value
- **index** : Template Index position
- **format** : Optional, you can only use substring
- **start** : Required parameter when using format:substring
- **end** : Required parameter when using format:substring
- **indexCondition** : Based on final value you can map inside a different column. Condition: Column, Condition: Column