![RealMatter](https://curator.artracx.com/wp-content/uploads/2022/11/RealMatter-Badgets-ea45e0e1.png)
# RealMatter DID:RM Method
did : rm : <ledger[1 *]> : <id[40 *]>

Technical Paper for W3C DID Registration

## Official DID:ART Method in W3C Registry

Merging into W3C Github DID Test Suite and DID Registry

## Real Matter Technology Limited
[realmatter.io](https://realmatter.io)

**Author** 
- Ming-lam Ng (RealMatter)

**Editor** 
- Daniel Chun (RealMatter)

**Advisors** 
- Paul Cheng, Emil Chan

**Contact** 
- mn@realmatter.io

**Date** 
- 30 Nov 2022

**Version** 
- First copy V1.0



## About Real Matter

Real Matter Technology Limited, 
a member of Ideation Program with Hong Kong Science Park, 
is a FinTech company with the vision to implement Chip-level blockchain identity technology with Smart legal contracts to create Real-world asset tokenization and formulate Investor exit plans.

This document specifies the “RealMatter” [DID Method](https://w3c.github.io/did-spec-registries/#did-methods) [**did:rm**].

RealMatter uses virtualassets.id as the official service website.

**Connecting real assets to virtual identities**

by
Chip-level Blockchain
Real-world Asset Tokenization
Smart Legal Contracts
Investor Exit Planning


**Real-world Asset Tokenization**

Investor exit planning is the most important part of Real-world Asset Tokenization

asset tokenization is # NOT nft
asset tokenization is # NOT opensea
asset tokenization is # investment
asset tokenization is # an exit plan


**RealMatter Platform**

 ![Identity platform](https://curator.artracx.com/wp-content/uploads/2022/11/RealMatter-Badgets-4-1dbc08dc.png) 
 ![Verifiable Credential platform](https://curator.artracx.com/wp-content/uploads/2022/11/RealMatter-Badgets-5-a1562fc0.png) 


## Conformity

This DID method specification conforms to the requirements specified in the DID specification currently published by the W3C Credentials Community Group. For more information about DIDs and DID method specifications, please see DID Primer and DID Specification.

The following DID Method will be registered in the DID Specification Registries (https://w3c.github.io/did-spec-registries/#did-methods).


## Status of This Document

This document was published as an Editor's Draft. Publication as an Editor's Draft does not imply endorsement by the W3C Membership. This is a draft document and may be updated, replaced or obsoleted by other documents at any time. It is inappropriate to cite this document as other than a work in progress.


## DID:RM Block Diagram

![RealMatter DID Block Diagram](https://curator.artracx.com/wp-content/uploads/2022/11/WhatsApp-Image-2022-11-30-at-4.06.48-PM-05db6f49.jpeg)


## DID:RM DID Method

The namestring that shall identify this DID method is : **rm**

A DID that uses this method MUST begin with the following prefix: did:rm. Per the DID specification, this string MUST be in lowercase. 


**DID Format**

```
RealMatter DID =  did: rm: method-specific-ledger-id: method-specific-subject-id 
method-specific-ledger-id  =  1*idchar   where idchar = 0-9 / a-z
method-specific-subject-id =  40*idhex   where idhex  = 0-9 / a-f
```

This generic DID scheme is a URI scheme conformant with [RFC3986](https://www.ietf.org/rfc/rfc3986.txt)

where 

method-specific-ledger-id refers to [Enecuum](https://enecuum.com/) ENQ pubic blockchain

method-specific-subject-id refers to a string of 40 hexadecimal characters

example :

did: rm: enq: f045c5c7d50145b65ca2702c38b4e2d46658293c


**Method Specific Subject ID Generation**

Take the highly secured key tag hardware as a default contract , method-specific-subject-id should be encoded as follow:

Retrieve the hardware RNG generated public key in the highly secured key tag hardware

Hash the public key and take the first 20 hex digits

Use the multibase format [base16](https://tools.ietf.org/id/draft-multiformats-multibase-00.html#RFC4648) to encode the first 20 digits without the prefix letter of base16 identifier to obtain the method-specific-subject-id in 40 hexadecimal characters.


## RealMatter DID Document
```
     {
        "@context": [
          "https://www.w3.org/ns/did/v1",
          "https://w3c-ccg.github.io/ld-cryptosuite-registry/#ecdsasecp256k1signature2019"
        ],
        "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
        "verificationMethod": [
          {
            "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey",
            "type": "EcdsaSecp256k1VerificationKey2019",
            "controller": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
            "publicKeyMultibase": "fef2823c7d237bd094d633a1765d5896b0f442481a997da2f83d7a928ddce7e65",
            "blockchainAccountId":"enq:f045c5c7d50145b65ca2702c38b4e2d46658293c"
          }
        ],
        "authentication": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "assertionMethod": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "service": [
          {
	    "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#service",
    	    "type": "LinkedDomains",
    	    "serviceEndpoint": "https://virtualassets.id"
          }
        ]
      }
```


## DID Path, Query and Fragment 


**Path**

One type of path is supported in this version

/contract : response = smart contract information, e.g. brief description of contract


**Query**

No query is supported in this version


**Fragment**

One type of fragment is supported in this version
#masterkey : the specific master key applied in the verification methods


## DID Create Operation

The instruction to create a new DID is issued via a POST HTTP request. 
```
POST /document/did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c   
HTTP/1.1
Host: virtualassets.id
Content-Type: application/ld+json, application/json, text/plain, */*
Accept-Encoding: gzip, deflate
{
    "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
    "operation": "create",
    "document": {
        "@context": [
            "https://www.w3.org/ns/did/v1",
            "https://w3c-ccg.github.io/ld-cryptosuite-registry/#ecdsasecp256k1signature2019"
        ],
        "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
        "verificationMethod": [
          {
            "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey",
            "type": "EcdsaSecp256k1VerificationKey2019",
            "controller": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
            "publicKeyMultibase": "fef2823c7d237bd094d633a1765d5896b0f442481a997da2f83d7a928ddce7e65",
            "blockchainAccountId":"enq:f045c5c7d50145b65ca2702c38b4e2d46658293c"
          }
        ],
        "authentication": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "assertionMethod": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "service": [
          {
	    "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#service",
    	    "type": "LinkedDomains",
    	    "serviceEndpoint": "https://virtualassets.id"
          }
        ]
    }
}
```


## DID Read Operation (Resolve)

The instruction to read a DID is issued via a GET HTTP request. 

https://virtualassets.id/{method-specific-subject-id}

Example :

[https://virtualassets.id/f045c5c7d50145b65ca2702c38b4e2d46658293c](https://did.artrac.id/f045c5c7d50145b65ca2702c38b4e2d46658293c)

```
GET /document/did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c   
HTTP/1.1
Host: virtualassets.id
Content-Type: application/ld+json, application/ld+json, application/json, text/plain, 
Accept-Encoding: gzip, deflate
```

Response from the service endpoint did.artrac.id
```
{
    "responseCode": 0,
    "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
    "document": {
        "@context": [
            "https://www.w3.org/ns/did/v1",
            "https://w3c-ccg.github.io/ld-cryptosuite-registry/#ecdsasecp256k1signature2019"
        ],
        "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
        "verificationMethod": [
          {
            "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey",
            "type": "EcdsaSecp256k1VerificationKey2019",
            "controller": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
            "publicKeyMultibase": "fef2823c7d237bd094d633a1765d5896b0f442481a997da2f83d7a928ddce7e65",
            "blockchainAccountId":"enq:f045c5c7d50145b65ca2702c38b4e2d46658293c"
          }
        ],
        "authentication": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "assertionMethod": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "service": [
          {
	    "id": "did:art:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#service",
    	    "type": "LinkedDomains",
    	    "serviceEndpoint": "https://virtualassets.id"
          }
        ]
    }
}
```


## DID Update Operation

The instruction to update a DID is issued via a PUT HTTP request. 
```
PUT /document/did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c   
HTTP/1.1
Host: virtualassets.id
Content-Type: application/ld+json, application/json, text/plain
Accept-Encoding: gzip, deflate
{
    "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
    "operation": "update",
    "document": {
        "@context": [
            "https://www.w3.org/ns/did/v1",
            "https://w3c-ccg.github.io/ld-cryptosuite-registry/#ecdsasecp256k1signature2019"
        ],
        "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
        "verificationMethod": [
          {
            "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey",
            "type": "EcdsaSecp256k1VerificationKey2019",
            "controller": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c",
            "publicKeyMultibase": "fef2823c7d237bd094d633a1765d5896b0f442481a997da2f83d7a928ddce7e65",
            "blockchainAccountId":"enq:f045c5c7d50145b65ca2702c38b4e2d46658293c"
          }
        ],
        "authentication": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "assertionMethod": [
          "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#masterkey"
        ],
        "service": [
          {
	    "id": "did:rm:enq:f045c5c7d50145b65ca2702c38b4e2d46658293c#service",
    	    "type": "LinkedDomains",
    	    "serviceEndpoint": "https://virtualassets.id"
          }
        ]
    }
}
```


## DID Delete Operation

The instruction to delete a DID is issued via a DELETE HTTP request. 

DELETE https://virtualassets.id/f045c5c7d50145b65ca2702c38b4e2d46658293c


## Security Considerations


The DID:RM method never exposes the private key. The user can however use and display the DID's private key locally on the highly secured security key tag hardware.

In the RealMatter DID system, all users' private data is stored on the highly secured security key tag hardware. Only the hash value or strings generated by crypt algorithms of the data are public on-chain, the attackers cannot derive the private data with the hash value or strings.

All data stored in DID documents is considered public. DID documents do not contain any personal information about the user concerned.

**Attacks**

To prevent an attack, a did proof has to go through the signature verification against the verifier’s challenge. The signature is processed inside the highly secured security key tag hardware.


## Privacy Considerations

The RealMatter DID blockchain and DID Documents contain no PII (Personally-Identifiable Information).

Private data in RealMatter is encrypted and signed using the private key which corresponds to the public key in the DID. This ensures that no message insertion or modification is possible and authenticity of the DID Documents is ensured. 

The RealMatter DID system prevents forgery and tampering through hash value checking.

Private keys(for signing operations) are to be held on highly secured security key tag hardware.

