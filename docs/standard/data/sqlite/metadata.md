---
title: Meta Veriler
ms.date: 12/13/2019
description: Veritabanıyla ilgili meta verileri nasıl alacağınızı öğrenin.
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447197"
---
# <a name="metadata"></a>Meta Veriler

ADO.NET içinde meta verileri almak için iki API vardır. Biri sorgu sonuçlarıyla ilgili meta verileri alır. Diğeri veritabanı şeması hakkındaki meta verileri alır.

## <a name="query-result-metadata"></a>Sorgu sonucu meta verileri

`SqliteDataReader`<xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> yöntemi kullanarak bir sorgunun sonuçlarıyla ilgili meta verileri elde edebilirsiniz. Döndürülen <xref:System.Data.DataTable> şu sütunları içerir:

| Sütun             | Tür    | Açıklama                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | Boole değeri | Kaynak sütunu NULL olabilir.                                    |
| `BaseCatalogName`  | Dize  | Kaynak sütunun veritabanının adı. İfadeler için Always NULL.    |
| `BaseColumnName`   | Dize  | Kaynak sütunun diğer adı değil. İfadeler için Always NULL.    |
| `BaseSchemaName`   | Dize  | Her zaman NULL. SQLite şemaları desteklemez.                              |
| `BaseServerName`   | Dize  | Bağlantı dizesinde belirtilen veritabanı dosyasının yolu.         |
| `BaseTableName`    | Dize  | Kaynak sütunun tablosunun adı. İfadeler için Always NULL.       |
| `ColumnName`       | Dize  | Sonuç kümesindeki sütunun adı veya diğer adı.                        |
| `ColumnOrdinal`    | Int32   | Sonuç kümesindeki sütunun sıra sayısı.                              |
| `ColumnSize`       | Int32   | Always-1. Bu, `Microsoft.Data.Sqlite`sonraki sürümlerinde değişebilir.   |
| `DataType`         | Tür    | Sütunun varsayılan .NET veri türü.                                 |
| `DataTypeName`     | Dize  | Sütunun SQLite veri türü.                                       |
| `IsAliased`        | Boole değeri | Sonuç kümesinde sütun adı diğer ad ise true.                     |
| `IsAutoIncrement`  | Boole değeri | Kaynak sütunu AUTOıNCREMENT anahtar sözcüğüyle oluşturulduysa true.     |
| `IsExpression`     | Boole değeri | Sütun sorgudaki bir ifadeden kaynaklanıyorsa true.            |
| `IsKey`            | Boole değeri | Kaynak sütunu BIRINCIL ANAHTARıN parçasıysa doğru.                     |
| `IsUnique`         | Boole değeri | Kaynak sütunu BENZERSIZ ise doğru.                                      |
| `NumericPrecision` | Int16   | Her zaman NULL. Bu, `Microsoft.Data.Sqlite`sonraki sürümlerinde değişebilir. |
| `NumericScale`     | Int16   | Her zaman NULL. Bu, `Microsoft.Data.Sqlite`sonraki sürümlerinde değişebilir. |

Aşağıdaki örnek, bir sonuçla ilgili meta verileri gösteren bir hata ayıklama dizesi oluşturmak için `GetSchemaTable` nasıl kullanacağınızı gösterir:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

Örneğin, bu sorgu aşağıdaki hata ayıklama dizesini üretir:

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a>Şema meta verileri

Microsoft. Data. SQLite, DbConnection üzerinde GetSchema metodunu uygulamıyor. Bunun yerine, [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) ve [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list)gıbı [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tablo ve pragma deyimlerini kullanarak doğrudan şema bilgileri için sorgulama yapabilirsiniz.

Örneğin, bu sorgu veritabanındaki tüm sütunlarla ilgili meta verileri alır.

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a>Ayrıca bkz.

* [SQL veritabanı şemasının depolanması](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [PRAGMA deyimleri](https://www.sqlite.org/pragma.html)
* [Veri türleri](types.md)
