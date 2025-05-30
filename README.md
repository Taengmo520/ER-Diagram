# ER-Diagram

ระบบนี้ออกแบบมาเพื่อรองรับการซื้อ-ขายแลกเปลี่ยนคริปโต (เช่น BTC, ETH, XRP, DOGE) ด้วยเงินสกุล Fiat (THB, USD) และรองรับการโอนเหรียญภายใน/ภายนอกระบบ

### Entity

- `User`  
  ผู้ใช้ที่ลงทะเบียนในระบบ มีข้อมูลส่วนตัว เช่น อีเมล, เบอร์โทร, สถานะ KYC  
  ผู้ใช้ 1 คนสามารถมีหลายกระเป๋าเงิน

- `FiatWallet`  
  กระเป๋าเงินสำหรับเก็บเงินสกุลทั่วไป เช่น THB, USD  
  ผูกกับผู้ใช้ 1 คน

- `CryptoWallet`  
  กระเป๋าเงินคริปโตที่แยกตามเหรียญ (BTC, ETH, etc.)  
  ผูกกับผู้ใช้ 1 คน

- `TradeOrder`  
  คำสั่งขายเหรียญที่ผู้ใช้ตั้งขึ้น เช่น “ขาย 1 BTC ราคา 1.2 ล้านบาท”  
  จะถูกจับคู่กับผู้ซื้อในระบบ

- `TradeTransaction`  
  ธุรกรรมที่เกิดจากการซื้อจากคำสั่งขาย  
  ระบุผู้ซื้อ-ผู้ขาย ปริมาณ และจำนวนเงิน

- `CryptoTransfer`  
  การโอนเหรียญระหว่างผู้ใช้ภายในระบบ หรือออกไปนอกระบบ  
  รองรับการระบุ Address ปลายทางภายนอก

---

## การทำงานของระบบโดยสรุป

1. ผู้ใช้สมัครบัญชี และสร้างกระเป๋าเงิน (Fiat/Crypto)
2. ผู้ขายตั้ง TradeOrder เพื่อขายเหรียญ
3. ผู้ซื้อจับคู่คำสั่งเพื่อซื้อเหรียญ
4. ระบบบันทึก TradeTransaction พร้อมโอนเหรียญและหักยอดเงิน Fiat
5. ผู้ใช้สามารถโอนเหรียญให้กันในระบบ หรือออกไปยัง wallet ภายนอกได้

---

