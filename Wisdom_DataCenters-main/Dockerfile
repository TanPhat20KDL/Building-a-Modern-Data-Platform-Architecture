FROM bitnami/spark:3.4.0

USER root
# Cài đặt pyspark và pyyaml
RUN pip install pyyaml mysql-connector-python

RUN mkdir -p /app/logs && chmod -R 777 /app/logs


# Sao chép nội dung dự án vào container
COPY . /app

# Thiết lập thư mục làm việc
WORKDIR /app

COPY src/batch_etl/jars/mysql-connector-java-8.0.28.jar /opt/bitnami/spark/jars/

## Tạo thư mục logs và thay đổi quyền
#RUN mkdir -p /app/logs && chmod -R 777 /app/logs

CMD ["spark-submit", "--master", "spark://spark-master:7077", "src/batch_etl/main.py"]

USER 1001