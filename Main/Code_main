import subprocess


def scan_arp():
  try:
    result = subprocess.run(
        ["su", "-c", "cat /proc/net/arp"],
        capture_output=True,
        text=True,
        check=True,
    )
    lines = result.stdout.strip().split("\n")

    if len(lines) <= 1:
      print("Không tìm thấy thiết bị kết nối.")
      return

    print(f"{'IP Address':<18} {'MAC Address':<20} {'Interface'}")
    print("-" * 52)

    for line in lines[1:]:
      parts = line.split()
      if len(parts) >= 6:
        print(f"{parts[0]:<18} {parts[3]:<20} {parts[5]}")

  except subprocess.CalledProcessError:
    print("Lỗi: Thiếu quyền root hoặc không thể thực thi lệnh.")
  except Exception as e:
    print(f"Lỗi hệ thống: {e}")


if __name__ == "__main__":
  scan_arp()
