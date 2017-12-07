# Dream Design Web Application: Invoice Manager

## Application Description
> My dream web application is an invoice managing system that sends an invoice to the receving customer. The invoice will be accessible through the application where the recipient e-signs the document. Once the document is signed, the invoice is updated and marked as "payment pending". For this app to function, the merchant and all their customers will need PayPal and DocuSign accounts.

### Web Service(s) Used
> The invoicing portion of my application will be handled by the PayPal API. The PayPal Invoices API has numerous built in functions, which include drafting, sending, and updating of invoices. The merchant will need to make an API call to draft/generate the invoice—this request will include customer info, billing info, and a list of purchased items. Once the invoice is drafted, another API call is required to send the invoice. Support for the electronic signature will be provided by the DocuSign API. This API has a built in function that enables the web developer to embed a secure e-signature link in the web app. After the customer e-signs the invoice, the PayPal API makes another request to update the invoice on the merchant's end.

> Documentation:  
> https://developer.paypal.com/docs/api/invoicing/  
> https://www.docusign.com/developer-center/api-overview

## Top-Level Design/Layout
> Provide an overview of your user interface. Annotated mockups work very well here, with accompanying text describing, at a high level, the various components of your design.
![](homepage.jpg)
![](merchant.jpg)
![](customer.jpg)

## Usage Scenarios

### Drafting and Sending an Invoice
> The creation of an invoice is only accessible by the merchant. They merchant will start at the homepage and click on "Create" to generate a new invoice. This will bring the merchant to a new page where they are prompted to enter info into text boxes. The merchant must first enter the customer's name into the given field; the text will autocomplete the name based off of the merchant's database of customers. Each cutomer's name is associated with an object that includes billing and shipping info and their email address. All of this information will autofill into the appropriate elements in the interface so that the merchant can check its accuracy. Next, the merchant has to type in the date and each item the customer purchased. Upon being clicked, the "Item" field will turn into a drop down menu; however, it will still allow text entry. The merchant needs to enter the name, quantity, and price per unit for each item. The "Quantity" and "Price" fields only accept numbers—the standard quantity and price per unit is pounds and price per pound, respectively. If the merchant intends on entering more than three items they must click "Add Another Item" or the plus sign; another row will appear at the bottom of the list of items. As the merchant inputs quantities and prices, the "Price of Items" field will automatically update to display the cost of all the items, summing the products of quantity and price. The "Tax" field will also update automatically, multiplying the price of the items and the tax percentage. Similarly, the "Total" field will update as the user inputs items. The final step is clicking "Save & Send", which will make two API calls. The first API call will draft the invoice, taking all the info from the text fields and using it to send the request. This request will return a lot of data, but the only important piece is the ID of the invoice. Upon the succes of this API call, another API call will be made that requires two parameters: invoice_id and notify_merchant. The invoice_id is taken from the first API call and notify_merchant is always set to false so that the merchant does not receive an email notification. The second API call sends the invoice to the customer.

### E-Signing an Invoice
> Once the customer receives an invoice, it will be added to the list of invoices that are pending a signature. Upon clicking the "Pending Invoices" button, the "Invoice" element will be populated with a clickable list of all the invoices that still require a signature. Clicking on one of the invoices will change the "Invoice" element to show the selected invoice. Here, the customer can review the invoice. Signing and returning the invoice to the merchant only requires a single click of the "Sign & Send" button. This action will result in two API calls. First, the DocuSign API will send a request with the customer's unique ClientUserId and a status. This request will return an event parameter equal to signing_complete. Upon the succes of this API call, the PayPal API will update the invoice. This request also requires both invoice_id and notify_merchant parameters; however, notify_merchant will be set to true so that they receive a notification. The request will update merchant_memo, an element in the invoice object, so that it is equal to "Invoice Signed". This API call will mark the invoice as signed and move it out of the "Pending Invoices" list. However, if the customer notices the invoice is incorrect then they must contact the merchant so they can update it and send it back to the customer.

## Design Rationale
> State why your design is the way it is: relevant priorities, mental models, interaction design concepts, guidelines, principles, theories, etc. Cite relevant references as needed.

## Usability Metric Forecast
> If implemented then tested, what would be your design’s strong metrics? Weak metrics? Explain your choices.

## References
> Cite formally, as you would with any other research paper.
