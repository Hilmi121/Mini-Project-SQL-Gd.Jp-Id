# Mini-Project-SQL-Gd.Jp-Id
SQL Mini Project: Analysis of Online Shop Sales Jastip Jp-Id

CREATE TABLE pelanggan1 (
    id_pelanggan NUMBER PRIMARY KEY,
    nama_pelanggan VARCHAR2(50),
    alamat VARCHAR2(50)
);

INSERT INTO pelanggan1 VALUES (1, 'Hilmi', 'Jakarta');
INSERT INTO pelanggan1 VALUES (2, 'Nopal', 'Osaka');
INSERT INTO pelanggan1 VALUES (3, 'Afif', 'Jakarta');

SELECT * FROM pelanggan1
DROP TABLE actionfigure

CREATE TABLE fashion (
    id_fashion NUMBER PRIMARY KEY,
    judul_fashion VARCHAR(150),
    harga NUMBER
);

INSERT INTO fashion VALUES (101, 'Adidas', 2200000);
INSERT INTO fashion VALUES (102, 'Onitsuka Tiger', 2200000);
INSERT INTO fashion VALUES (103, 'GU', 450000);

SELECT * FROM fashion

CREATE TABLE Figure (
    id_figure NUMBER PRIMARY KEY,
    judul_figure VARCHAR(150),
    harga NUMBER
);

INSERT INTO figure VALUES (201, 'Labubu', 1000000);
INSERT INTO figure VALUES (202, 'Hirono', 500000);
INSERT INTO figure VALUES (203, 'Nailong', 250000);

SELECT * FROM figure
DROP TABLE figure

CREATE TABLE transaksi1 (
    id_transaksi NUMBER PRIMARY KEY,
    id_pelanggan NUMBER,
    tanggal DATE,
    CONSTRAINT fk_pelanggan1
        FOREIGN KEY (id_pelanggan)
        REFERENCES pelanggan1 (id_pelanggan)
);

INSERT INTO transaksi1 VALUES (1001, 1, SYSDATE);
INSERT INTO transaksi1 VALUES (1002, 2, SYSDATE);
INSERT INTO transaksi1 VALUES (1003, 3, SYSDATE);

SELECT * FROM transaksi1

CREATE TABLE transaksi11 (
    id_transaksi11 NUMBER PRIMARY KEY,
    id_pelanggan NUMBER,
    tanggal DATE,
    CONSTRAINT fk_pelanggan1
        FOREIGN KEY (id_pelanggan)
        REFERENCES pelanggan1 (id_pelanggan)
);

INSERT INTO transaksi11 VALUES (2001, 1, SYSDATE);
INSERT INTO transaksi11 VALUES (2002, 2, SYSDATE);
INSERT INTO transaksi11 VALUES (2003, 3, SYSDATE);

SELECT * FROM transaksi11

CREATE TABLE detail_transaksi1 (
    id_detail NUMBER PRIMARY KEY,
    id_transaksi1 NUMBER,
    id_fashion NUMBER,
    jumlah NUMBER,
    CONSTRAINT fk_transaksi1
        FOREIGN KEY (id_transaksi1)
        REFERENCES transaksi1(id_transaksi),
    CONSTRAINT fk_fashion
        FOREIGN KEY (id_fashion)
        REFERENCES fashion(id_fashion)
);

INSERT INTO detail_transaksi1 VALUES (1, 1001, 101, 1);
INSERT INTO detail_transaksi1 VALUES (2, 1001, 102, 2);
INSERT INTO detail_transaksi1 VALUES (3, 1002, 103, 1);
INSERT INTO detail_transaksi1 VALUES (4, 1003, 101, 3);

SELECT * FROM detail_transaksi1

CREATE TABLE detail_transaksi1 (
    id_detail NUMBER PRIMARY KEY,
    id_transaksi1 NUMBER,
    id_figure NUMBER,
    jumlah NUMBER,
    CONSTRAINT fk_transaksi1
        FOREIGN KEY (id_transaksi1)
        REFERENCES transaksi1(id_transaksi),
    CONSTRAINT fk_figure
        FOREIGN KEY (id_figure)
        REFERENCES fashion(id_figure)
);

INSERT INTO detail_transaksi1 VALUES (1, 1001, 101, 1);
INSERT INTO detail_transaksi1 VALUES (2, 1001, 102, 2);
INSERT INTO detail_transaksi1 VALUES (3, 1002, 103, 1);
INSERT INTO detail_transaksi1 VALUES (4, 1003, 101, 3);
