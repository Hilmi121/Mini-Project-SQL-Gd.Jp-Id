# Mini-Project-SQL-Gd.Jp-Id
SQL Mini Project: Analysis of Online Shop Sales Jastip Jp-Id

CREATE TABLE kategori (
    id_kategori NUMBER PRIMARY KEY,
    nama_kategori VARCHAR2(50)
);

INSERT INTO kategori VALUES (1, 'Figure');
INSERT INTO kategori VALUES (2, 'Fashion');
INSERT INTO kategori VALUES (3, 'Food');
INSERT INTO kategori VALUES (4, 'Beauty');

SELECT * FROM kategori

CREATE TABLE produk (
    id_produk NUMBER PRIMARY KEY,
    nama_produk VARCHAR2(100),
    harga NUMBER,
    stok NUMBER,
    id_kategori NUMBER,
    CONSTRAINT fk_kategori
    FOREIGN KEY (id_kategori)
    REFERENCES kategori(id_kategori)
);

INSERT INTO produk VALUES (101, 'Labubu', 1000000, 244, 1);
INSERT INTO produk VALUES (102, 'Hirono', 500000, 300, 1);
INSERT INTO produk VALUES (103, 'Nailong', 250000, 211, 1); 
INSERT INTO produk VALUES (104, 'Adidas', 2200000, 50, 2);
INSERT INTO produk VALUES (105, 'Onitsuka Tiger', 2200000, 75, 2);
INSERT INTO produk VALUES (106, 'GU', 450000, 111, 2);
INSERT INTO produk VALUES (107, 'Meiji', 82000, 30, 3);
INSERT INTO produk VALUES (108, 'Pocky', 45000, 70, 3);
INSERT INTO produk VALUES (109, 'Ghana', 78000, 60, 3);
INSERT INTO produk VALUES (110, 'Sabarino', 265000, 10, 4);
INSERT INTO produk VALUES (111, 'Melano', 145000, 15, 4);
INSERT INTO produk VALUES (112, 'Bioliss', 165000, 20, 4);

SELECT * FROM produk

CREATE TABLE customer (
    id_customer NUMBER PRIMARY KEY,
    nama_customer VARCHAR2(100),
    alamat VARCHAR2(50)
);

INSERT INTO customer VALUES (1, 'Hilmi', 'Jakarta');
INSERT INTO customer VALUES (2, 'Nopal', 'Osaka');
INSERT INTO customer VALUES (3, 'Afif', 'Jakarta');
INSERT INTO customer VALUES (4, 'Rafif', 'Bandung');
INSERT INTO customer VALUES (5, 'Rafly', 'Bandung');

SELECT * FROM customer

CREATE TABLE penjualan (
    id_penjualan NUMBER PRIMARY KEY,
    tanggal DATE,
    id_customer NUMBER,
    id_produk NUMBER,
    jumlah NUMBER,
    CONSTRAINT fk_customer
    FOREIGN KEY (id_customer)
    REFERENCES customer(id_customer),
    
    CONSTRAINT fk_produk
    FOREIGN KEY (id_produk)
    REFERENCES produk(id_produk)
);

INSERT INTO penjualan VALUES (
1,
TO_DATE('2025-01-05','YYYY-MM-DD'),
1,
101,
1
);

INSERT INTO penjualan VALUES (
2,
TO_DATE('2025-01-08','YYYY-MM-DD'),
2,
103,
3
);

INSERT INTO penjualan VALUES (
3,
TO_DATE('2025-01-10','YYYY-MM-DD'),
3,
104,
2
);

INSERT INTO penjualan VALUES (
4,
TO_DATE('2025-01-15','YYYY-MM-DD'),
1,
102,
5
);

INSERT INTO penjualan VALUES (
5,
TO_DATE('2025-01-18','YYYY-MM-DD'),
4,
106,
1
);

INSERT INTO penjualan VALUES (
6,
TO_DATE('2025-01-20','YYYY-MM-DD'),
5,
105,
10
);

INSERT INTO penjualan VALUES (
7,
TO_DATE('2025-01-25','YYYY-MM-DD'),
2,
101,
1
);

INSERT INTO penjualan VALUES (
8,
TO_DATE('2025-02-02','YYYY-MM-DD'),
3,
106,
2
);

SELECT * FROM penjualan

SELECT * FROM produk WHERE harga > 150000;

SELECT * FROM produk ORDER BY harga DESC;
