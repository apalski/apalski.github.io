---
layout: post
title:      "Frontend action with Ajax + JSON API "
date:       2018-05-05 11:43:20 +0000
permalink:  frontend_action_with_ajax_json_api
---


Take a previous project and change the front end from rails to a Json API. Sounds simple enough but oh what a steep learning curve it turned out to be.

You've powered through the lessons and labs and feeling fairly confident and then you start. Suddenly nothing is working the way you think it should. The slightest tweek can make everything work or break everything and you can't really see why.

Once again it was a case of going back over everything and trying to gain a deeper understanding of the material the second time around. 

The basic goals were to render an index view and a show view using jQuery with an Active Model Serialisation. In addition you had to create a new resource from a form and render the response without a refresh. I began with a very simple goal in mind, do just one of each of the requirements. I ended up rendering all index and show views using JQuery and in addition managed to get them all rendering to the same page, the user's show page and had each show view with a next and previous button.

As I investigated and googled my way through the project I found numerous ways to tackle the problem. Each time I found a solution I came back to the project requirements and used them to decide the path I would take. 

My project contains constructor functions to translate a JSON response into a js model object:

```function Movement(adminmovement) {
	this.id = adminmovement.id;
	this.name = adminmovement.name;
	this.movement_type = adminmovement.movement_type;
	this.quantity = adminmovement.quantity;
};```

It uses prototype templates to construct the HTML for the page:

```Movement.prototype.adminIndexTemplate = function() {
	let adminmovementHtml = `
	<li> ${this.id} </li><br>
	<li class="adminmovementName">Movement: ${this.name}</li><br>
	<li class="adminmovementType">Movement Type: ${this.movement_type}</li><br>
	<li class="adminmovementQuantity">Quantity: ${this.quantity}</li><br>
	<div class="">
		<a href="/admin/movements/${this.id}/edit" data-id="${this.id} class="show_link">Edit/Delete Movement</a>
	</div>
	<h3>_____________________________________</h3>
		`;
	return adminmovementHtml;
};```

It then uses the constructor functions and the prototype templates to render the HTML result to the page:

```function renderAdminMovements(adminmovements) {
  adminmovements.forEach(adminmovement => {
    let newAdminMovement = new Movement(adminmovement);
    let adminmovementHtml = newAdminMovement.adminIndexTemplate();
    $('.crossfit-container').append(adminmovementHtml);
  });
};```

While the project took a lot longer than I anticipated it would, I went from hating Javascript to having a grudging respect for the language. I can now say, while I am not proficient at Javascript, I have a really good grasp of Javascript and am confident that I can build on my knowledge.




