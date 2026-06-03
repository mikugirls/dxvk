FROM foundationubuntu2204

# 升级 Meson 到 1.0 以上
RUN apt-get update && apt-get install -y python3-pip && \
    pip3 install --upgrade meson

RUN rm -rf /opt/dxvk; mkdir -p /opt/dxvk/output
COPY ./ /opt/dxvk/
RUN ls -la /opt/dxvk/
ENV PATH="/opt/bylaws-llvm-mingw-20240929-ucrt-ubuntu-20.04-x86_64/bin:$PATH"

# 接收构建参数（版本号）
ARG DXVK_VERSION

# 使用传入的版本号进行打包，不再依赖 git describe
RUN cd /opt/dxvk; ./package-release.sh ${DXVK_VERSION} /opt/dxvk/output
