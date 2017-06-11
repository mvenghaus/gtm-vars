# Google Remarketing - Tag Params

## Name
Google Remarketing - Tag Params

## Type
Custom Javascript

## Dependencies
Variable "Page Type" must exist

## Code
	function() {

		var googleTagParams = {
			ecomm_pagetype: "{{Page Type}}"
		}

		var ecommerce = {{Ecommerce}};
		if (typeof ecommerce === 'undefined') {
			return googleTagParams;
		}

		if (ecommerce.hasOwnProperty('purchase')) {
			googleTagParams.ecomm_prodid = [];
			for (var i=0; i<ecommerce.purchase.products.length; i++) {
	  			googleTagParams.ecomm_prodid.push(ecommerce.purchase.products[i].id);
			}

			googleTagParams.ecomm_totalvalue = ecommerce.purchase.actionField.revenue;
		}

		return googleTagParams;
	}