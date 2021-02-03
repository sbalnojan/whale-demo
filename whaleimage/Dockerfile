FROM rust:1.49 AS rust_base
RUN git clone https://github.com/dataframehq/whale.git
RUN apt-get -y update
RUN cd whale && make
RUN apt-get -y install unixodbc-dev

FROM python:3.7
RUN apt-get -y update
RUN apt-get -y install unixodbc-dev
RUN git clone https://github.com/dataframehq/whale.git
RUN mkdir ~/.whale && mkdir ~/.whale/bin
COPY --from=rust_base /whale/cli/target/ /whale/cli/target/
RUN cd whale && make python
RUN cp /whale/cli/target/release/whale ~/.whale/bin
