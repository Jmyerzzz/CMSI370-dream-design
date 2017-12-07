# Dream Design Web Application

## Application Description
> My dream web application is an invoice managing system that sends an invoice to the receving customer. The invoice will be accessible through the application where the recipient e-signs the document. Once the document is signed, the invoice is updated and marked as received. The customer will also receive an email notification that there is an invoice with a pending signature.

### Web Service(s) Used
> The invoicing portion of my application will be handled by the PayPal API. The PayPal Invoices API has numerous built in functions, which include drafting, sending, and updating of invoices. The merchant will need to make an API call to draft/generate the invoice—this request will include customer info, billing info, and a list of purchased items. Once the invoice is drafted, another API call is required to send the invoice. Support for the electronic signature will be provided by the DocuSign API. This API has a built in function that enables the web developer to embed a secure e-signature link in the web app. After the customer e-signs the invoice, the PayPal API makes another request to update the invoice on the merchant's end.

> References:  
> https://developer.paypal.com/docs/api/invoicing/  
> https://www.docusign.com/developer-center/api-overview

## Top-Level Design/Layout
> Provide an overview of your user interface. Annotated mockups work very well here, with accompanying text describing, at a high level, the various components of your design.

## Usage Scenarios
> A usage scenario is a mini-story that highlights how a user would accomplish a certain task in your dream design. Provide at least two. Make sure to provide the following information per scenario: (a) the task that the user will perform, (b) the relevant user interface elements for performing this task, and (c) a brief narrative on how the user would perform this task with those user interface elements. Mock up, animate, or annotate your scenarios liberally.

### Usage Scenario 1
> Replace the title with an actual description of the scenario, e.g., “Adding a Song to a Playlist.”

### Usage Scenario 2
> Ditto with the title.

## Design Rationale
> State why your design is the way it is: relevant priorities, mental models, interaction design concepts, guidelines, principles, theories, etc. Cite relevant references as needed.

## Usability Metric Forecast
> If implemented then tested, what would be your design’s strong metrics? Weak metrics? Explain your choices.

## References
> Cite formally, as you would with any other research paper.
