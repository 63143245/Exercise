# 1.สร้างไฟล์ README.md 

    ถ้ายังไม่มีไฟล์ README.md ใน root directory ของ Git repository ของคุณ ให้สร้างไฟล์ดังกล่าวขึ้นมาใหม่ โดยใช้โปรแกรมแก้ไขข้อความเช่น Notepad (สำหรับ Windows) หรือ Visual Studio Code

# 2.เพิ่มข้อมูลในไฟล์ README.md

    เพิ่มข้อมูลดังต่อไปนี้ในไฟล์ README.md เพื่อให้คำแนะนำเกี่ยวกับวิธีการ build และ run โปรเจค Flask ของคุณ

# 2.1 วิธีการ Build และ Run โปรเจค Flask

    โค้ดต่อไปนี้คือตัวอย่างของแอปพลิเคชัน Flask ที่สร้างเพื่อคำนวณและแสดงลำดับของตัวเลข Fibonacci ตามจำนวนสมาชิกที่กำหนด

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

def fibonacci(n):
    fib_sequence = [0, 1]
    for _ in range(n - 2):
        fib_sequence.append(fib_sequence[-1] + fib_sequence[-2])
    return fib_sequence

@app.route('/api/surasit/test/<int:member_count>', methods=['GET'])
def get_fibonacci(member_count):
    if 1 <= member_count <= 100:
        fib_list = fibonacci(member_count)
        fib_sum = sum(fib_list)

        response = {
            'member-count': member_count,
            'sequence': fib_list,
            'total': fib_sum
        }

        return jsonify(response)
    else:
        return jsonify({'error': 'จำนวนสมาชิกต้องอยู่ระหว่าง 1 และ 100'})

if __name__ == '__main__':
    app.run(debug=True)

# วิธีการใช้งาน 

    1.ติดตั้ง Flask

    ก่อนอื่นให้ติดตั้ง Flask บนระบบของคุณ โดยใช้คำสั่งต่อไปนี้ใน Terminal 
      pip install Flask

    2.Run แอปพลิเคชัน
    เปิด Terminal แล้วเข้าสู่ไดเรกทอรีของโปรเจค จากนั้นใช้คำสั่งต่อไปนี้เพื่อรันแอปพลิเคชัน
      python att surasit.py

    3.ทดสอบ API 
    เมื่อแอปพลิเคชันกำลังทำงาน คุณสามารถเรียกใช้ API ผ่านเบราว์เซอร์หรือโปรแกรมที่สามารถทำ HTTP Request ได้ เช่น http://localhost:5000/api/surasit/test/10 เพื่อคำนวณลำดับ Fibonacci ของสมาชิก n คน
