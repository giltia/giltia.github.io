---
title:
date: 2024-01-01
type: landing

sections:
  - block: hero
    content:
      title: |
        Grupo de Investigación
        Voz Maya
      image:
        filename: welcome.jpg
      text: |
        <br>

        El **Grupo de Investigación Voz Maya** de [CentroGeo](https://www.centrogeo.org.mx) desarrolla tecnología de procesamiento de lenguaje natural para la **lengua maya yucateca**, contribuyendo a su preservación y difusión digital.

  - block: collection
    content:
      title: Últimas Noticias
      subtitle:
      text:
      count: 5
      filters:
        author: ''
        category: ''
        exclude_featured: false
        publication_type: ''
        tag: ''
      offset: 0
      order: desc
      page_type: post
    design:
      view: card
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image:
          filename: coders.jpg
          filters:
            brightness: 0.7
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen

  - block: collection
    content:
      title: Últimas Publicaciones
      text: ""
      count: 5
      filters:
        folders:
          - publication
        publication_type: 'article'
    design:
      view: citation
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Conoce al equipo →" %}}
    design:
      columns: '1'
---
