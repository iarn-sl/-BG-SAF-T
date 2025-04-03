# -BG-SAF-T
SAF-T General

1. Main Entity: InvoiceStructure

    Fields to Populate:
        InvoiceNo (string, max length 70)
        AccountID (string, max length 70)
        BranchStoreNumber (string, max length 35)
        Period (string)
        PeriodYear (string)
        InvoiceDate (DateTime)
        InvoiceType (string, max length 9)
        PaymentTerms (string, max length 70)
        SelfBillingIndicator (string, max length 9)
        SourceID (string, max length 35)
        BatchID (string, max length 35)
        SystemID (string, max length 35)
        TransactionID (string, max length 70)
        ReceiptNumbers (string, max length 256)

    Connections:
        CustomerInfo (InvoiceStructureCustomerInfo)
        SupplierInfo (InvoiceStructureSupplierInfo)
        ShipTo (ShippingPointStructure)
        ShipFrom (ShippingPointStructure)
        InvoiceLine (Collection of InvoiceStructureInvoiceLine)
        InvoiceSettlement (InvoiceStructureInvoiceSettlement)
        InvoiceDocumentTotals (InvoiceStructureInvoiceDocumentTotals)

2. Customer Information: InvoiceStructureCustomerInfo

    Fields to Populate:
        CustomerID (string, max length 35)
        Name (string, max length 70)
        BillingAddress (AddressStructure)

3. Supplier Information: InvoiceStructureSupplierInfo

    Fields to Populate:
        SupplierID (string, max length 35)
        Name (string, max length 70)
        BillingAddress (AddressStructure)

4. Address Structure: AddressStructure

    Fields to Populate:
        StreetName (string, max length 70)
        Number (string, max length 18)
        AdditionalAddressDetail (string, max length 70)
        Building (string, max length 35)
        City (string, max length 35)
        PostalCode (string, max length 18)
        Region (string, max length 35)
        Country (string)
        AddressType (AddressStructureAddressType)

5. Shipping Point Structure: ShippingPointStructure

    Fields to Populate:
        DeliveryID (string, max length 35)
        DeliveryDate (DateTime, nullable)
        WarehouseID (string, max length 35)
        LocationID (string, max length 18)
        UCR (string, max length 35)
        Address (AddressStructure)

6. Invoice Line: InvoiceStructureInvoiceLine

    Fields to Populate:
        LineNumber (string, max length 18)
        AccountID (string, max length 70)
        GoodsServicesID (string, max length 9)
        ProductCode (string, max length 70)
        ProductDescription (string, max length 256)
        Quantity (decimal)
        InvoiceUOM (string, max length 9)
        UnitPrice (decimal)
        TaxPointDate (DateTime)
        Description (string, max length 256)
        DebitCreditIndicator (InvoiceStructureInvoiceLineDebitCreditIndicator)
        InvoiceLineAmount (AmountStructure)
        ShippingCostsAmount (AmountStructure)

7. Amount Structure: AmountStructure

    Fields to Populate:
        Amount (decimal)
        CurrencyCode (string)
        CurrencyAmount (decimal)
        ExchangeRate (decimal, nullable)

8. Invoice Settlement: InvoiceStructureInvoiceSettlement

    Fields to Populate:
        SettlementDiscount (string, max length 35)
        SettlementAmount (AmountStructure)
        SettlementDate (DateTime, nullable)
        PaymentMechanism (string, max length 9)

9. Invoice Document Totals: InvoiceStructureInvoiceDocumentTotals

    Fields to Populate:
        NetTotal (decimal)
        GrossTotal (decimal)
        ShippingCostsAmountTotal (decimal, nullable)
        TaxInformationTotals (Collection of TaxInformationStructure)

10. Tax Information Structure: TaxInformationStructure

    Fields to Populate:
        TaxType (string, max length 9)
        TaxCode (string, max length 9)
        TaxPercentage (decimal, nullable)
        TaxBase (decimal, nullable)
        TaxBaseDescription (string, max length 70)
        TaxAmount (AmountStructure)
        TaxExemptionReason (string, max length 70)
        TaxDeclarationPeriod (string, max length 35)

Connections Summary

    The InvoiceStructure is the central entity that connects to customer and supplier information, shipping details, invoice lines, and settlement information.
    Each invoice line can have multiple tax information entries, and the document totals aggregate values from the invoice lines.
    Address structures are used for both customer and supplier billing addresses, as well as shipping points.

This structured analysis provides a clear overview of the fields that need to be populated and the relationships between different entities in the schema.


Relationships Between Entities in the Invoice Schema

