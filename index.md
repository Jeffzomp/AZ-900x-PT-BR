---
title: Instruções online hospedadas
permalink: index.html
layout: home
---

# <a name="content-directory"></a>Diretório de conteúdo

Hyperlinks to each of the walkthroughs. Instructors may choose to use the walkthrough as a demonstration or a student lab. 

## <a name="walkthroughs"></a>Passo a passo

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Módulo | Passo a passo |
| --- | --- | 
{% para atividade no wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

