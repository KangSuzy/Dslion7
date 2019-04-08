# Dslion7-Django 

;파이썬으로 만들어진 무료 오픈소스 웹 애플리케이션 프레임워크    

## 시작하기    
-------------
1. 작업 디렉토리 생성    
2. 가상환경 생성 및 실행 
;$ python –m venv (myvenv)
;$ source (myvenv)/Scripts/activate <-> deactivate
3. 장고 설치    
;$ pip install django
4. 프로젝트 생성    
;$ django-admin startproject (firstproject)    
5. app 만들기    
;$ python manage.py startapp (myapp)    
;settings.py/INSTALLED_APPS[    
		‘appname.apps.AppnameConfig’    
						]    
;$ python manage.py runserver <-> ctrl+C    
6. templates 만들기    
;(myapp)/templates/(home).html    
7. view 함수 만들기
;def home(request):    
	return render(request, ‘home.html’)    
8. url 작성하기
;urls.py import myapp.views //작성해놓은 함수를 사용하기 위해    
;urlpatterns = [...    
			path(‘’, myapp.views.home, name=’home’),
			...	]    

## template extending / inheritance    

;중복되는 코드를 한꺼번에 관리하는 방법    

1) templates/base.html 생성 //공통되는 내용    
	{% block content %}    
	{% endblock %}     // 개별적 내용 표시 태그    
2) 확장을 위해 {% extends ‘base.html’ %} 선언    

## static files    
-------------
;웹사이트의 고정된 파일들 ex) CSS JS Image ...    

1) settings.py/ INSTALL_APPS[..., ‘django.contrib.staticfiles’, ...] 확인    
2) settings.py/ STATIC_URL = ‘/static/’ 확인    
3) settings.py/ STATICFILES_DIRS=(os.path.join(BASE_DIR,'static'),)    
	STATIC_ROOT=os.path.join(BASE_DIR,'staticfiles') 내용 추가    
4) static file 생성 후 css, javascript, image ... 넣기    
5) 사용하고자 하는 html 상단에 {% load static %} / {% load staticfiles %} 작성    
6) src 속성에 {% %} 이용하여 경로 지정

## MTV    
-------------
- models.py     
 데이터 테이블을 정의        
- views.py      
 app의 제어 흐름 및 처리 로직 정의    
- templates/*.html     
 사용자에게 보여줄 화면 정의    
