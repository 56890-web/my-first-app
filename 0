import streamlit as st

# ตั้งค่าหน้าเว็บ
st.markdown("# :blue[🛒 ร้านค้าขายเครื่องเขียน สมุดมิตร]")
st.write("ยินดีต้อนรับเข้าสู่ระบบคำนวณเงินและส่วนลดอัตโนมัติ")
st.write("---")

# ส่วนที่ 1: รับจำนวนสินค้าแต่ละรายการจากผู้ใช้งาน
st.subheader("📝 เลือกจำนวนสินค้าที่ต้องการซื้อ")
qty_notebook = st.number_input("สมุด (13 บาท)", min_value=0, value=0, step=1)
qty_pen = st.number_input("ปากกา (10 บาท)", min_value=0, value=0, step=1)
qty_pencil = st.number_input("ดินสอ (7 บาท)", min_value=0, value=0, step=1)
qty_eraser = st.number_input("ยางลบ (5 บาท)", min_value=0, value=0, step=1)
qty_correction = st.number_input("ลิควิดน้ำ (15 บาท)", min_value=0, value=0, step=1)
qty_tape = st.number_input("ลิควิดเทป (20 บาท)", min_value=0, value=0, step=1)
qty_ruler = st.number_input("ไม้บรรทัด (16 บาท)", min_value=0, value=0, step=1)

# ส่วนที่ 2: คำนวณราคารวมทั้งหมด
if st.button("คำนวณเงินทั้งหมด 💰"):
    total_price = (
        (qty_notebook * 13) +
        (qty_pen * 10) +
        (qty_pencil * 7) +
        (qty_eraser * 5) +
        (qty_correction * 15) +
        (qty_tape * 20) +
        (qty_ruler * 16)
    )
    
    st.write("---")
    st.write(f"ยอดซื้อรวมทั้งหมด: **{total_price} บาท**")

    # ส่วนที่ 3: เช็คเงื่อนไข if-else เพื่อคำนวณส่วนลดประจำร้าน
    # เกณฑ์: ยอดซื้อ 500-700 ลด 2% | 701-900 ลด 4% | 901 ขึ้นไป ลด 5%
    if 500 <= total_price <= 700:
        discount_rate = 0.02
        discount_text = "ลด 2%"
    elif 701 <= total_price <= 900:
        discount_rate = 0.04
        discount_text = "ลด 4%"
    elif total_price > 900:
        discount_rate = 0.05
        discount_text = "ลด 5%"
    else:
        discount_rate = 0.0
        discount_text = "ไม่มีส่วนลด (ยอดซื้อไม่ถึง 500 บาท)"

    discount_amount = total_price * discount_rate
    final_price = total_price - discount_amount

    st.info(f"สิทธิ์ส่วนลดของคุณ: {discount_text} (ส่วนลด {discount_amount:.2f} บาท)")
    st.header(f"ยอดเงินที่ต้องจ่ายจริง: **{final_price:.2f} บาท**")

    # ส่วนที่ 4: รับเงินจากลูกค้า และคำนวณเงินทอน
    st.write("---")
    cash_received = st.number_input("รับเงินสดจากลูกค้า (บาท):", min_value=0.0, value=0.0)
    
    if cash_received > 0:
        if cash_received >= final_price:
            change = cash_received - final_price
            st.success(f"💵 เงินทอน: **{change:.2f} บาท**")
        else:
            st.error("⚠️ เงินสดที่รับมาไม่พอจ่าย กรุณาตรวจสอบใหม่อีกครั้ง")

st.divider()
st.write("ผู้จัดทำ: ภาคิณ ดวงศรี เลขที่ 35 ม.4/...")