The schema defines a complex structure with various entities that are interconnected. Below is a detailed description of the relationships between these entities, along with examples to illustrate each relationship.
1. InvoiceStructure

    Description: The main entity representing an invoice.
    Relationships:
        CustomerInfo: Contains details about the customer associated with the invoice.
        SupplierInfo: Contains details about the supplier associated with the invoice.
        ShipTo: Represents the shipping address for the invoice.
        ShipFrom: Represents the origin address for the invoice.
        InvoiceLine: A collection of invoice line items that detail the products or services sold.
        InvoiceSettlement: Contains information about any settlements related to the invoice.
        InvoiceDocumentTotals: Aggregates totals for the invoice, including net and gross amounts.

Example:

InvoiceStructure

  ├── CustomerInfo (InvoiceStructureCustomerInfo)
  ├── SupplierInfo (InvoiceStructureSupplierInfo)
  ├── ShipTo (ShippingPointStructure)
  ├── ShipFrom (ShippingPointStructure)
  ├── InvoiceLine (Collection of InvoiceStructureInvoiceLine)
  ├── InvoiceSettlement (InvoiceStructureInvoiceSettlement)
  └── InvoiceDocumentTotals (InvoiceStructureInvoiceDocumentTotals)
  
2. InvoiceStructureCustomerInfo

    Description: Contains information about the customer.
    Relationships:
        BillingAddress: An instance of AddressStructure that provides the customer's billing address.

Example:

InvoiceStructureCustomerInfo

  ├── CustomerID: "CUST123"
  ├── Name: "John Doe"
  └── BillingAddress (AddressStructure)

3. InvoiceStructureSupplierInfo

    Description: Contains information about the supplier.
    Relationships:
        BillingAddress: An instance of AddressStructure that provides the supplier's billing address.

Example:

InvoiceStructureSupplierInfo

  ├── SupplierID: "SUPP456"
  ├── Name: "ABC Supplies"
  └── BillingAddress (AddressStructure)

4. AddressStructure

    Description: Represents an address.
    Relationships:
        Used in both InvoiceStructureCustomerInfo and InvoiceStructureSupplierInfo for billing addresses.
        Used in ShippingPointStructure for shipping addresses.

Example:

AddressStructure

  ├── StreetName: "123 Main St"
  ├── Number: "45"
  ├── City: "Metropolis"
  ├── PostalCode: "12345"
  └── Country: "CountryName"

5. ShippingPointStructure

    Description: Represents shipping points for the invoice.
    Relationships:
        Address: An instance of AddressStructure that provides the address for shipping.

Example:

ShippingPointStructure

  ├── DeliveryID: "DEL001"
  ├── WarehouseID: "WH001"
  └── Address (AddressStructure)

6. InvoiceStructureInvoiceLine

    Description: Represents individual line items in the invoice.
    Relationships:
        ShipTo: Can reference a shipping point for the line item.
        ShipFrom: Can reference a shipping point for the line item.
        Analysis: Can contain analysis structures for additional categorization.
        TaxInformation: Can contain tax information related to the line item.

Example:

InvoiceStructureInvoiceLine

  ├── LineNumber: "1"
  ├── ProductCode: "PROD789"
  ├── Quantity: 10
  ├── UnitPrice: 15.00
  └── TaxInformation (Collection of TaxInformationStructure)

7. InvoiceStructureInvoiceSettlement

    Description: Contains settlement information for the invoice.
    Relationships:
        SettlementAmount: An instance of AmountStructure that details the settlement amount.

Example:

InvoiceStructureInvoiceSettlement

  ├── SettlementDiscount: "5%"
  └── SettlementAmount (AmountStructure)

8. InvoiceStructureInvoiceDocumentTotals

    Description: Aggregates totals for the invoice.
    Relationships:
        TaxInformationTotals: A collection of tax information structures that summarize tax details.

Example:

InvoiceStructureInvoiceDocumentTotals

  ├── NetTotal: 150.00
  ├── GrossTotal: 157.50
  └── TaxInformationTotals (Collection of TaxInformationStructure)

9. TaxInformationStructure

    Description: Represents tax-related information.
    Relationships:
        Can be associated with both InvoiceStructureInvoiceLine and InvoiceStructureInvoiceDocumentTotals.

Example:

TaxInformationStructure

  ├── TaxType: "VAT"
  ├── TaxCode: "VAT20"
  └── TaxAmount (AmountStructure)

Summary of Relationships

    The InvoiceStructure serves as the central entity connecting customer and supplier information, shipping details, line items, and settlement information.
    Each InvoiceLine can have multiple TaxInformation entries, and the InvoiceDocumentTotals aggregates values from the invoice lines.
    AddressStructure is reused across different entities for billing and shipping addresses, demonstrating a clear relationship between customers, suppliers, and shipping points.

This structured overview provides a clear understanding of how the entities are interconnected within the invoice schema, along with practical examples to illustrate these relationships.
