
# Fast VIN Decoder API Documentation

This repository hosts the **Fast VIN Decoder API** documentation.

## 🚀 Overview
The **Fast VIN API** allows users to decode **Vehicle Identification Numbers (VINs)** and retrieve vehicle details using **NHTSA** data.

---

## 🔗 API Reference
👉 **[View API Docs](https://petstore.swagger.io/?url=https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/fast-vin-api-docs/main/docs/openapi.yaml)**

---

## 📌 Endpoints

### **`GET /decode-vin-lite/{vin}`**
**Description:** Decodes a VIN and retrieves vehicle details.

#### ✅ Parameters:
| Name       | Type     | Required | Description |
|------------|---------|----------|------------|
| `vin`      | `string` | ✅ Yes  | The **Vehicle Identification Number (VIN)** |
| `modelyear` | `string` | ❌ No  | The model year of the vehicle (optional) |
| `format`   | `string` | ❌ No  | Response format: `json` or `xml` (default: `json`) |

---

## 📄 Example Requests & Responses

### ✅ **200 - Success**
#### Request:
```bash
curl -X GET "https://your-api-url.com/decode-vin/JTEBU5JRXJ5543007?format=json"

Response (JSON):

{
  "VIN": "JTEBU5JRXJ5543007",
  "Make": "TOYOTA",
  "Model": "4-Runner",
  "ModelYear": "2018",
  "Trim": "SR5 Premium",
  "ErrorText": "0 - VIN decoded clean. Check Digit (9th position) is correct"
}

Response (XML):

<?xml version="1.0" encoding="UTF-8"?>
<VINLookup>
  <VIN>JTEBU5JRXJ5543007</VIN>
  <Make>TOYOTA</Make>
  <Model>4-Runner</Model>
  <ModelYear>2018</ModelYear>
  <Trim>SR5 Premium</Trim>
  <ErrorText>0 - VIN decoded clean. Check Digit (9th position) is correct</ErrorText>
</VINLookup>

❌ 400 - Invalid VIN Format

Request:

curl -X GET "https://your-api-url.com/decode-vin/INVALIDVIN?format=json"

Response (JSON):

{
  "error": "Invalid VIN format"
}

Response (XML):

<?xml version="1.0" encoding="UTF-8"?>
<Error>
  <Message>Invalid VIN format</Message>
</Error>

❌ 500 - Server Error

Request:

curl -X GET "https://your-api-url.com/decode-vin/JTEBU5JRXJ5543007?format=json"

Response (JSON):

{
  "error": "Server Error: Unable to decode VIN"
}

Response (XML):

<?xml version="1.0" encoding="UTF-8"?>
<Error>
  <Message>Server Error: Unable to decode VIN</Message>
</Error>
