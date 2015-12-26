---
layout: default
---

{% include page.html %}

---

### pagination

{% for post in paginator.posts %}
*   <p>`{{ post.path }}`              =>    [{{ post.url }}]({{ post.url }})</p>
{% endfor %}

<nav>
    <ul class="pagination">
        {% if paginator.previous_page %}
        <li>
        <a href="{{ paginator.previous_page_path }}" aria-label="Previous">
            <span>Previous</span>
        </a>
        </li>
        {% else %}
        <li class='disabled'>
        <a>
            <span>Previous</span>
        </a>
        </li>
        {% endif %}
        {% for page in (1..paginator.total_pages) %}
        {% if page == paginator.page %}
        <li class='active'><a>{{ page }}</a></li>
        {% elsif page == 1 %}
        <li>
        <a href="{{ paginator.paginate_path | prepend: site.baseurl | replace: '//', '/' }}">{{ page }}</a>
        </li>
        {% else %}
        <li>
        <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
        </li>
        {% endif %}
        {% endfor %}
        {% if paginator.next_page %}
        <li>
        <a href="{{ paginator.next_page_path }}" aria-label="Next">
            <span>Next</span>
        </a>
        </li>
        {% else %}
        <li class='disabled'>
        <a>
            <span>Next</span>
        </a>
        </li>
        {% endif %}
    </ul>
</nav>
