# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600549
**Name:** Lê Xuân Tiến Đạt
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 9 | Tra loi dung. Du lieu da qua pipeline validate + transform nen sach, khong con gia am/null/sai kieu. |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Tra loi sai. Agent bi danh lua boi outlier gia 999999 va khong loc duoc du lieu rac. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai vi no chi don gian chon san pham co gia cao nhat ma khong he kiem tra chat luong du lieu dau vao. Voi bo Garbage Data, co rat nhieu loi nghiem trong khien ket qua bi "ngo doc". Thu nhat la **Extreme Outlier**: ban ghi "Nuclear Reactor" co gia 999999 la mot gia tri bat thuong, nhung Agent lai tuong day la mon hang tot nhat nen da chon no thay vi Laptop. Thu hai la **Duplicate IDs**: co hai ban ghi cung mang id=1 (Laptop va Banana), gay nhap nhang khi truy van va de lam sai logic dem hoac join du lieu. Thu ba la **Wrong Data Types**: ban ghi "Broken Chair" co gia la chuoi "ten dollars" thay vi so, neu Agent co gang tinh toan se gay crash hoac bi bo qua sai cach. Thu tu la **Null Values**: ban ghi "Ghost Item" co id va category deu rong (None) cung gia bang 0, lam ban du lieu va co the gay loi khi nhom theo category. Tat ca nhung van de nay deu la nhung loi chat luong du lieu kinh dien ma neu khong co buoc validate trong pipeline ETL thi Agent se dua ra quyet dinh hoan toan sai lam.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Du Agent co logic thong minh hay prompt tot den dau, neu du lieu dau vao ban thi ket qua van sai (Garbage In, Garbage Out). Thi nghiem cho thay cung mot Agent, cung mot cau hoi, nhung chi can thay du lieu sach bang du lieu rac la cau tra loi tu dung (Laptop) thanh sai (Nuclear Reactor). Vi vay, buoc validate va lam sach du lieu trong pipeline ETL la nen mong bat buoc cho moi he thong AI dang tin cay.
