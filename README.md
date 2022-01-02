# Search-Bar

def index(request):
    queryset = article.objects.all()
    number_of_records = article.objects.count()
    random_page = random.randint(1,number_of_records)
    context = {
        "object_list": queryset,
        "random_page": random_page
    }

#    query = ""
#    if request.GET:
#        query = request.GET['q']
#        context['query'] = str(query)


    entries = util.list_entries()
    return render(request, "encyclopedia/index.html", context)
    #{
        #"entries": util.list_entries(),
        #"random_page": random_page,
    #})
def dynamic_articles_view(request, my_id):
    obj = article.objects.get(id= my_id)
    number_of_records = article.objects.count()
    random_page = random.randint(1,number_of_records)
    context = {
        "object": obj,
        "random_page": random_page
    }
    return render(request, "encyclopedia/article_detail.html", context)
