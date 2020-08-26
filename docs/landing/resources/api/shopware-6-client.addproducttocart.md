<!-- Do not edit this file. It is automatically generated by API Documenter. -->

[Home](./index.md) &gt; [@shopware-pwa/shopware-6-client](./shopware-6-client.md) &gt; [addProductToCart](./shopware-6-client.addproducttocart.md)

## addProductToCart() function

> This API is provided as a preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.
> 

Adds specific quantity of the product to the cart by productId. It creates a new cart line item.

Warning: This method does not change the state of the cart in any way if productId already exists in a cart. For changing the quantity use addQuantityToCartLineItem() or changeCartLineItemQuantity() methods.

<b>Signature:</b>

```typescript
export declare function addProductToCart(productId: string, quantity?: number, contextInstance?: ShopwareApiInstance): Promise<Cart>;
```

## Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  productId | string |  |
|  quantity | number |  |
|  contextInstance | [ShopwareApiInstance](./shopware-6-client.shopwareapiinstance.md) |  |

<b>Returns:</b>

Promise&lt;Cart&gt;

## Exceptions

ClientApiError
