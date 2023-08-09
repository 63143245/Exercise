# 1.สร้างไฟล์ README.md 

    ถ้ายังไม่มีไฟล์ README.md ใน root directory ของ Git repository ของคุณ ให้สร้างไฟล์ดังกล่าวขึ้นมาใหม่ โดยใช้โปรแกรมแก้ไขข้อความเช่น Notepad (สำหรับ Windows) หรือ Visual Studio Code.

# 2.เพิ่มข้อมูลในไฟล์ README.md

    เพิ่มข้อมูลดังต่อไปนี้ในไฟล์ README.md เพื่อให้คำแนะนำเกี่ยวกับวิธีการ build และ run โปรเจค Flask ของคุณ:
    # วิธีการ Build และ Run โปรเจค Flask

    โค้ดต่อไปนี้คือตัวอย่างของแอปพลิเคชัน Flask ที่สร้างเพื่อคำนวณและแสดงลำดับของตัวเลข Fibonacci ตามจำนวนสมาชิกที่กำหนด:

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
2323