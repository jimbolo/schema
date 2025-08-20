# PostScan Mail Schema.org Implementation Guide

## Overview

This document explains the comprehensive Schema.org JSON-LD structured data implementation for PostScan Mail's Los Angeles virtual address and mailbox services. The schema is optimized for AI search engines and follows Schema.org best practices for maximum search visibility and ranking.

> **Last Updated:** August 2, 2025

---

### Note: remove "\_comment" sections on live-site

---

## Schema Structure Summary

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "@id": "https://www.postscanmail.com/a/5101-santa-monica-blvd-ste-8.html"
}
```

**Primary Type**: `LocalBusiness` - Represents a physical business location providing local services  
**Schema Version**: Uses latest Schema.org vocabulary (2024-2025 compatible)  
**Target Keywords**: "Los Angeles virtual address," "CMRA mailbox," "virtual business address"

---

## Section-by-Section Breakdown

### 1. Business Identity (`@type: LocalBusiness`)

```json
"@type": "LocalBusiness",
"@id": "https://www.postscanmail.com/a/5101-santa-monica-blvd-ste-8.html",
"name": "PostScan Mail - Los Angeles Virtual Address and Mailbox",
"legalName": "PostScan Mail, Inc.",
"alternateName": "PostScan Mail Santa Monica Los Angeles"
```

**Purpose**: Establishes the primary business entity and official identification  
**Schema.org Rules**:

- `@id` provides unique identifier for the business location
- `legalName` must match official business registration
- `alternateName` supports search variations for brand recognition
- Optimizes for queries like "PostScan Mail Los Angeles" and "PostScan Mail Santa Monica"

### 2. Business Classification & Compliance

```json
"naics": "561499",
"taxID": "12-3456789",
"duns": "123456789",
"leiCode": "1234567890ABCDEFGHIJ12",
"iso6523Code": "0060:1234567890123"
```

**Purpose**: Provides official business classification and regulatory compliance signals  
**Schema.org Rules**:

### Selected Code: 561499

**NAICS 561499** has been chosen for mail consolidation services.

**NAICS** (North American Industry Classification System) code **561499** is the official U.S. government classification for **"All Other Business Support Services."** This is the most appropriate and closest classification available for virtual address and CMRA services.

### Why 561499 is Perfect for Virtual Address Services

Key services explicitly listed under **561499** that match your business:

- **"Mail consolidation services"** - This directly covers your package consolidation and forwarding services
- **"Mail presorting services"** - Covers mail handling and processing activities
- **"Address bar coding services"** - Related to mail processing and addressing services

### 3. Contact Information (`contactPoint`)

```json
"contactPoint": [
  {
    "@type": "ContactPoint",
    "telephone": "+12135557890",
    "contactType": "customer service",
    "areaServed": "US",
    "availableLanguage": ["English", "Spanish"]
  },
  {
    "@type": "ContactPoint",
    "email": "support@postscanmail.com",
    "contactType": "technical support",
    "areaServed": "US"
  }
]
```

**Purpose**: Structured contact information for different service types  
**Schema.org Rules**:

- Multiple `ContactPoint` objects enable service-specific contact methods
- `contactType` categorizes the purpose of each contact method
- `availableLanguage` array supports multilingual customer base (important for LA market)
- `areaServed` specifies geographic coverage for contact support

### 4. Geographic Location & Targeting

#### Physical Address

```json
"address": {
  "@type": "PostalAddress",
  "streetAddress": "4321 Sunset Blvd, Suite 100",
  "addressLocality": "Los Angeles",
  "addressRegion": "CA",
  "postalCode": "90026",
  "addressCountry": "US"
}
```

#### Geographic Coordinates

```json
"geo": {
  "@type": "GeoCoordinates",
  "latitude": 34.097,
  "longitude": -118.288
}
```

**Purpose**: Precise location identification for local search optimization  
**Schema.org Rules**:

- `PostalAddress` requires `streetAddress`, `addressLocality`, `addressRegion` for complete address
- `GeoCoordinates` enhances location-based search results
- Essential for "near me" searches and local business discovery

### 5. Service Area Targeting (`areaServed`)

```json
"areaServed": [
  {
    "@type": "City",
    "name": "Los Angeles",
    "sameAs": "https://en.wikipedia.org/wiki/Los_Angeles",
    "containedInPlace": {
      "@type": "AdministrativeArea",
      "name": "California",
      "sameAs": "https://en.wikipedia.org/wiki/California"
    }
  },
  {
    "@type": "GeoCircle",
    "name": "Greater Los Angeles Metropolitan Area Service Zone",
    "geoMidpoint": {
      "@type": "GeoCoordinates",
      "latitude": 34.097,
      "longitude": -118.288
    },
    "geoRadius": "50000"
  }
]
```

**Purpose**: Defines geographic areas where services are provided  
**Schema.org Rules**:

- `City` type for specific municipal targeting
- `sameAs` links to Wikipedia for disambiguation (prevents confusion between cities with same names)
- `containedInPlace` establishes geographic hierarchy
- `GeoCircle` with `geoRadius` in meters (50000m = 50km) for comprehensive coverage
- Optimizes for location-specific searches like "Beverly Hills virtual address"

### 6. Service Knowledge Areas (`knowsAbout`)

```json
"knowsAbout": [
  "Virtual Business Address",
  "CMRA-Compliant Mailbox",
  "Digital Mailbox with Physical Routing",
  "LLC Business Address",
  "Form 1583 Notarization Support"
]
```

**Purpose**: Keywords and expertise areas for topical relevance  
**Schema.org Rules**:

- Array of text strings describing business knowledge areas
- Should match actual service capabilities and website content
- Helps AI understand business specializations and expertise
- Optimizes for informational queries related to virtual address services

### 7. Service Offerings (`makesOffer`)

#### Virtual Mailbox Service

```json
{
  "@type": "Offer",
  "itemOffered": {
    "@type": "Service",
    "name": "Virtual Mailbox",
    "serviceType": "Virtual Mailbox for Anyone",
    "serviceOutput": [
      {
        "@type": "DigitalDocument",
        "name": "24/7 Personal Mail Management",
        "description": "Access your personal mailbox anytime..."
      }
    ]
  }
}
```

**Purpose**: Detailed service descriptions with specific deliverables  
**Schema.org Rules**:

- `Offer` contains `itemOffered` of type `Service`
- `serviceOutput` array describes specific deliverables using appropriate schema types:
  - `DigitalDocument` for mail scanning and digital services
  - `ParcelDelivery` for shipping and forwarding services
  - `Product` for physical storage services
- Each output has descriptive `name` and detailed `description`

#### Pricing Structure

```json
"priceSpecification": [
  {
    "@type": "UnitPriceSpecification",
    "price": "10.00",
    "priceCurrency": "USD",
    "unitCode": "MON",
    "unitText": "monthly",
    "billingIncrement": 1,
    "priceType": "https://schema.org/Subscription"
  }
]
```

**Purpose**: Structured pricing information for subscription services  
**Schema.org Rules**:

- `UnitPriceSpecification` for recurring billing
- `unitCode` uses ISO 4217 currency codes or common abbreviations ("MON" for monthly)
- `priceType` specifies subscription model
- `billingIncrement` indicates billing frequency

### 8. Target Audience Specification (`audience`)

```json
"audience": {
  "@type": "Audience",
  "audienceType": "Individuals, Expats, Consumers, Expatriates, RV Travelers, Secure Mail Users, Snowbirds, Personal Privacy Seekers, Foreign Residents, Professionals, Students, U.S. Citizens Abroad, Digital Nomads"
}
```

**Purpose**: Defines target customer segments for AI understanding  
**Schema.org Rules**:

- `Audience` type specifies who the service is intended for
- `audienceType` accepts comma-separated list of customer categories
- Helps AI search engines match services to user intent
- Different services can target different audience segments (Personal vs Business)
- Critical for intent-based search optimization

### 9. ParcelDelivery Services

```json
{
  "@type": "ParcelDelivery",
  "name": "Personal Package Receiving and Forwarding",
  "description": "Receive packages from all carriers (USPS, UPS, FedEx, DHL) at your virtual address. Forward to your current location worldwide, consolidate multiple packages to save shipping costs, or hold for pickup."
}
```

**Purpose**: Structured representation of package handling and shipping services  
**Schema.org Rules**:

- `ParcelDelivery` type specifically for shipping and logistics services
- Can include `carrier`, `deliveryAddress`, `trackingNumber` properties
- Essential for virtual address services offering package forwarding
- Optimizes for queries like "package forwarding Los Angeles" and "virtual address shipping"

#### Advanced ParcelDelivery Implementation

```json
{
  "@type": "Offer",
  "itemOffered": {
    "@type": "ParcelDelivery",
    "name": "Mail Package Consolidation Forwarding Service",
    "provider": {
      "@type": "Organization",
      "name": "PostScan Mail, Inc."
    },
    "carrier": {
      "@type": "Organization",
      "name": "USPS, UPS, FedEx, DHL, ARAMEX"
    },
    "deliveryAddress": [
      {
        "@type": "PostalAddress",
        "addressCountry": "US",
        "name": "Domestic Shipping"
      },
      {
        "@type": "PostalAddress",
        "addressCountry": "INTERNATIONAL",
        "name": "International Shipping"
      }
    ]
  }
}
```

**Schema.org Rules**:

- `provider` identifies the service operator
- `carrier` specifies supported shipping companies
- `deliveryAddress` array defines shipping destinations (domestic/international)
- Enables rich shipping information in search results

### 10. Registered Agent GovernmentService Integration

```json
          {
            "@type": "GovernmentService",
            "name": "Service of Process Receipt",
            "description": "Professional receipt and forwarding of lawsuits, summons, subpoenas, and legal notices"
          },
          {
            "@type": "GovernmentService",
            "name": "Government Compliance Notice Receipt",
            "description": "Receipt of tax documents, annual report reminders, and state regulatory communications"
          }
