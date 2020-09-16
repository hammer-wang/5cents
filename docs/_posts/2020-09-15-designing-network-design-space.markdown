---
layout: posts
title:  "Desining Network Design Space."
date:   2020-09-15 17:44:12 -0400
categories: representation-learning
katex: yes
---
<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/ -->

This paper introduces a method for designing the design space of deep neural networks. The core idea is to sample network designs from a design space and analyze the quality of the design space using error empirical density function. A good design space would lead to designs with a high concentration of good models. The authors start with a simple, yet generic architecture template based on the standard residual bottleneck block as the unconstrained design space. Through a set of extensive experiments, the authors successfully discovered four ways to constrain the design space to a high-quality region. Specifically, the authors set all residual blocks to share the same bottleneck ratio and group width. In addition, the authors enforce the stage depths to be non-decreasing and the stage widths to follow a quantized linear relationship with respect to the block index. Overall, the authors managed to reduce the design space size from $$O(10^{18})$$ to $O(10^8)$. Through experiments, the authors found the design space leads to a good performance across a range of flop regimes. With the refined search space, the authors managed to discover a network architecture with similar performance as EfficientNet trained with the same procedure but is up to 5 times faster on GPUs.

__Strengths__
Overall this paper proposes a simple and effective method that can construct a high-quality design space for searching neural network architectures. Compared to neural architecture search (NAS), which can only discover a single network instance for a specific task, the design space design method generalizes to different training regimes and can provide us more insights about the general design principles for neural networks. The findings from the discovered design space may help us better understand neural network architectures. In terms of writing, this paper has a really nice organization, and the authors deliver the key messages precisely. The extensive experiment performed by the authors is also very impressive. I think the idea of designing network design space can be extended to many other application domains, such as NLP and RL.

__Shortcomings__
From Table 4, we observe that the top-1 error of RegNetY is higher than EfficientNet trained with enhanced training schedules. It’s not clear how would the RegNet design space choices affect the results of training-time enhancements. If the RegNet design space lead to a limited effect of training-time enhancement, the proposed method might be less practical unless we can come up with training-time enhancement methods effective for the RegNet model family. 

[paper link](https://arxiv.org/abs/2003.13678)