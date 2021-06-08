ARG BUILD_FROM
FROM $BUILD_FROM
WORKDIR /app
COPY . /app
RUN chmod +x addon_deps.sh
RUN ./addon_deps.sh
RUN pip3 install .
COPY config.json /usr/local/lib/python3.8/site-packages/config.json

RUN git clone -b v2 https://github.com/andrea-mattioli/bticino_X8000_rest_api.git \
&& mv bticino_X8000_rest_api/* /app/ \
&& rm -rf bticino_X8000_rest_api;

COPY run.sh /app/

RUN chmod +x /app/run.sh

RUN pip3 install -r requirements.txt

EXPOSE 5588

CMD [ "/app/run.sh" ]

#ENTRYPOINT ["python3", "-m", "backup"]
