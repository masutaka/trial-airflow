## Apache Airflow とは

:airflow: https://airflow.apache.org/

ワークフローをスケジューリング、モニタリングするためのツール。ワークフローエンジンと呼ぶらしい。

他の代表的なワークフローエンジンには「[Digdag](https://www.digdag.io/)」「[Argo](https://argoproj.github.io/argo-workflows/)」「[Prefect](https://www.prefect.io/)」があるらしい。おお、Argo って [Argo CD](https://argoproj.github.io/cd/) の仲間なのね。

[以前 embulk を試した](https://github.com/masutaka/trial-embulk)こともあり、Digdag は昔から知っていたのだけど、データ基盤の文脈だと Airflow をよく目にする。気のせいかもしれない。

## Quick Start してみた

試すだけなら Docker を使うのがお手軽。

:airflow: https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html

### Initialise and Running Airflow

```
$ curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.4.3/docker-compose.yaml'
$ echo 'AIRFLOW_UID=50000' > .env # optional on macOS
$ docker compose up airflow-init
$ docker-compose up
```

### Running the CLI commands

```
$ docker-compose run airflow-worker airflow info
$ curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.4.3/airflow.sh'
$ chmod +x airflow.sh
$ ./airflow.sh info
$ ./airflow.sh bash
$ ./airflow.sh python
```

### Accessing the web interface

http://localhost:8080

user: airflow, password: airflow

### Cleaning up

```
# $ docker-compose down --volumes --remove-orphans
$ docker-compose down --volumes --rmi all
```
