# Thronedis Token-Gated Page (Polygon)

หน้าเว็บตัวอย่างสำหรับ **Token Gate ด้วยคอลเล็กชัน NFT** (ERC‑721/1155) บน Polygon (chainId 137) โดยตรวจสิทธิ์จากการถือโทเค็นในคอลเล็กชัน

- Contract (Collection): `0x76f4E59DBBF99D025B6F1014D33843AB138e4085`
- IPFS CID (ไฟล์ที่ล็อค): `bafybeigsrytimlmv4dkz2px7ke4bwco4qj2kgxsdaeaxgmvkubiuexh5cu`
- ไฟล์หน้าเว็บ: `export.html` (เปิดใช้งานได้ทันที)

> หมายเหตุ: โค้ดตรวจชนิดสัญญาอัตโนมัติ (ERC‑721/1155) ด้วย ERC‑165  
> ERC‑721: ถืออะไรก็ได้ในคอลเล็กชัน = ผ่าน  
> ERC‑1155: กำหนด `TOKEN_IDS` ในไฟล์เพื่อระบุรายการ id ที่อนุญาต (หรือทำตรวจสิทธิ์ที่ backend เพื่อรองรับทั้งคอลเล็กชันจริง ๆ)

---

## โครงสร้างไฟล์

```
.
├─ export.html     # หน้าเว็บ Token Gate
└─ README.md
```

## การใช้งานแบบเร็ว (ทดสอบบนเครื่อง)

1) เปิดไฟล์ `export.html` ด้วยเบราว์เซอร์ที่ติดตั้ง MetaMask  
2) สลับเครือข่ายเป็น **Polygon Mainnet** ถ้าระบบถามให้กดยืนยัน  
3) กด **Connect Wallet & Verify**  
4) ถ้าถือ NFT ตามเงื่อนไข จะเห็นลิงก์ IPFS สำหรับดาวน์โหลด

> **ความปลอดภัย:** IPFS เป็น public — ใครได้ลิงก์ก็เข้าถึงได้ หากต้องการกันแชร์ลิงก์ แนะนำทำ backend สร้าง **one‑time download link** หลังตรวจสิทธิ์

## ตั้งค่าที่แก้ได้ใน `export.html`

- `CONTRACT_ADDRESS` – ที่อยู่คอลเล็กชัน NFT
- `NETWORK_HEX` – โครงข่าย (ดีฟอลต์เป็น Polygon `0x89`)
- `TOKEN_IDS` – (เฉพาะ ERC‑1155) รายการ tokenId ที่ถือแล้วให้ปลดล็อกได้
- ลิงก์ IPFS ที่จะแสดงเมื่อปลดล็อก (`#secret` section)

## Deploy ไป GitHub Pages

1) สร้างรีโพใหม่บน GitHub (public) แล้วอัปโหลดไฟล์ `export.html` และ `README.md`
2) ไปที่ **Settings → Pages**
3) ตั้งค่า **Source = Deploy from a branch**
4) เลือกสาขา `main` (หรือ `master`) และโฟลเดอร์ราก `/ (root)`
5) กด Save แล้วรอสักครู่
6) หน้าเว็บจะอยู่ที่ `https://<username>.github.io/<repo>/export.html`

> หากใช้ชื่อไฟล์ `index.html` สามารถเข้าถึงได้ที่หน้า root ทันที

## คำเตือน/ข้อควรทราบ

- เบราว์เซอร์ต้องมี **MetaMask** หรือ Wallet ที่รองรับ `window.ethereum`
- หากคอลเล็กชันเป็น ERC‑1155 และมีหลาย tokenId มาก ๆ แนะนำทำตรวจที่ **backend** เพื่อประสิทธิภาพและความยืดหยุ่น
- โค้ดนี้เป็นตัวอย่าง **ฝั่ง client** เท่านั้น

---

## English (Brief)

This is a simple client-side token-gated page for an NFT **collection** on Polygon.  
It auto-detects whether the contract is ERC‑721 or ERC‑1155 via ERC‑165.

- For **ERC‑721**: access is granted if `balanceOf(user) > 0`.
- For **ERC‑1155**: set `TOKEN_IDS` to the list of token IDs that should unlock access (or move validation to a backend).

To deploy on **GitHub Pages**: upload `export.html` + `README.md`, enable Pages from repo Settings, and visit `https://<username>.github.io/<repo>/export.html`.