```

**Purpose**: Represents government-related document handling services  
**Schema.org Rules**:

- `GovernmentService` type for official document processing
- Important for registered agent services
- Signals compliance with legal document handling requirements
- Optimizes for queries about registered agent services and legal document receipt

### 11. Product-Based Storage Services

```json
{
  "@type": "Product",
  "name": "Personal Storage Solutions",
  "description": "Secure storage for personal belongings, seasonal items, important documents, and packages. Flexible short-term or long-term storage with 7 days free, then $0.10 per pound per day."
}
```

**Purpose**: Physical storage services represented as products  
**Schema.org Rules**:

- `Product` type for tangible storage solutions
- Includes pricing information within service descriptions
- Can be enhanced with `brand`, `category`, `offers` properties
- Differentiates physical storage from digital services

### 12. Business Hours & Availability (`openingHoursSpecification`)

```json
"openingHoursSpecification": [
  {
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
    "opens": "09:00",
    "closes": "17:00"
  }
]
```

**Purpose**: Structured business hours for customer service and operations  
**Schema.org Rules**:

- `OpeningHoursSpecification` requires `dayOfWeek`, `opens`, `closes`
- Times in 24-hour format (HH:MM)
- Can include multiple specifications for different service types
- Supports `specialOpeningHoursSpecification` for holidays and exceptions
- Critical for local business discovery and customer expectations

### 13. Social Media & Brand Presence (`sameAs`)

```json
"sameAs": [
  "https://www.facebook.com/PostScanMail",
  "https://x.com/postscanmail",
  "https://www.linkedin.com/company/postscan-mail"
]
```

**Purpose**: Links to official social media profiles and brand presence  
**Schema.org Rules**:

- Array of URLs to official brand profiles
- Helps search engines verify business legitimacy
- Consolidates brand authority signals across platforms
- Should only include officially controlled profiles
- Supports brand entity recognition and trust building

### 14. Customer Actions (`potentialAction`)

```json
"potentialAction": {
  "@type": "BuyAction",
  "name": "Starter Plan",
  "description": "Signup this location's virtual mailbox...",
  "target": {
    "@type": "EntryPoint",
    "urlTemplate": "https://app.postscanmail.com/registration?plan=10037...",
    "actionPlatform": [
      "http://schema.org/DesktopWebPlatform",
      "http://schema.org/MobileWebPlatform"
    ]
  }
}
```

**Purpose**: Defines available customer actions and conversion paths  
**Schema.org Rules**:

- `BuyAction` indicates purchase capability
- `EntryPoint` specifies the URL and supported platforms
- `actionPlatform` array lists compatible device types
- Enables rich snippets with action buttons in search results

### 15. Credentials & Certifications

#### Educational Credential (Legacy)

```json
"hasCredential": {
  "@type": "EducationalOccupationalCredential",
  "name": "USPS Commercial Mail Receiving Agency (CMRA) Authorization",
  "credentialCategory": "Regulatory"
}
```

#### Enhanced Certification (Current Best Practice)

```json
"hasCertification": {
  "@type": "Certification",
  "name": "USPS Commercial Mail Receiving Agency (CMRA) Authorization",
  "certificationIdentification": "CMRA-CA-2024-001",
  "certificationStatus": "CertificationActive",
  "issuedBy": {
    "@type": "GovernmentOrganization",
    "name": "United States Postal Service"
  }
}
```

**Purpose**: Demonstrates regulatory compliance and professional credentials  
**Schema.org Rules**:

- `Certification` is preferred over `EducationalOccupationalCredential` for regulatory compliance
- `certificationStatus` indicates current validity
- `issuedBy` references the authorizing organization
- Critical for CMRA services requiring USPS authorization

### 16. Corporate Structure & Relationships

#### Parent Organization

```json
"parentOrganization": {
  "@type": "Organization",
  "name": "PostScan Mail, Inc.",
  "naics": "561499",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "1950 W Corporate Way",
    "addressLocality": "Anaheim"
  }
}
```

#### Branch Relationship

```json
"branchOf": {
  "@type": "Organization",
  "name": "PostScan Mail, Inc.",
  "url": "https://www.postscanmail.com"
}
```

**Purpose**: Establishes corporate hierarchy and authority  
**Schema.org Rules**:

- `parentOrganization` for corporate structure
- `branchOf` indicates this is a branch location
- Separate address for corporate headquarters vs. local branch
- Inherits trust signals from parent organization
- Important for multi-location businesses

### 17. Web Page Context (`mainEntityOfPage`)

```json
"mainEntityOfPage": {
  "@type": "WebPage",
  "@id": "https://www.postscanmail.com/a/5101-santa-monica-blvd-ste-8.html"
}
```

**Purpose**: Links the business entity to its primary web page  
**Schema.org Rules**:

- `WebPage` type represents the HTML page containing this schema
- `@id` should match the canonical URL of the page
- Helps search engines understand page-entity relationships
- Important for knowledge graph construction and entity recognition

---

## AI Search Optimization Features

### 1. **Geographic Targeting**

- **Multi-level targeting**: City, County, Region, and Radius-based coverage
- **Disambiguation**: Wikipedia `sameAs` links prevent location confusion
- **Hierarchical structure**: `containedInPlace` establishes geographic relationships

### 2. **Service Specificity**

- **Detailed service outputs**: Each service describes specific deliverables
- **Audience targeting**: Different services target different customer segments
- **Industry keywords**: Incorporates CMRA, LLC, and business registration terminology

### 3. **Compliance Signals**

- **Regulatory credentials**: USPS CMRA authorization
- **Business identifiers**: NAICS, DUNS, LEI codes for legitimacy
- **Government organization references**: Links to official USPS resources

### 4. **Technical Optimization**

- **JSON-LD format**: Clean, crawlable structured data
- **Unique identifiers**: `@id` for entity disambiguation
- **Schema.org compliance**: Uses latest vocabulary and best practices

---

## Implementation Notes

### Required Updates

1. **Replace placeholder data** with actual business information
2. **Verify URLs** point to correct pages and resources
3. **Update certification details** with real CMRA credentials
4. **Test schema** using Google's Rich Results Test tool

### Maintenance Schedule

- **Monthly**: Review service descriptions and pricing
- **Quarterly**: Update area served and contact information
- **Annually**: Verify certifications and business identifiers
- **As needed**: Add new services or locations

### Performance Monitoring

- Monitor search console for schema errors
- Track rich result impressions and clicks
- A/B test different service descriptions
- Monitor local search ranking improvements

---

## Schema.org Resources

- **Official Documentation**: `https://schema.org/docs/schemas.html`
- **Google Rich Results Test**: `https://search.google.com/test/rich-results`
- **Schema Markup Validator**: `https://validator.schema.org/`
- **Local Business Guidelines**: `https://developers.google.com/search/docs/appearance/structured-data/local-business`

This implementation represents a comprehensive approach to Schema.org markup for virtual address services, optimized for both traditional SEO and emerging AI search technologies.
