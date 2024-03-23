# CSS Issues 

그림이 중앙에 들어가지 않으며
justify-content-center -> align-items-center

# 새로운 page를 추가하고 싶을 때

* layout 에 template page 를 추가
* content 에 새로운 page 를 추가 (layout을 지정해줘야 함)

# 내용을 markdown 형식을 작성하고 싶을 때

* Template 에 markdownify 필터를 사용하여 markdown 형식으로 변환
{{ . | markdownify }}
