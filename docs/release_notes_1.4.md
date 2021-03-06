---
layout: default
---

## Invoice 1.4 Release Notes
### <a name="response_code"></a> 28 july 2020 - PaymentReference
Due to restrictions in external systems we added recommendation to keep `PaymentReference` up to 30 symbols for [direct invoice](api_reference#single-invoice-request) and [invoice link](api_reference#invoice-link-request) requests.

### <a name="response_code"></a> 26 june 2020 - User consent for InvoiceDirect released in Sandbox
New feature: User consent for InvoiceDirect. Read more about user consent for InvoiceDirect [here](https://mobilepaydev.github.io/MobilePay-Invoice/api_reference#direct-invoice-consent) 

Goal of this functionality is for invoice issuer to ask users phone number and consent to receive Invoices directly to MobilePay (InvoiceDirect). Current release is just in Sandbox. Release in Production is planned for beginning of August. App version from which functionality can work for users - 4.24.0 (July).

### <a name="response_code"></a> 23 april 2020 - ConsumerName and ConsumerAddressLines now optional
Removed **Required** validation for `ConsumerName` and `ConsumerAddressLines`

### <a name="response_code"></a> 17 february 2020 - Increased max number of invoices to one user
Increased the max number of invoices per day merchants can send to one user. Now merchants can send up to 10 invoices to one user.

### <a name="response_code"></a> 17 february 2020 - Removed Merchant daily Invoice limit
Daily invoice <code>Limit</code> for merchants was removed.

### <a name="response_code"></a> 16 january 2020 - Increased Invoice FI amount
Invoice FI <code>Amount</code> validation was increased to 2000 EUR

### <a name="response_code"></a> 08 november 2019 - Removed consumer name validation
<code>ConsumerName</code> validation (Levenshtein rule) was removed from InvoiceDirect validation rules.
However, it is still used for displaying <code>ConsumerName</code> when generating invoice PDF.


### <a name="response_code"></a> 06 august 2019 - Response Code 
The response codes for invoices have been unified. Batch requests now return <code>202</code> , all others should now return <code>200</code> 
If your system logic examines the concrete response code and checks strict the status code, you may have to change the logic in order to cope with the change in response code. We do not consider this a breaking chance, as most merchants only check if the call was a success such as 2xx, and do not depend on a concrete status code. However, having the right HTTP status codes mapped also enables you to get more insight around the response received.

### <a name="decimals"></a> 01 april 2019 - decimals
<code>TotalVATAmount</code> can not have more than two decimals. 


### <a name="response_code"></a> 01 march 2019 - QR code

New feature: Scanning QR code with InvoiceLink will open MobilePay Invoice

We're excited to announce, that MobilePay's own QR code reader can now read a QR code, that contains InvoiceLink. Read more about InvoiceLink [here](https://github.com/MobilePayDev/MobilePay-Invoice/blob/master/docs/api_reference.md#-invoicelink) 
- When you scan a QR with the MobilePay app, and the QR contains InvoiceLink, then the Invoice context screen is opened.
- If the scanned link is already expired, then the user will see an error message in the overlay screen
- If the invoice is expired, then the endpoint will return a 404 status

[![](assets/images/android_fi2.jpg)](assets/images/android_fi2.jpg)    

### <a name="Merchant-PDF"></a> Provide your own PDF for invoice
Currenlty, PDF file of the invoice is generated internally by MobilePay. With release of **Invoice 1.4** merchants now have a possibility to provide the URL to their own PDF file.

If you create an invoice with <code>InvoiceUrl</code> parameter filled in, user will be redirected to the URL from the app when showing an invoice, otherwise the previous flow of showing PDF generated by MobilePay internally will apply.

The following endpoints will be extended to accept an optional <code>InvoiceUrl</code> parameter:

```
POST api/v1/merchants/{merchantId}/invoices
POST api/v1/merchants/{merchantId}/invoices/batch
POST api/v1/merchants/{merchantId}/invoices/link
POST api/v1/merchants/{merchantId}/invoices/link/batch
```

##### <a name="single_invoice_object"/> Input

|Parameter             |Type        |Description |
|----------------------|------------|------------|
|`InvoiceUrl`    ?? ?? ?? |`string`    |URL to the Invoice PDF provided by merchant.|

<div class="note">
<strong>Note:</strong> Only HTTPS scheme URLs will be supported.
</div>

##### Create Invoice Direct example

```json
{
  "InvoiceIssuer": "efd08c19-24cf-4833-a4a4-bfa7bd58fbb2",
  "ConsumerAlias": {
    "Alias": "+4577007700",
    "AliasType": "Phone"
  },
  "ConsumerName": "Consumer Name",
  "TotalAmount": 360,
  "TotalVATAmount": 72,
  "CountryCode": "DK",
  "CurrencyCode": "DKK",
  "ConsumerAddressLines": [
    "Paradis??blevej 13",
    "CC-1234 Andeby", 
    "WONDERLAND"
  ],
  "DeliveryAddressLines": [
    "??sterbrogade 120",
    "CC-1234 Andeby",
    "WONDERLAND"
  ],
  "InvoiceNumber": "301",
  "IssueDate": "2018-02-12",
  "DueDate": "2018-03-12",
  "OrderDate": "2018-02-05",
  "DeliveryDate": "2018-02-10",
  "Comment": "Any comment",
  "MerchantContactName": "Snowboard gear shop",
  "MerchantOrderNumber": "938",
  "BuyerOrderNumber": "631",
  "PaymentReference": "186",
  "InvoiceArticles": [
    {
      "ArticleNumber": "1-123",
  "ArticleDescription": "Process Flying V Snowboard",
      "VATRate": 25,
      "TotalVATAmount": 72,
      "TotalPriceIncludingVat": 360,
      "Unit": "1",
      "Quantity": 1,
      "PricePerUnit": 288,
      "PriceReduction": 0,
      "PriceDiscount": 0,
      "Bonus": 5
    }      
  ],
  "InvoiceUrl": "https://www.merchant.dk/invoice/efd08c19-24cf-4833-a4a4-bfa7bd58123"
}
```
##### Create Invoice Link example

```json
{
  "InvoiceIssuer": "efd08c19-24cf-4833-a4a4-bfa7bd58fbb2",
  "ConsumerAlias": {
    "Alias": "+4577007700",
    "AliasType": "Phone"
  },
  "ConsumerName": "Consumer Name",
  "TotalAmount": 360,
  "TotalVATAmount": 72,
  "CountryCode": "DK",
  "CurrencyCode": "DKK",
  "ConsumerAddressLines": [
    "Paradis??blevej 13",
    "CC-1234 Andeby", 
    "WONDERLAND"
  ],
  "DeliveryAddressLines": [
    "??sterbrogade 120",
    "CC-1234 Andeby",
    "WONDERLAND"
  ],
  "InvoiceNumber": "301",
  "IssueDate": "2018-02-12",
  "DueDate": "2018-03-12",
  "OrderDate": "2018-02-05",
  "DeliveryDate": "2018-02-10",
  "Comment": "Any comment",
  "MerchantContactName": "Snowboard gear shop",
  "MerchantOrderNumber": "938",
  "BuyerOrderNumber": "631",
  "PaymentReference": "186",
  "InvoiceArticles": [
    {
      "ArticleNumber": "1-123",
      "ArticleDescription": "Process Flying V Snowboard",
      "VATRate": 25,
      "TotalVATAmount": 72,
      "TotalPriceIncludingVat": 360,
      "Unit": "1",
      "Quantity": 1,
      "PricePerUnit": 288,
      "PriceReduction": 0,
      "PriceDiscount": 0,
      "Bonus": 5
    }      
  ],
  "InvoiceUrl": "https://www.merchant.dk/invoice/efd08c19-24cf-4833-a4a4-bfa7bd58124"
}
```
