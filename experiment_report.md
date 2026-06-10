# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600786
**Name:** Trần Mạnh Chánh Quân
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "Based on my data, the best choice is Laptop at $1200." | 9 | Du lieu da qua ETL: gia am va category rong da bi loai bo, gia tri hop le -> Agent tra ve san pham dien tu dat nhat dung mong doi (Laptop). |
| Garbage Data (`garbage_data.csv`) | "Based on my data, the best choice is Nuclear Reactor at $999999." | 2 | Du lieu chua duoc lam sach: outlier cuc lon (999999) keo ket qua sai lech, ID trung lap, sai kieu du lieu va null khien Agent tra ve san pham vo ly. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai khi dung Garbage Data vi du lieu dau vao chua duoc kiem dinh chat luong. Thu nhat, Outlier "Nuclear Reactor" co gia 999999 la mot gia tri bat thuong; vi Agent chon san pham theo gia cao nhat (idxmax), no lap tuc bi danh lua va tra ve mot ket qua vo nghia thay vi Laptop. Thu hai, Duplicate IDs (ID = 1 xuat hien hai lan) pha vo tinh duy nhat cua khoa, khien viec tra cuu va tong hop tro nen khong dang tin cay. Thu ba, Wrong Data Type: cot price chua chuoi "ten dollars" thay vi so, neu logic tinh toan gap phai gia tri nay se gay loi hoac sai ket qua. Cuoi cung, Null Values (id va category bang None) tao ra cac ban ghi ma khong the loc hoac so sanh chinh xac. Tat ca cac van de nay cho thay rac vao thi rac ra (garbage in, garbage out): du mo hinh hay cau lenh tot den dau, du lieu ban van pha hong ket qua.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Thi nghiem chung minh rang du lieu sach quan trong hon ca prompt hoan hao. Voi cung mot logic Agent va cung mot cau hoi, chi can thay doi chat luong du lieu la ket qua di tu chinh xac (Laptop) sang sai hoan toan (Nuclear Reactor). Mot prompt tot khong the cuu duoc du lieu rac, nhung mot pipeline ETL tot (validate + transform) dam bao Agent luon lam viec tren nen tang du lieu dang tin cay. Vi vay, dau tu vao Data Observability va lam sach du lieu la uu tien hang dau truoc khi toi uu prompt.
