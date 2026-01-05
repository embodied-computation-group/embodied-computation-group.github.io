---
title: People
permalink: /people/
---

### Lab Members

The Embodied Computation Group is a multidisciplinary team bringing together expertise in computational modelling, psychophysics, neuroimaging, and clinical research. We are united by our interest in understanding how visceral and embodied processes shape cognition, emotion, and perception.

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_array = "pi|postdoc|gradstudent|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if role == 'postdoc' %}
<h3>Postdoctoral Researchers</h3>
 {% elsif role == 'pi' %}
<h3>Principal Investigator</h3>
 {% elsif role == 'gradstudent' %}
<h3>PhD Students</h3>
 {% elsif role == 'researchstaff' %}
<h3>Research Staff</h3>
 {% elsif role == 'visiting' %}
<h3>Visiting Scholars</h3>
 {% elsif role == 'others' %}
<h3>Collaborators</h3>
 {% elsif role == 'alumni' %}
<h3>Alumni</h3>
{% endif %}
</div>

{% if role != 'alumni' %}
<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          {% if profile.avatar %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="https://via.placeholder.com/200x200?text=No+Photo"></a>
          {% endif %}
          <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
        </p>
      </div>
    {% endif %}
  {% endfor %}
</div>
<hr>

{% else %}

<table>
  <thead>
    <tr>
      <th>Who are they</th>
      <th>When were they here</th>
      <th>Where they went</th>
    </tr>
  </thead>
  <tbody>
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
    <tr>
      <td><a href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a></td>
      <td>{{ profile.role }} ({{ profile.joined }})</td>
      <td>{{ profile.current }}</td>
    </tr>
    {% endif %}
  {% endfor %}
  </tbody>
</table>

{% endif %}
{% endfor %}
