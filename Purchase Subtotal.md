# Purchase Subtotal

## Name
Purchase Subtotal

## Type
Custom Javascript

## Code
    function () {
        var ecommerce = {{Ecommerce}};

        if (typeof ecommerce !== 'undefined') {
            if (ecommerce.hasOwnProperty('purchase')) {
                return Math.round((ecommerce.purchase.actionField.revenue - ecommerce.purchase.actionField.tax - ecommerce.purchase.actionField.shipping) * 100) / 100;
            }
        }
    }
