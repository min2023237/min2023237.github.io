---
layout: post
title: "댓글 기능 만들기(with. utterances)"
date: 2024-02-18 20:25:20 +0900
description:  # Add post description (optional) # 구글에서 검색했을 때 나오는?
img:  # Add image post (optional)
fig-caption: #
tags: [Github, Pages, Blog, utterances, comment]
---
나는 GitHub Pages를 만들 때, [flexible-jekyll](https://jekyllthemes.io/theme/flexible-jekyll)이라는 테마를 적용했고, `Disqus`라는 댓글 플랫폼이 자동으로 적용되어 있었다. 그런데 이게 광고가 붙어있어서 블로그가 너무 지저분해 보였다.<br>


`Disqus`를 대신할 플랫폼을 찾던 중 `utterances`라는 앱이 눈에 띄었다. `Utterances`는 GitHub Issues를 활용하여 블로그나 웹사이트에 댓글 기능을 추가할 수 있는 경량의 댓글 시스템이다.<br><br>
 GitHub Pages에 `Utterances`를 적용하려면 다음 단계를 따르면 된다:

#### 1. Utterances GitHub App 설치:<br>
먼저 Utterances GitHub App을 설치해야 한다. [설치 페이지](https://github.com/apps/utterances)에 방문하여 Install 버튼을 클릭하면, 아래와 같은 설정 페이지가 나온다.<br>
`Only select repositories`에 체크하여, `Utterances`를 추가하고자 하는 GitHub repository를 선택한다. 이 repository에 댓글이 저장된다. <br>
repository를 선택하였으면, `Install` 버튼을 누른다.

#### 2. Utterances 설정
`Install`을 누르면 자동으로 설정 페이지로 넘어간다.<br> 
여기서 `repo` 부분에 나의 GitHub Username과 repository 이름을 아래와 같이 작성한다.<br>
{% highlight Bash %}
min2023237/min2023237.github.io
{% endhighlight %}

#### 3. `_config.yml` 파일 설정 추가
설정을 마치면, 맨 아래에 HTML `<script>` 태그가 제공된다. 이것을 참고하여 `_config.yml`을 아래와 같이 수정한다.
{% highlight YAML %}
# Disqus
# discus-identifier: # add your discus identifier

# utterances
comments:
  provider: "utterances"
  utterances:
    repo: "min2023237/min2023237.github.io"
    issue_term: "pathname"
    theme: "github-light"
{% endhighlight %}
쓰지 않는 discus는 주석처리하고, 그 밑에 utterances 설정을 넣어주었다. 

#### 4. 레이아웃 또는 포스트 템플릿 수정
visual studio code에서 disqus를 검색해보면, 이 theme에서 disqus를 어떻게 적용하고 있는지 파악할 수 있다. 
먼저 post.html에서 `{% include disqus.html %}`으로 disqus.html을 불러오고 있다. 그리고 disqus.html에는 `_config.yml`의 설정을 기반으로 조건부로 `disqus`를 불러오는 것을 알 수 있다.<br>


{% highlight HTML %}
<section class="comment-area">
  <div class="comment-wrapper">
    .{% if site.discus-identifier %}
    <div id="disqus_thread" class="article-comments"></div>
    <script>
      (function() {
          var d = document, s = d.createElement('script');
          s.src = '//{{ site.discus-identifier }}.disqus.com/embed.js';
          s.setAttribute('data-timestamp', +new Date());
          (d.head || d.body).appendChild(s);
      })();
    </script>
    <noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
    .{% endif %}
  </div>
</section> <!-- End Comment Area -->
{% endhighlight %}

이 코드를 아래와 같이 수정하면, `disqus`가 아닌 `Utterances`를 불러올 수 있다.
{% highlight HTML %}
<section class="comment-area">
  <div class="comment-wrapper">
    {% if site.comments.provider == "utterances" %}
      <script src="https://utteranc.es/client.js"
              repo="{{ site.comments.utterances.repo }}"
              issue-term="{{ site.comments.utterances.issue_term }}"
              theme="{{ site.comments.utterances.theme }}"
              crossorigin="{{ site.comments.utterances.crossorigin }}"
              async>
      </script>
      {% endif %}
  </div>
</section> <!-- End Comment Area -->
{% endhighlight %}

#### 5. 사이트 빌드 및 확인
변경 사항을 적용한 후, 사이트를 빌드하고 로컬에서 테스트하여 댓글 시스템이 올바르게 작동하는지 확인한다. 그 후, 변경사항을 GitHub에 푸시하여 GitHub Pages에 반영한다.