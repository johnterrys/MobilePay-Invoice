---
layout: default
---

## Visual examples

### <a name="payment-screens"></a> User pays invoice 

[![](assets/images/how_user_initiates_payment.jpeg)](assets/images/how_user_initiates_payment.jpeg)

[![](assets/images/pay_invoice_now.jpeg)](assets/images/pay_invoice_now.jpeg)

[![](assets/images/schedule_invoice_payment_for_future.jpeg)](assets/images/schedule_invoice_payment_for_future.jpeg)


### <a name="review-invoice"></a> View bill
[![](assets/images/view_bill.jpeg)](assets/images/view_bill.jpeg)

### <a name="reject-invoice"></a> Reject Invoice

[![](assets/images/reject_invoice.jpeg)](assets/images/reject_invoice.jpeg)

### <a name="pdf"></a> PDF example
Image explains what data of merchant/invoice issuer/invoice is used in the generated PDF and where.
[![](assets/images/pdf.png)](assets/images/pdf.png)

| Marking<br>from<br>an example | Mapping Invoice                                                     | EN                | DK                    | FI                   |
|-------------------------------|---------------------------------------------------------------------|-------------------|-----------------------|----------------------|
|                             1 | Hardcoded                                                           | Invoice           | FAKTURA               | LASKU                |
|                             2 | Invoice issuer logo                                                 | N/A               | N/A                   | N/A                  |
|                             3 | Invoice Issuer name                                                 | N/A               | N/A                   | N/A                  |
|                             4 | Invoice issuer address                                              | N/A               | N/A                   | N/A                  |
|                             5 | Merchant CVR                                                        | Company ID        | CVR                   | Y-tunnus             |
|                             6 | MerchantContanctName                                                | N/A               | N/A                   | N/A                  |
|                             7 | ConsumerName                                                        | N/A               | N/A                   | N/A                  |
|                             8 | ConsumerAddressLines                                                | N/A               | N/A                   | N/A                  |
|                             9 | Alias                                                               | N/A               | N/A                   | N/A                  |
|                            10 | DeliveryAddressLines                                                | Delivery address  | Leveringsadresse      | Toimitusosoite       |
|                            11 | DeliveryDate                                                        | Delivery date     | Leveringsdato         | Toimitusp??iv??        |
|                            12 | BuyerOrderNumber                                                    | Buyers order ID   | K??bers ordrenummer    | Ostajan tilausnumero |
|                            13 | MerchantOrderNumber                                                 | Merchant order ID | S??lgers ordrenummmer  | Myyj??n tilausnumero  |
|                            14 | OrderDate                                                           | Order date        | Ordredato             | P??iv??                |
|                            15 | InvoiceNumber                                                       | Invoice number    | Fakturanummer         | Laskun numero        |
|                            16 | IssueDate                                                           | Issue date        | Fakturadato           | Laskun p??iv??         |
|                            17 | DueDate                                                             | Due date          | Betalingsdato         | Er??p??iv??             |
|                            18 | PaymentReference                                                    | Payment reference | Betalingsreference    | Maksun viite         |
|                            19 | ArticleNumber                                                       | Item ID           | Varenummer            | Tuotenumero          |
|                            20 | ArticleDescription                                                  | Description       | Beskrivelse           | Kuvaus               |
|                            21 | Quantity                                                            | Quantity          | Antal                 | M????r??                |
|                            22 | Unit                                                                | Type              | Enhed                 | Yksikk??              |
|                            23 | PricePerUnit                                                        | Quantity price    | Enhedspris            | Yksikk??hinta         |
|                            24 | VATRate %                                                           | VAT               | Moms                  | ALV                  |
|                            25 | TotalPriceIncludingVat                                              | Total             | Total                 | Yhteens??             |
|                            26 | Sum  of  PriceReduction                                             | Price deduction   | Total prisneds??ttelse | Kokonaishinta        |
|                            27 | Sum  of  PriceDiscount                                              | Discount          | Total rabat           | Alennus              |
|                            28 | Sum of Bonus                                                        | Bonus             | Total bonus           | Kokonaisbonus        |
|                            29 | Calculated<br>TotalAmount - (sum of InvoiceArticles.TotalVATAmount) | Total ex VAT      | Total uden moms       | Yhteens?? ilman ALV   |
|                            30 | TotalVatAmount                                                      | Total VAT         | Moms                  | ALV yhteens??         |
|                            31 | TotalAmount                                                         | Total             | Total                 | Yhteens??             |
|                            32 | Comment                                                             | Comments          | Kommentar             | Kommentit            |


### <a name="link-flows"></a> InvoiceLink flows

#### Dual device flow
Scheme represents flow when user press on `InvoiceLink` link in the desktop device or tablet.
[![](assets/images/lp/dual_device_flow.png)](assets/images/lp/dual_device_flow.png)

#### Single device flow
Scheme represents flow when user press on `InvoiceLink` link in the mobile device (except tablet).
[![](assets/images/lp/single_device_flow.png)](assets/images/lp/single_device_flow.png)
