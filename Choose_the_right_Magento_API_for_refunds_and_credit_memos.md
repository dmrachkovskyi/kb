# Choose the right Magento API for refunds and credit memos

This article is a short guide to choosing the Magento Refund API that would best match your needs.

## salesRefundInvoice service

With this service, you may initiate and process a refund based on an Invoice ID.

The service allows to:

* create a Credit Memo (complete or partial) for a particular Invoice
* add details about the refunded items to an Order
* change status and state of an Order according to performed actions
* notify a customer about the performed refund operation

More info on DevDocs:

[The RefundInvoice service](http://devdocs.magento.com/guides/v2.2/mrg/ce/Sales.html#refundinvoice)
[Magento REST API documentation (Swagger)](http://devdocs.magento.com/swagger/index.html#/)

## salesRefundOrder service

Allows to perform the same operations as with the RefundInvoice service but based on an Order ID.

More info on DevDocs:

[The RefundOrder service](http://devdocs.magento.com/guides/v2.2/mrg/ce/Sales.html#refundOrder)
[Magento REST API documentation (Swagger)](http://devdocs.magento.com/swagger/index.html#/)

## salesCreditmemoManagement service

The service also allows to initiate and process a refund but requires much more information in a request — as compared with the RefundInvoice and RefundOrder services.

The RefundInvoice and RefundOrder services are newer, more complex and universal, and may be viewed as an improvement to the CreditmemoManagement service — providing more convenience working with refunds. Still, the CreditmemoManagement service is fully valid and functional.

## salesCreditmemoRepository service

This service is only for persistence operations with refunds: it may add or update a refund, but does not process it in the Magento system.

The `POST /V1/creditmemo` method of this service allows to place a new refund (credit memo) or update an existing one, but will not process any operations with it. Sending a request with this method will not change the status of a credit memo and will not affect the refund amount; consequently, a new credit memo will not have any status and the refund amount will be zero.

## Choose a correct method with the Creditmemo services

1. Create a new credit memo and process it: use the salesCreditmemoManagementV1 service (POST /V1/creditmemo/refund method)

2. Create and update credit memos without processing them: use the salesCreditmemoRepositoryV1 service (POST /V1/creditmemo method).

Note: for the correct refund shipment, these parameters are required:

* `shipping_amount`
* `base_shipping_amount`
