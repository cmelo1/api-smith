# Fast VIN Decoder API Documentation

This repository hosts the **Fast VIN Decoder API** documentation.

## 🚀 Overview
The **Fast VIN API** allows users to decode **Vehicle Identification Numbers (VINs)** and retrieve vehicle details using **NHTSA** data.

---

## 🔗 API Reference
👉 **[View API Docs](https://petstore.swagger.io/?url=https://raw.githubusercontent.com/cmelo1/api-smith/main/fast-vin/docs/openapi.yaml)**

---

## 📌 Endpoints

### **`GET /decode-vin-full/{VIN}`**
**Description:** Full VIN decode with complete vehicle details from NHTSA database (140+ fields).

#### ✅ Parameters:
| Name       | Type     | Required | Description |
|------------|----------|----------|-------------|
| `VIN`      | `string` | ✅ Yes   | The **Vehicle Identification Number (VIN)** |
| `format`   | `string` | ❌ No    | Response format: `json` or `xml` (default: `json`) |
| `flatfile` | `string` | ❌ No    | Whether to return a simplified response format: `true` or `false` (default: `true`) |
| `modelyear`| `string` | ❌ No    | The model year of the vehicle (optional) |

### **`GET /decode-vin/{VIN}`**
**Description:** Standard VIN decode with comprehensive vehicle details (~137 fields).

#### ✅ Parameters:
| Name       | Type     | Required | Description |
|------------|----------|----------|-------------|
| `VIN`      | `string` | ✅ Yes   | The **Vehicle Identification Number (VIN)** |
| `format`   | `string` | ❌ No    | Response format: `json` or `xml` (default: `json`) |
| `flatfile` | `string` | ❌ No    | Whether to return a simplified response format: `true` or `false` (default: `true`) |
| `modelyear`| `string` | ❌ No    | The model year of the vehicle (optional) |

### **`GET /decode-vin-lite/{vin}`**
**Description:** Basic VIN decode with essential vehicle details (6 fields).

#### ✅ Parameters:
| Name       | Type     | Required | Description |
|------------|----------|----------|-------------|
| `vin`      | `string` | ✅ Yes   | The **Vehicle Identification Number (VIN)** |
| `modelyear`| `string` | ❌ No    | The model year of the vehicle (optional) |
| `format`   | `string` | ❌ No    | Response format: `json` or `xml` (default: `json`) |

---

## 📄 Example Requests & Responses

### Full Decode Example

#### Request:
```bash
curl -X GET "https://fast-vin.p.rapidapi.com/decode-vin-full/JTEBU5JRYJ5543007?format=json&flatfile=true"
```

#### Response (JSON):
```json
{
  "Count": 1,
  "Message": "Results returned successfully",
  "SearchCriteria": "VIN(s): JTEBU5JRYJ5543007",
  "Results": [{
    "ABS": "Standard",
    "ActiveSafetySysNote": "Front and Rear Parking Assist Sonar: Standard for Limited trim",
    "BodyClass": "Sport Utility Vehicle (SUV)/Multi-Purpose Vehicle (MPV)",
    "DisplacementL": "4",
    "DriveType": "4WD/4-Wheel Drive/4x4",
    "EngineConfiguration": "V-Shaped",
    "EngineCylinders": "6",
    "EngineHP": "270",
    "Make": "TOYOTA",
    "Model": "4-Runner",
    "ModelYear": "2018",
    "Trim": "SR5 Premium",
    "VIN": "JTEBU5JRYJ5543007"
  }]
}
```

### Standard Decode Example

#### Request:
```bash
curl -X GET "https://fast-vin.p.rapidapi.com/decode-vin/JTEBU5JRYJ5543007?format=json&flatfile=true"
```

#### Response (JSON):
```json
{
  "Count": 1,
  "Message": "Results returned successfully",
  "SearchCriteria": "VIN(s): JTEBU5JRYJ5543007",
  "Results": [{
    "Make": "TOYOTA",
    "Model": "4-Runner",
    "ModelYear": "2018",
    "PlantCountry": "JAPAN",
    "Series": "GRN280L/GRN285L",
    "Trim": "SR5 Premium",
    "VehicleType": "MULTIPURPOSE PASSENGER VEHICLE (MPV)",
    "VIN": "JTEBU5JRYJ5543007"
  }]
}
```

### Lite Decode Example

#### Request:
```bash
curl -X GET "https://fast-vin.p.rapidapi.com/decode-vin-lite/JTEBU5JRYJ5543007?format=json"
```

#### Response (JSON):
```json
{
  "Count": 1,
  "Message": "Results returned successfully",
  "SearchCriteria": "VIN(s): JTEBU5JRYJ5543007",
  "Results": [{
    "Make": "TOYOTA",
    "Model": "4-Runner",
    "ModelYear": "2018",
    "Trim": "SR5 Premium",
    "VIN": "JTEBU5JRYJ5543007"
  }]
}
```

## Field Mapping

The following table shows all available fields and their availability across different API endpoints:

| Field Name | Format | Sample Value | Lite | Standard | Full |
|------------|--------|--------------|------|----------|------|
| ABS | string | Standard | ❌ | ✅ | ✅ |
| ActiveSafetySysNote | string | Front and Rear Parking Assist Sonar: Standard for Limited trim; Keyless Ignition: Standard for Limited trim | ❌ | ❌ | ✅ |
| AdaptiveCruiseControl | string | null | ❌ | ❌ | ✅ |
| AirBagLocCurtain | string | All Rows | ❌ | ❌ | ✅ |
| AirBagLocFront | string | 1st Row (Driver and Passenger) | ❌ | ❌ | ✅ |
| AirBagLocKnee | string | 1st Row (Driver and Passenger) | ❌ | ❌ | ✅ |
| BasePrice | decimal | 34810.00 | ❌ | ❌ | ✅ |
| BodyClass | string | Sport Utility Vehicle (SUV)/Multi-Purpose Vehicle (MPV) | ❌ | ❌ | ✅ |
| BrakeSystemDesc | string | Calipers / Front Vented Discs | ❌ | ❌ | ✅ |
| DisplacementCC | string | 4000 | ❌ | ❌ | ✅ |
| DisplacementL | string | 4 | ❌ | ❌ | ✅ |
| Doors | string | 5 | ❌ | ❌ | ✅ |
| DriveType | string | 4WD/4-Wheel Drive/4x4 | ❌ | ❌ | ✅ |
| EngineConfiguration | string | V-Shaped | ❌ | ❌ | ✅ |
| EngineCylinders | string | 6 | ❌ | ❌ | ✅ |
| EngineHP | string | 270 | ❌ | ❌ | ✅ |
| EngineModel | string | 1GR-FE | ❌ | ❌ | ✅ |
| ErrorCode | string | 0 | ✅ | ✅ | ✅ |
| ErrorText | string | 0 - VIN decoded clean. Check Digit (9th position) is correct | ✅ | ✅ | ✅ |
| FuelInjectionType | string | Multipoint Fuel Injection (MPFI) | ❌ | ❌ | ✅ |
| FuelTypePrimary | string | Gasoline | ❌ | ❌ | ✅ |
| Make | string | TOYOTA | ✅ | ✅ | ✅ |
| MakeID | string | 448 | ❌ | ✅ | ✅ |
| Manufacturer | string | TOYOTA MOTOR CORPORATION | ❌ | ✅ | ✅ |
| Model | string | 4-Runner | ✅ | ✅ | ✅ |
| ModelID | string | 2216 | ❌ | ✅ | ✅ |
| ModelYear | string | 2018 | ✅ | ✅ | ✅ |
| PlantCity | string | TAHARA | ❌ | ✅ | ✅ |
| PlantCountry | string | JAPAN | ❌ | ✅ | ✅ |
| SeatRows | string | 2 | ❌ | ❌ | ✅ |
| Seats | string | 5 | ❌ | ❌ | ✅ |
| Series | string | GRN280L/GRN285L | ❌ | ✅ | ✅ |
| TransmissionSpeeds | string | 5 | ❌ | ❌ | ✅ |
| TransmissionStyle | string | Automatic | ❌ | ❌ | ✅ |
| Trim | string | SR5/SR5 Premium/TRD Off Road/TRD Off Road Premium/Ltd/TRD Pro | ✅ | ✅ | ✅ |
| VIN | string | JTEBU5JRYJ5543007 | ✅ | ✅ | ✅ |
| VehicleType | string | MULTIPURPOSE PASSENGER VEHICLE (MPV) | ❌ | ✅ | ✅ |

> Note: This is a subset of the most commonly used fields. The full API response includes additional fields. Fields marked with ✅ are included in the respective endpoint response, while ❌ indicates the field is not available in that endpoint.

### Endpoint Field Coverage

- **Lite**: 6 essential fields (basic vehicle identification)
- **Standard**: ~137 fields (comprehensive vehicle details)
- **Full**: 140+ fields (complete NHTSA database fields)

For a complete list of all available fields, please refer to our [field-mapping.csv](./sample-responses/field-mapping.csv) file.
