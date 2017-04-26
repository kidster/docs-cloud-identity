.. _get-a-domain-v2.0-rax-auth:

Get a domain
~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/domains/{domainId}

Use this operation to get detailed information about a specified domain.

.. note::

   This API operation is implemented through the
   :ref:`RAX-AUTH extension <extensions-ovw>`  to the core Identity API.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The request was valid,   |
|                          |                         |but the server is        |
|                          |                         |refusing to respond      |
|                          |                         |because you do not have  |
|                          |                         |permission to access the |
|                          |                         |requested resource.      |
|                          |                         |Submit a request to your |
|                          |                         |account administrator to |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
+--------------------------+-------------------------+-------------------------+
|405                       |Invalid Method           |The method specified in  |
|                          |                         |the request is not valid |
|                          |                         |for the resource         |
|                          |                         |identified in the        |
|                          |                         |request URI.             |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{domainId}                |URI                      |A domain ID.             |
|                          |String *(Required)*      |                         |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example: Get a domain HTTP request header XML**


.. code::

   GET /v2.0/RAX-AUTH/domain/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: c6f56a1d89274da4b14c1de36c412345


**Example: Get a domain HTTP request header: JSON**


.. code::

   GET /v2.0/RAX-AUTH/domain/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: c6f56a1d89274da4b14c1de36c412345


Response
--------

This table shows the body parameters for the response:

+-------------------------------------+---------------------+---------------------+
|Name                                 |Type                 |Description          |
+=====================================+=====================+=====================+
|RAX-AUTH:domain                      |Object               |An object that       |
|                                     |                     |contains the domain  |
|                                     |                     |configuration        |
|                                     |                     |attribute settings.  |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\ **id**             |String               |The unique id for    |
|                                     |                     |the domain.          |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\ **enabled**        |Boolean              |Indicates whether    |
|                                     |                     |the domain is        |
|                                     |                     |enabled.             |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\ **description**    |String               |The domain           |
|                                     |                     |description.         |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\ **name**           |String               |The domain name.     |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\                    |String *(Optional)*  |The Rackspace        |
|**rackspaceCustomerNumber**          |                     |customer number.     |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\                    |String               |If present, this     |
|**domainMultiFactorEnforcementLevel**|                     |extended attribute   |
|                                     |                     |specifies the multi- |
|                                     |                     |factor               |
|                                     |                     |authentication       |
|                                     |                     |enforcement policy   |
|                                     |                     |that applies to      |
|                                     |                     |accounts within the  |
|                                     |                     |specified domain. *  |
|                                     |                     |                     |
|                                     |                     |- ``REQUIRED``       |
|                                     |                     |   Users             |
|                                     |                     |   within the domain |
|                                     |                     |   must use multi-   |
|                                     |                     |   factor            |
|                                     |                     |   authentication to |
|                                     |                     |   access their      |
|                                     |                     |   account. *        |
|                                     |                     |                     |
|                                     |                     |- ``OPTIONAL``       |
|                                     |                     |   Users             |
|                                     |                     |   have the option to|
|                                     |                     |   authenticate using|
|                                     |                     |   multi-factor      |
|                                     |                     |   authentication.   |
+-------------------------------------+---------------------+---------------------+


**Example: Get domain response header XML**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml


**Example: Get domain response: XML**

.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <rax-auth:domain
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0"
        id="123456" name="GCorp" enabled="true" rackspaceCustomerNumber="RCN-123-123-123" domainMultiFactorEnforcementLevel="OPTIONAL">
            <rax-auth:description>A very good customer</rax-auth:description>
    </rax-auth:domain>



**Example: Get domain response header JSON**

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json


**Example: Get domain response: JSON**

.. code::

    {
        "RAX-AUTH:domain": {
            "id": "123456",
            "enabled": true,
            "description": "A very good customer",
            "name": "GCorp",
            "rackspaceCustomerNumber": "RCN-123-123-123",
            "domainMultiFactorEnforcementLevel": "OPTIONAL"
        }
    }
