---
layout: default
title: "Genome Ark - Lista Gatunków"
---

<h1>Lista Gatunków w Kolekcji</h1>

<table class="species-table">
  <thead>
    <tr>
      <th>Zdjęcie</th>
      <th>Nazwa (ang.)</th>
      <th>Nazwa (łac.)</th>
      <th>Rodzina</th>
      <th>Rząd</th>
      <th>Zsekwencjonowane zasoby</th>
    </tr>
  </thead>
  <tbody>
    {% for species in site.species %}
<tr 
  {% assign has_bionano = false %}
  {% for data in species.samples %}
    {% if data.datatype contains "Bionano" %}
      {% assign has_bionano = true %}
    {% endif %}
  {% endfor %}
  class="species-row{% if has_bionano %} bionano-highlight{% endif %}">

      <td class="species-image">
        <a href="{{ species.url }}">
          <img src="{{ species.image }}" alt="{{ species.title }}" class="species-img">
        </a>
      </td>
      <td>{{ species.common_name }}</td>
      <td><i>{{ species.name }}</i></td>
      <td>{{ species.family.name }}</td>
      <td>{{ species.order.name }}</td>
      <td>
        {% assign count = species.samples | size %}
         <strong>{{ count }} {% if count == 1 %}zasób{% elsif count > 1 and count < 5 %}zasoby{% else %}zasobów{% endif %}:</strong>
        <ul>
          {% for data in species.samples %}
            <li>{{ data.datatype }}: {{ data.bases }}</li>
          {% endfor %}
        </ul>
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>

<footer>
  <p>Autor: Maja Domańska</p>
</footer>

