# Fast VIN Decoder API

The Fast VIN Decoder API allows you to decode Vehicle Identification Numbers (VINs) and retrieve detailed vehicle information using NHTSA data.

## API Endpoint

```
GET /decode-vin/{vin}
```

Base URL: `https://your-api-url.com`

## Authentication

*Coming soon*

## Request Parameters

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| vin | string | Yes | The Vehicle Identification Number (VIN) to decode |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| modelyear | string | No | The model year of the vehicle |
| format | string | No | Response format (`json` or `xml`). Defaults to `json` |

## Response Format

### Successful Response (200)

```json
{
  "VIN": "JTEBU5JRXJ5543007",
  "Make": "TOYOTA",
  "Model": "4-Runner",
  "ModelYear": "2018",
  "Trim": "SR5 Premium",
  "ErrorText": "0 - VIN decoded clean. Check Digit (9th position) is correct"
}
```

### Error Responses

#### Bad Request (400)
```json
{
  "error": "Invalid VIN format"
}
```

#### Server Error (500)
```json
{
  "error": "Server Error: Unable to decode VIN"
}
```

## Example Usage

### cURL
```bash
curl -X GET "https://your-api-url.com/decode-vin/JTEBU5JRXJ5543007?format=json"
```

### Python
```python
import requests

vin = "JTEBU5JRXJ5543007"
response = requests.get(f"https://your-api-url.com/decode-vin/{vin}")
vehicle_data = response.json()
print(vehicle_data)
```

## Rate Limits

*Coming soon*

## Support

If you encounter any issues or have questions about the Fast VIN Decoder API, please:
1. Check this documentation for answers
2. Open an issue on our [GitHub repository](https://github.com/your-username/api-smith)

## Contributing

We welcome contributions! Please see our contributing guidelines for more information. 