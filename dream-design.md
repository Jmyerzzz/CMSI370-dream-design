# Dream Design Web Application

## Application Description
> My dream web application is an invoice managing system that sends an invoice to the receving customer. The invoice will be accessible through the application where the recipient e-signs the document. Once the document is signed, the invoice is updated and marked as "payment pending". The customer will also receive an email notification that there is an invoice with a pending signature.

### Web Service(s) Used
> The invoicing portion of my application will be handled by the PayPal API. The PayPal Invoices API has numerous built in functions, which include drafting, sending, and updating of invoices. The merchant will need to make an API call to draft/generate the invoice—this request will include customer info, billing info, and a list of purchased items. Once the invoice is drafted, another API call is required to send the invoice. Support for the electronic signature will be provided by the DocuSign API. This API has a built in function that enables the web developer to embed a secure e-signature link in the web app. After the customer e-signs the invoice, the PayPal API makes another request to update the invoice on the merchant's end.

> References:  
> https://developer.paypal.com/docs/api/invoicing/  
> https://www.docusign.com/developer-center/api-overview

## Top-Level Design/Layout
> Provide an overview of your user interface. Annotated mockups work very well here, with accompanying text describing, at a high level, the various components of your design.

## Usage Scenarios
> A usage scenario is a mini-story that highlights how a user would accomplish a certain task in your dream design. Provide at least two. Make sure to provide the following information per scenario: (a) the task that the user will perform, (b) the relevant user interface elements for performing this task, and (c) a brief narrative on how the user would perform this task with those user interface elements. Mock up, animate, or annotate your scenarios liberally.

### Drafting and Sending an Invoice
> The creation of an invoice is only accessible by the merchant. They merchant will start at the homepage and click on "Create" to generate a new invoice. This will bring the merchant to a new page where they are prompted to enter info into text boxes. The merchant must first enter the customer's name into the given field; the text will autocomplete the name based off of the merchant's database of customers. Each cutomer's name is associated with an object that includes billing and shipping info and their email address. All of this information will autofill into the appropriate elements in the interface so that the merchant can check its accuracy. Next, the merchant has to type in the date and each item the customer purchased. Upon being clicked, the "Item" field will turn into a drop down menu; however, it will still allow text entry. The merchant needs to enter the name, quantity, and price per unit for each item. The "Quantity" and "Price" fields only accept numbers—the standard quantity and price per unit is pounds and price per pound, respectively. If the merchant intends on entering more than three items they must click "Add Another Item" or the plus sign; another row will appear at the bottom of the list of items. As the merchant inputs quantities and prices, the "Price of Items" field will automatically update to display the cost of all the items, summing the products of quantity and price. The "Tax" field will also update automatically, multiplying the price of the items and the tax percentage. Similarly, the "Total" field will update as the user inputs items. The final step is clicking "Save & Send", which will make two API calls. The first API call will draft the invoice, taking all the info from the text fields and using it to send the request. This request will return a lot of data, but the only important piece is the ID of the invoice. Upon the succes of this API call, another API call will be made that requires two parameters: invoice_id and notify_merchant. The invoice_id is taken from the first API call and notify_merchant is always set to false so that the merchant does not receive an email. The second API call sends the invoice to the customer.

### E-Signing the Invoice
> Ditto with the title.

## Design Rationale
> State why your design is the way it is: relevant priorities, mental models, interaction design concepts, guidelines, principles, theories, etc. Cite relevant references as needed.

## Usability Metric Forecast
> If implemented then tested, what would be your design’s strong metrics? Weak metrics? Explain your choices.

## References
> Cite formally, as you would with any other research paper.
