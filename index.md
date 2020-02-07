---
layout: default
title: Datafund Consent Receipt Suite
nav_order: 2
tags: consent, documentation, datafund
---

The Consent Receipt Suite by [Datafund](https://datafund.io/) is a suite of open source programs in [React](https://reactjs.org/) that you can integrate into your product to allow you to issue and work with [Kantara](https://kantarainitiative.org/confluence/display/infosharing/Consent+Receipt+Specification) compliant consent receipts enabling also blockchain traceability, signing and storing them on [Swarm](https://swarm-guide.readthedocs.io/en/latest/introduction.html) decentralized storage.

# Table of Contents
{: .no_toc}


1. TOC
{:toc}

# About Consent Receipt Suite


A general overview of the Consent Receipt Suite can also be found in the blog post [TLDR: Consent Receipt Suite — what is it about … ?](https://blog.datafund.net/tldr-consent-receipt-suite-what-is-it-about-88c8da9531b7), along with videos demoing its functionalities.

Consent Receipts from the point of view of the individual are explained in the blog post [You get a receipt for groceries, why not data?](https://blog.datafund.net/you-get-a-receipt-for-groceries-why-not-data-cf55a8db81c2).

Developers should also read the blog post [Developers — move your apps towards GDPR-compliance, easy, fast & free](https://blog.datafund.net/developers-move-your-apps-towards-gdpr-compliance-easy-fast-free-af5d61f1a80e) to rationalize the usage of the Suite.

The motivation for companies is described in the blog post [Take your company into the fair data economy](https://blog.datafund.net/take-your-company-into-the-fair-data-economy-965598d32412).

## About Consent Receipts

With GDPR, the need to have proper processes in place related to personally identifiable data (PII) became a necessity. Consent by the individual is needed in many cases, when PII are processed. Consent receipts are a way to record a given consent in a standardized way.

Having a consent receipt is good for both the individual as well as for the data controller. It is a record of agreement about usage of PII that both parties can refer to. Additional solutions can also be offered on top of these records -- opening a way towards more advanced data economy services.

Datafund specializes in developing the solutions, so you don't have to. Consent receipts were implemented according to Kantara specification, funded by the Sitra fund. And are now available open source and free for you to use.

Kantara is developing the specification further and we plan to update it, when a new version is accepted. In addition to providing a Kantara compliant consent receipt, we have also added decentralized Swarm storage and blockchain signing of the transactions to the packages. The signing features offer proof of consent, that is not legally required, but should became standard in our belief. Decentralized Swarm storage allows the consent receipts to be immediately stored in a secure and always-on storage, where the individual and the data controller can access them as needed.

## Workings of Consent Receipt suite

![image](https://user-images.githubusercontent.com/1554520/59093151-86c5ba80-8913-11e9-9bba-0a67af598133.png)

The "CR JSONSchema" defines the structure of a CR. Starting from the schema, the PII Controller can generate a "proposed CR JSON", by adding values to all the relevant fields. The "proposed CR JSON" should be presented to the PII Principal in an appropriate way (human readable and possibly using one of the developed modules). PII Principal can  give his consent, after which a "CR JWT" is generated which both the Controller and Principal can save (to different variants of storage).

Building upon the [React JSONSchema framework](https://mozilla-services.github.io/react-jsonschema-form/), the presentation of CR on screen in either the human readable and read only form or the more flexible editable form used by the PII controller will be achieved by a combination of CR JSONSchema (defining the structure and allowed values), UISchema (defining the controls / menus displayed on screen), formData (defining the default / displayed values) and CSS styles (defining the look of the UI).

![image](https://user-images.githubusercontent.com/1554520/59093196-a230c580-8913-11e9-9a45-254204574f73.png)

All the parts are saved in the form of a JSON project file, that can be used as a template.


# How to integrate consent receipt libraries into your solutions

The table shows the Consent Receipt Suite packages available, that you can use and integrate into your application. Each one can be used individually, but together they offer all the functionalities.

| Description                                                  | GitHub                                                   | npm.js                                                       | Web     | Swarm     |
| ------------------------------------------------------------ | -------------------------------------------------------- | ------------------------------------------------------------ | ---- | ---- |
| Consent Receipt Generator                                    | [dr-generator](https://github.com/datafund/dr-generator) | [@datafund/consent-generator](https://www.npmjs.com/package/@datafund/consent-generator) |      |      |
| Consent Receipt Viewer                                       | [dr-viewer](https://github.com/datafund/dr-viewer)       | [@datafund/consent-viewer](https://www.npmjs.com/package/@datafund/consent-viewer) |      |      |
| Consent Receipt Summary Viewer                               | [dr-summary](https://github.com/datafund/dr-summary)                                               | [@datafund/consents-summary](https://www.npmjs.com/package/@datafund/consents-summary) |      |      |
| A helper library for working with Consent Receipts on the blockchain | [datareceipt.js](https://github.com/datafund/datareceipt.js)                                           | [@datafund/data-receipt](https://www.npmjs.com/package/@datafund/data-receipt) |      |      |
| Sample React and integration for using consent on the blockchain | [df-fds-consent-manager](https://github.com/datafund/df-fds-consent-manager)                                   |                                                              |      |      |
| Sample node.js API server implementation for generating consent token (JWT) | [dr-api-server](https://github.com/datafund/dr-api-server)                                            |                                                              |      |      |
| Consent Receipt Suite Demo app demonstrating functionalities of the  generator, viewer, blockchain transactions and Swarm storage | [dr-editor-sample](https://github.com/datafund/dr-editor-sample)                                         |                                                              | [Web link](https://consents.fairdrop.one/#/)     |      |


The main packages are in the form of React components that can be included in your software.

The objective of this part is to give you enough of an overview of the packages and how they fit together for you to be able to use them in your own software.

### Consent Receipt Generator

The Consent Receipt Generator is meant to be used for editing the contents of the consent receipt.

### Consent Receipt Viewer

The Consent Receipt Viewer is meant for displaying a human readable consent receipt from the JSON data.

### Consent Receipt Summary Viewer

The Consent Receipt Summary Viewer is meant for displaying most important summary data of several consent receipts at once, in a tabular view.

### DataReceipt.js
Is a helper library for working with Consent Receipts on the blockchain. It encapsulates creation of FDS accounts, creation of Consent Receipts JWT tokens, sending over Swarm, decoding and verifying tokens with additional layer to support Consent Manager smart contract and consent signing and verification of Consent smart contract on blockchain. It sits on top of fds.js.
`Consent Manager` smart contract creates `Consent` contracts and acts as interface to them.

See details on [GitHub](https://github.com/datafund/datareceipt.js).

### Sample React and integration for using consent on the blockchain

A sample how to initialize fds.js and datareceipt.js. Sample consent is generated, signed and sent to another account. It's meant as a simplified reference implementation.

### Sample node.js API server implementation for generating consent token (JWT)

API server implementation is an example of a server for signing a proposed consent receipt and making it into a consent receipt JWT. It is runs in Node.js environment. **NOTE: It is not meant to be used in a production environemnt as-is, as it should not be considered secured enough. Consider it a reference implementation. Putting private key in .js script is NOT considereg secure**

### Consent Receipt Suite Demo

The Consent Receipt Suite Demo is a reference implementation of all the modules bundled into one application. It is meant for demos.

Contains all modules, editor, generator, summary viewer, consent viewer and uses uses datareceipt.js and fds.js.

#### Decentralized Consent Receipt Suite Demo

To deploy it yourself
run `npm run build`

then upload it to Swarm through gateway (if you don't run your own swarm node)
`swarm.exe --bzzapi https://swarm.fairdatasociety.org --defaultpath index.html --recursive up .\build\`

## Putting it all together

The modules can be used independently or in concert. The Sample Demo app was constructed with intent to demonstrate usability and as a reference implementation.

If you encounter an issues, have any questions open an issue on GitHub in https://github.com/datafund/dr-editor-sample.

# References / additional information

- [TLDR: Consent Receipt Suite — what is it about … ?](https://blog.datafund.net/tldr-consent-receipt-suite-what-is-it-about-88c8da9531b7)
- [Datafund Github](https://github.com/datafund)
- [Datafund webpage](https://datafund.io/)
- [Kantara initiative](https://kantarainitiative.org)
- [Kantara initiative consent receipt specification](https://kantarainitiative.org/confluence/display/infosharing/Consent+Receipt+Specification)
- [Sitra Finnish Innovation Fund](https://www.sitra.fi/en/)
- [Sitra on Fair data economy](https://www.sitra.fi/en/topics/fair-data-economy/)
- [Fair Data Society webpage](https://fairdatasociety.org/)
- [Fair Data Society Github](https://github.com/fairDataSociety)
- [Fairdrop personal storage Dapp (test version)](https://staging.fairdrop.xyz/)
- [Chattie chat Dapp (test version)](https://staging.chattie.xyz/)
- [Chattie Dapp Howto blog](https://blog.datafund.net/chattie-or-how-to-build-a-decentralised-chat-app-in-10-minutes-72ba816b88)
