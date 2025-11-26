FROM ubuntu:24.04

# Cài đặt python3 và socat
RUN apt-get update && apt-get install -y python3 socat

# Tạo user ctf để chạy bài
RUN useradd -m ctf
WORKDIR /home/ctf

# Copy các file cần thiết
COPY chall .
COPY flag.txt .
COPY wrapper.py .

# Cấp quyền thực thi cho binary
RUN chmod +x chall && chmod 444 flag.txt

# Chuyển user
USER ctf

# Mở port 1337
EXPOSE 1335

CMD socat -T60 TCP-LISTEN:1335,reuseaddr,fork EXEC:"python3 -u wrapper.py"