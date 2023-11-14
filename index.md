---
---
<script src="assets/js/sorttable.js"></script>
<script src="assets/js/collapsible.js"></script>

<details open>
<summary>
Why does this exist?
</summary>

This is a list of commonly requested features/bugs being made by administrators to the Mosyle support team.
Currently there is no publicly accessible roadmap available for requests, and tickets that are being logged are forwarded to a mysterious product team though never heard from again until maybe a release is made in their monthly updates.

By having a public list of requests, we hope to provide greater transparency on issues and features that have been raised by administrators like you, and maybe inspire the creation of an official public tracker.
</details>

{% assign all = site.tickets | sort: "ticket_number" %}
{% assign default = "" | split: ',' %}
{% assign success = "" | split: ',' %}
{% for ticket in all %}
	{% if ticket.status contains "completed" %}
		{% assign success = success | push: ticket %}
	{% else %}
		{% assign default = default | push: ticket %}
	{% endif %}
{% endfor %}

## ⚠️ Current Requests ##
Current common requests from the community.
<table class="sortable">
	<thead>
		<tr>
			<th>Ticket Number</th>
			<th>Title</th>
			<th>Short Summary</th>
		</tr>
	</thead>
	<tbody>
		{% for ticket in default %}
		<button class="collapsible">
			<tr>
				<td markdown="span"><a href="{{ ticket.relevant_thread }}">{{ ticket.ticket_number }}</a></td>
				<td markdown="span">{{ ticket.title }}</td>
				<td class="table-summary" markdown="span" title="{{ ticket.summary }}">Short summary dummy</td>
			</tr>
		</button>
			<div class="content">
				<div class="inner-content-summary">
					<div class="info-row">{{ ticket.summary }}</div>
					<div class="info-row">
						<div class="info-col">Submitted: {{ ticket.submitted_on }}</div>
						<div class="info-col">By: {{ ticket.submitted_by }}</div>
						<div class="info-col">Last Update: {{ ticket.last_update }}</div>
					</div>
				</div>
			</div> 
		{% endfor %}
	</tbody>

</table>

## ✅ Success Stories ##
Some tickets have already been actioned, kudos Mosyle!

<table class="sortable">
	<thead>
		<tr>
			<th>Ticket Number</th>
			<th>Title</th>
			<!-- <th>Summary</th> -->
			<th>Last Updated</th>
			<th>Submitted by</th>
			<th>Relevant Thread</th>
		</tr>
	</thead>
	<tbody>
		{% for ticket in success %}
		<tr>
			<td markdown="span">{{ ticket.ticket_number }}</td>
			<td markdown="span">[{{ ticket.title }}](## {{ ticket.summary }})</td>
			<!-- <td markdown="span">{{ ticket.summary }}</td> -->
			<td markdown="span">{{ ticket.last_update }}</td>
			<td markdown="span"><a href="{{ ticket.submitted_by_link }}">{{ ticket.submitted_by }}</a></td>
			<td markdown="span"><a href="{{ ticket.relevant_thread }}">Link</a></td>
		</tr>
		{% endfor %}
	</tbody>
</table>

## FAQs

<details>
<summary>
How do I contribute my support request to this page?
</summary>
Easy, pop on over to the github repo listed below and open either an issue or a pull request with the required information. 
</details>

## Thanks:

Thanks to robchahin who published sso.tax, whose site/repo served as a good foundation for this github