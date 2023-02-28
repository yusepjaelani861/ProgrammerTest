# Jawaban Programmer Test

# Jawaban Nomor 1
Jawaban nomor 1 bisa dilihat pada folder warpupProgrammerTest

# Jawaban terkait Software development knowledge*
### Why is writing software difficult?
Mungkin karena kekomplekannya, karena pengembangan suatu software membutuhkan banyak pemahaman terkait bahasa pemrograman, struktur data dan berbagai arsitektur software tersebut.

Kemudian terkait perubahan perkembangan teknologi. Perkembangan teknologi saat ini berkembang dengan sangat cepat dan kita harus mengikuti suatu bahasa baru/kerangka baru agar bisa tetap mengikuti perkembangannya.

Error/Bug. Hal tersebut  adalah sesuatu yang pasti ada dan kadang agak sulit untuk menemukan suatu kesalahan/bug pada suatu baris kode yang banyak/besar.

### What makes maintaining software hard?
Maintenance software sulit mungkin karena kode atau kodingan lama. Hal itu akan menjadi suatu tantangan apabila terus mempertahankan kodingan lama.

Lalu pembaruan atau modifikasi kode. Ini bisa jadi tantangan juga apabila kode tersebut tidak mempertimbangkan fleksibilitas dalam pembuatan perangkat lunak.


# Jawaban UseCase Technical Test

## Jawaban Nomor 1.

### Struktur database di bawah ini dibuat menggunakan struktur dari PrismaORM Typescript.

```bash
model customer {
  id                 Int                @id @default(autoincrement())
  customer_name      String             @db.VarChar(50)
  customer_addresses customer_address[]
  order              order[]
}

model customer_address {
  id          Int      @id @default(autoincrement())
  customer_id Int
  address     String   @db.VarChar(50)
  customer    customer @relation(fields: [customer_id], references: [id], onDelete: Cascade)
  order       order[]
}

model product {
  id           Int            @id @default(autoincrement())
  name         String         @db.VarChar(50)
  price        Int
  order_detail order_detail[]
}

model payment_method {
  id        Int     @id @default(autoincrement())
  name      String  @db.VarChar(50)
  is_active Boolean @default(false)
}

model order {
  id                  Int              @id @default(autoincrement())
  customer_id         Int
  customer_address_id Int
  customer            customer         @relation(fields: [customer_id], references: [id], onDelete: Cascade)
  order_details       order_detail[]
  customer_address    customer_address @relation(fields: [customer_address_id], references: [id], onDelete: Cascade)
}

model order_detail {
  id          Int     @id @default(autoincrement())
  order_id    Int
  product_id  Int
  order       order   @relation(fields: [order_id], references: [id], onDelete: Cascade)
  product     product @relation(fields: [product_id], references: [id], onDelete: Cascade)
}
```


## Jawaban Nomor 2
Agar tidak terjadinya error atau relasi tidak ditemukan ketika pada table A dihapus dan memiliki relasi di table B, bisa menggunakan Cascade pada SQL/Database. Jadi ketika 1 data di table customer di hapus, apabila memiliki relasi misalkan pada table order dan address, maka sesuatu yang berelasi dengan id customer tersebut akan ikut terhapus.


## Jawaban Nomor 3
Silahkan kunjungi link github berikut.

[TechnicalTestBackend](https://github.com/yusepjaelani861/TechnicalTestBackend)