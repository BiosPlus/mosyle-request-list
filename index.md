---
layout: default
title: Tickets
has_children: true
has_toc: true
---


{% assign all = site.tickets | sort: "ticket_number" %}
{% assign default = "" | split: ',' %}
{% assign success = "" | split: ',' %}
{% assign all = site.docs.tickets | sort: "ticket_number" %}
{% for ticket in all %}
        {% if ticket.status contains "Success" %}
            {% assign success = success | push: ticket %}
        {% elsif ticket.status contains "Progress" %}
            {% assign progress = progress | push: ticket %}
        {% elsif ticket.status contains "Limbo" %}
            {% assign limbo = limbo | push: ticket %}
        {% elseif ticket.status contains "Failed" %}
            {% assign failed = failed | push: ticket %}
        {% elsif ticket.status contains "Pending" %}
            {% assign pending = pending | push: ticket %}
        {% else %}
            {% assign default = default | push: ticket %}
        {% endif %}
{% endfor %}


## ✅ Successful Requests ##
Successful requests from the community.
<table>
	<thead>
		<tr>
			<th>Ticket Number</th>
			<th>Title</th>
			<!-- <th>Summary</th> -->
			<th>Submitted On</th>
		</tr>
	</thead>
	<tbody>
		{% for ticket in success %}
			<tr>
				<td markdown="span">{{ ticket.ticket_number }}</td>
				<td markdown="span">{{ ticket.ticket_title }}</td>
				<td markdown="span">{{ status }}</td>
			</tr>
		{% endfor %}
	</tbody>
</table>


## 🏃 In Progress Requests ##
Requests that are currently in progress, meaning the Mosyle team is working on it and are giving frequent updates
<table>
    <thead>
        <tr>
            <th>Ticket Number</th>
            <th>Title</th>
            <!-- <th>Summary</th> -->
            <th>Submitted On</th>
        </tr>
    </thead>
    <tbody>
        {% for ticket in progress %}
            <tr>
                <td markdown="span">{{ ticket.ticket_number }}</td>
                <td markdown="span">{{ ticket.ticket_title }}</td>
                <td markdown="span">{{ status }}</td>
            </tr>
        {% endfor %}
    </tbody>
</table>


## ⌛️ Pending Requests ##
Requests that are pending. These have just been submitted and lack a response, bug the author to update the ticket when more info comes through.
<table>
    <thead>
        <tr>
            <th>Ticket Number</th>
            <th>Title</th>
            <!-- <th>Summary</th> -->
            <th>Submitted On</th>
        </tr>
    </thead>
    <tbody>
        {% for ticket in pending %}
            <tr>
                <td markdown="span">{{ ticket.ticket_number }}</td>
                <td markdown="span">{{ ticket.ticket_title }}</td>
                <td markdown="span">{{ status }}</td>
            </tr>
        {% endfor %}
    </tbody>
</table>


## ❌ Failed Requests ##
Requests that have failed. They have been outright denied action.
<table>
    <thead>
        <tr>
            <th>Ticket Number</th>
            <th>Title</th>
            <!-- <th>Summary</th> -->
            <th>Submitted On</th>
        </tr>
    </thead>
    <tbody>
        {% for ticket in failed %}
            <tr>
                <td markdown="span">{{ ticket.ticket_number }}</td>
                <td markdown="span">{{ ticket.ticket_title }}</td>
                <td markdown="span">{{ status }}</td>
            </tr>
        {% endfor %}
    </tbody>
</table>


## 🌀 Limbo Requests ##
Requests that are in limbo. Unlikely to be updated as Mosyle haven't given a proper response to the matter and it's ended up closed.
<table>
    <thead>
        <tr>
            <th>Ticket Number</th>
            <th>Title</th>
            <!-- <th>Summary</th> -->
            <th>Submitted On</th>
        </tr>
    </thead>
    <tbody>
        {% for ticket in limbo %}
            <tr>
                <td markdown="span">{{ ticket.ticket_number }}</td>
                <td markdown="span">{{ ticket.ticket_title }}</td>
                <td markdown="span">{{ status }}</td>
            </tr>
        {% endfor %}
    </tbody>
</table>