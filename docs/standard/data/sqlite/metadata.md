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
# <a name="metadata"></a><span data-ttu-id="e767d-103">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="e767d-103">Metadata</span></span>

<span data-ttu-id="e767d-104">ADO.NET içinde meta verileri almak için iki API vardır.</span><span class="sxs-lookup"><span data-stu-id="e767d-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="e767d-105">Biri sorgu sonuçlarıyla ilgili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="e767d-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="e767d-106">Diğeri veritabanı şeması hakkındaki meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="e767d-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="e767d-107">Sorgu sonucu meta verileri</span><span class="sxs-lookup"><span data-stu-id="e767d-107">Query result metadata</span></span>

<span data-ttu-id="e767d-108">Üzerinde <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> `SqliteDataReader`yöntemi kullanarak bir sorgunun sonuçlarıyla ilgili meta verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e767d-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="e767d-109">Döndürülen <xref:System.Data.DataTable> şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="e767d-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="e767d-110">Sütun</span><span class="sxs-lookup"><span data-stu-id="e767d-110">Column</span></span>             | <span data-ttu-id="e767d-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e767d-111">Type</span></span>    | <span data-ttu-id="e767d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e767d-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="e767d-113">Boole</span><span class="sxs-lookup"><span data-stu-id="e767d-113">Boolean</span></span> | <span data-ttu-id="e767d-114">Kaynak sütunu NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="e767d-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="e767d-115">Dize</span><span class="sxs-lookup"><span data-stu-id="e767d-115">String</span></span>  | <span data-ttu-id="e767d-116">Kaynak sütunun veritabanının adı.</span><span class="sxs-lookup"><span data-stu-id="e767d-116">The name of the origin column's database.</span></span> <span data-ttu-id="e767d-117">İfadeler için Always NULL.</span><span class="sxs-lookup"><span data-stu-id="e767d-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="e767d-118">Dize</span><span class="sxs-lookup"><span data-stu-id="e767d-118">String</span></span>  | <span data-ttu-id="e767d-119">Kaynak sütunun diğer adı değil.</span><span class="sxs-lookup"><span data-stu-id="e767d-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="e767d-120">İfadeler için Always NULL.</span><span class="sxs-lookup"><span data-stu-id="e767d-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="e767d-121">Dize</span><span class="sxs-lookup"><span data-stu-id="e767d-121">String</span></span>  | <span data-ttu-id="e767d-122">Her zaman NULL.</span><span class="sxs-lookup"><span data-stu-id="e767d-122">Always NULL.</span></span> <span data-ttu-id="e767d-123">SQLite şemaları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e767d-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="e767d-124">Dize</span><span class="sxs-lookup"><span data-stu-id="e767d-124">String</span></span>  | <span data-ttu-id="e767d-125">Bağlantı dizesinde belirtilen veritabanı dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="e767d-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="e767d-126">Dize</span><span class="sxs-lookup"><span data-stu-id="e767d-126">String</span></span>  | <span data-ttu-id="e767d-127">Kaynak sütunun tablosunun adı.</span><span class="sxs-lookup"><span data-stu-id="e767d-127">The name of the origin column's table.</span></span> <span data-ttu-id="e767d-128">İfadeler için Always NULL.</span><span class="sxs-lookup"><span data-stu-id="e767d-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="e767d-129">Dize</span><span class="sxs-lookup"><span data-stu-id="e767d-129">String</span></span>  | <span data-ttu-id="e767d-130">Sonuç kümesindeki sütunun adı veya diğer adı.</span><span class="sxs-lookup"><span data-stu-id="e767d-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="e767d-131">Int32</span><span class="sxs-lookup"><span data-stu-id="e767d-131">Int32</span></span>   | <span data-ttu-id="e767d-132">Sonuç kümesindeki sütunun sıra sayısı.</span><span class="sxs-lookup"><span data-stu-id="e767d-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="e767d-133">Int32</span><span class="sxs-lookup"><span data-stu-id="e767d-133">Int32</span></span>   | <span data-ttu-id="e767d-134">Always-1.</span><span class="sxs-lookup"><span data-stu-id="e767d-134">Always -1.</span></span> <span data-ttu-id="e767d-135">Bu, gelecekteki sürümlerinde değişebilir `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="e767d-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="e767d-136">Tür</span><span class="sxs-lookup"><span data-stu-id="e767d-136">Type</span></span>    | <span data-ttu-id="e767d-137">Sütunun varsayılan .NET veri türü.</span><span class="sxs-lookup"><span data-stu-id="e767d-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="e767d-138">Dize</span><span class="sxs-lookup"><span data-stu-id="e767d-138">String</span></span>  | <span data-ttu-id="e767d-139">Sütunun SQLite veri türü.</span><span class="sxs-lookup"><span data-stu-id="e767d-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="e767d-140">Boole</span><span class="sxs-lookup"><span data-stu-id="e767d-140">Boolean</span></span> | <span data-ttu-id="e767d-141">Sonuç kümesinde sütun adı diğer ad ise true.</span><span class="sxs-lookup"><span data-stu-id="e767d-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="e767d-142">Boole</span><span class="sxs-lookup"><span data-stu-id="e767d-142">Boolean</span></span> | <span data-ttu-id="e767d-143">Kaynak sütunu AUTOıNCREMENT anahtar sözcüğüyle oluşturulduysa true.</span><span class="sxs-lookup"><span data-stu-id="e767d-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="e767d-144">Boole</span><span class="sxs-lookup"><span data-stu-id="e767d-144">Boolean</span></span> | <span data-ttu-id="e767d-145">Sütun sorgudaki bir ifadeden kaynaklanıyorsa true.</span><span class="sxs-lookup"><span data-stu-id="e767d-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="e767d-146">Boole</span><span class="sxs-lookup"><span data-stu-id="e767d-146">Boolean</span></span> | <span data-ttu-id="e767d-147">Kaynak sütunu BIRINCIL ANAHTARıN parçasıysa doğru.</span><span class="sxs-lookup"><span data-stu-id="e767d-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="e767d-148">Boole</span><span class="sxs-lookup"><span data-stu-id="e767d-148">Boolean</span></span> | <span data-ttu-id="e767d-149">Kaynak sütunu BENZERSIZ ise doğru.</span><span class="sxs-lookup"><span data-stu-id="e767d-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="e767d-150">Int16</span><span class="sxs-lookup"><span data-stu-id="e767d-150">Int16</span></span>   | <span data-ttu-id="e767d-151">Her zaman NULL.</span><span class="sxs-lookup"><span data-stu-id="e767d-151">Always NULL.</span></span> <span data-ttu-id="e767d-152">Bu, gelecekteki sürümlerinde değişebilir `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="e767d-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="e767d-153">Int16</span><span class="sxs-lookup"><span data-stu-id="e767d-153">Int16</span></span>   | <span data-ttu-id="e767d-154">Her zaman NULL.</span><span class="sxs-lookup"><span data-stu-id="e767d-154">Always NULL.</span></span> <span data-ttu-id="e767d-155">Bu, gelecekteki sürümlerinde değişebilir `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="e767d-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="e767d-156">Aşağıdaki örnek, bir sonuçla ilgili meta `GetSchemaTable` verileri gösteren bir hata ayıklama dizesi oluşturmak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e767d-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="e767d-157">Örneğin, bu sorgu aşağıdaki hata ayıklama dizesini üretir:</span><span class="sxs-lookup"><span data-stu-id="e767d-157">For example, this query would produce the following debug string:</span></span>

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

## <a name="schema-metadata"></a><span data-ttu-id="e767d-158">Şema meta verileri</span><span class="sxs-lookup"><span data-stu-id="e767d-158">Schema metadata</span></span>

<span data-ttu-id="e767d-159">Microsoft. Data. SQLite, DbConnection üzerinde GetSchema metodunu uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="e767d-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="e767d-160">Bunun yerine, [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) ve [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list)gıbı [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tablo ve pragma deyimlerini kullanarak doğrudan şema bilgileri için sorgulama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e767d-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="e767d-161">Örneğin, bu sorgu veritabanındaki tüm sütunlarla ilgili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="e767d-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="e767d-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e767d-162">See also</span></span>

* [<span data-ttu-id="e767d-163">SQL veritabanı şemasının depolanması</span><span class="sxs-lookup"><span data-stu-id="e767d-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="e767d-164">PRAGMA deyimleri</span><span class="sxs-lookup"><span data-stu-id="e767d-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="e767d-165">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="e767d-165">Data types</span></span>](types.md)
