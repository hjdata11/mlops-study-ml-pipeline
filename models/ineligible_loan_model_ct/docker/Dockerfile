FROM python:3.9-slim
LABEL maintainer="mlops.study@gmail.com"

ARG USER_HOME=/home/hj
ARG SUPPORT_SOURCE_PATH=support
ARG PREPARATION_SOURCE_PATH=models/ineligible_loan_model_ct/data_preparation
ARG MODEL_SOURCE_PATH=models/ineligible_loan_model_ct/model
ARG REQUIREMENTS_PATH=models/ineligible_loan_model_ct/docker

RUN groupadd --gid 1000 hj \
    && useradd --uid 1000 --gid hj --shell /bin/bash --create-home hj

COPY --chown=hj:hj ${SUPPORT_SOURCE_PATH}/ ${USER_HOME}/support/
COPY --chown=hj:hj ${PREPARATION_SOURCE_PATH}/preparation.py \
     ${USER_HOME}/data_preparation/
COPY --chown=hj:hj ${MODEL_SOURCE_PATH}/training.py ${USER_HOME}/model/
COPY --chown=hj:hj ${REQUIREMENTS_PATH}/requirements.txt ${USER_HOME}/

USER hj

RUN mkdir -p ${USER_HOME}/mlops_data_store \
    && pip install --no-cache-dir -r ${USER_HOME}/requirements.txt

WORKDIR ${USER_HOME}