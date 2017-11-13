# printer-integration-doc

#### Required information from client
* Development API URL/Endpoint
* Production API URL/Endpoint
* Additional parameters if any
* Sample success response
* Sample error response
* Sample xml schema(with required fields highlighted)

#### Cxml schema we are currently using
```xml
<?xml version="1.0"?>
<cXML version="1.2.028" timestamp="ISO_8601_timestamp" payloadID="unique_identifier">
  <Header>
            <From>
                <Credential domain="DUNS">
                    <Identity>PICA9</Identity>
                </Credential>
            </From>
            <To>
                <Credential domain="DUNS">
                    <Identity>Your Identity</Identity>
                </Credential>
            </To>
            <Sender>
                <Credential domain="DUNS">
                    <Identity>PICA9</Identity>
                    <SharedSecret>Shared Secret</SharedSecret>
                </Credential>
                <UserAgent>User Agent</UserAgent>
            </Sender></Header>
  <Request deploymentMode="test">
    <OrderRequest>
      <OrderRequestHeader type="new" orderID="order_id" orderDate="order_date">
                <Total>
                    <Money currency="USD">total_cost</Money>
                </Total>
                <BillTo>
                    <Address addressID="billing_address_identifier">
                        <Name xml:lang="en">billing_address_name</Name>
                        <PostalAddress>
                            <Street>billing_address_address1</Street>
                            <Street>billing_address_address2</Street>
                            <City>billing_address_city</City>
                            <State>billing_address_state</State>
                            <PostalCode>billing_address_zipcode</PostalCode>
                            <Country isoCountryCode="US"/>
                        </PostalAddress>
                    </Address>
                </BillTo>
            </OrderRequestHeader>
      <ItemOut quantity="item_quantity" lineNumber="1">
                <ItemID>
                    <SupplierPartID>sku</SupplierPartID>
                </ItemID>
            <ItemDetail>
                <UnitPrice>
                    <Money currency="USD">item_price</Money>
                </UnitPrice>
                <Description xml:lang="en">item_description</Description>
                <UnitOfMeasure>EA</UnitOfMeasure>
                <Classification domain=""/>
                <ManufacturePartID>sku</ManufacturePartID>
                <Extrinsic name="Asset Filename">item_filename</Extrinsic>
                <Extrinsic name="Asset URL">s3_signed_url</Extrinsic>
            </ItemDetail>
            <ShipTo isoCountryCode="US">
                <Address>
                    <Name xml:lang="en">shipping_address_name</Name>
                    <PostalAddress>
                        <Street>shipping_address_address1</Street>
                        <Street>shipping_address_address2</Street>
                        <City>shipping_address_city</City>
                        <State>shipping_address_state</State>
                        <PostalCode>shipping_address_zipcode</PostalCode>
                        <Country isoCountryCode="US"/>
                    </PostalAddress>
                </Address>
            </ShipTo>
        </ItemOut>
    </OrderRequest>
  </Request>
</cXML>
```
