FROM python:3.7.2

WORKDIR /python_aiplatform
COPY . .

#安装或者升级pip
RUN pip install -U pip
#一劳永逸配置pip源，永远设置pip下载源为国内源
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

#安装依赖的库等
RUN pip install -r /python_aiplatform/aiplatform/requirements.txt
EXPOSE 1234

#无需pip install gunicorn，因为已经在requirements的文件中安装了
#gunicorn的配置文件gunicorn_conf.py就是下面这个路径的地方
CMD cd aiplatform & gunicorn -c /python_aiplatform/aiplatform/aiplatform/gunicorn_conf.py aiplatform.wsgi:application