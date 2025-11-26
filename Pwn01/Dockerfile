# Sử dụng Ubuntu 24.04 (glibc 2.39)
FROM ubuntu:24.04

# Tránh các thông báo nhắc lệnh (interactive) khi cài phần mềm
ENV DEBIAN_FRONTEND=noninteractive

# Cập nhật và cài đặt socat
# 'rm -rf...' để xóa cache, giúp giảm dung lượng image
RUN apt-get update && \
    apt-get install -y socat && \
    rm -rf /var/lib/apt/lists/*

# Tạo user ctf
RUN useradd -m ctf

# Thiết lập thư mục làm việc
WORKDIR /home/ctf

# Copy file vào
COPY chall .
COPY flag.txt .

# Phân quyền
RUN chmod +x chall && \
    chmod 444 flag.txt

# Chuyển user
USER ctf

# Mở port
EXPOSE 1337

# Chạy socat
CMD socat -T60 TCP-LISTEN:1337,reuseaddr,fork EXEC:./chall