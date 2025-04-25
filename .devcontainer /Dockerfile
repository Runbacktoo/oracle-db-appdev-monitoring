# 使用 AlmaLinux 8 作为基础镜像
FROM almalinux:8

# 安装 glibc 2.17 和基础开发工具
RUN yum -y update && \
    yum -y groupinstall "Development Tools" && \
    yum -y install glibc wget tar sudo && \
    yum clean all

# 设置默认用户
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# 创建用户并设置权限
RUN groupadd --gid $USER_GID $USERNAME && \
    useradd --uid $USER_UID --gid $USER_GID -m $USERNAME && \
    echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# 切换到 vscode 用户
USER $USERNAME

# 设置默认工作目录
WORKDIR /workspace
