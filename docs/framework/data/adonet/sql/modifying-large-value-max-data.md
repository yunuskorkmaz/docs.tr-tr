---
title: Büyük Değer (max) Veri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174283"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="724a9-102">ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="724a9-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="724a9-103">Büyük nesne (LOB) veri türleri, maksimum satır boyutunu 8 kilobayt (KB) aşan veri türleridir.</span><span class="sxs-lookup"><span data-stu-id="724a9-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="724a9-104">SQL Server, `max` 2^32 `nvarchar`bayt kadar büyük değerlerin depolanmasına izin vermek için , ve `varbinary` veri türleri için `varchar`bir belirtim sağlar.</span><span class="sxs-lookup"><span data-stu-id="724a9-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="724a9-105">Tablo sütunları ve Transact-SQL `varchar(max)` `nvarchar(max)`değişkenleri `varbinary(max)` , veya veri türleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="724a9-106">ADO.NET olarak, `max` veri türleri bir , `DataReader`tarafından getirilebilir ve ayrıca herhangi bir özel işleme olmadan hem giriş hem de çıkış parametre değerleri olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="724a9-107">Büyük `varchar` veri türleri için veriler alınabilir ve artımlı olarak güncellenebilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="724a9-108">Veri `max` türleri karşılaştırmalar, Transact-SQL değişkenleri olarak ve birlikteleştirme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="724a9-109">Ayrıca, SELECT deyiminin DISTINCT, ORDER BY, GROUP by yan tümcelerinde ve toplamlar, birleştirmeler ve alt sorgularda da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="724a9-110">Aşağıdaki tablo, SQL Server Books Online'daki belgelere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="724a9-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="724a9-111">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="724a9-111">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="724a9-112">[Büyük Değer Veri Türlerini Kullanma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="724a9-112">[Using Large-Value Data Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="724a9-113">Büyük Değer Türü Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="724a9-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="724a9-114">Aşağıdaki kısıtlamalar, daha `max` küçük veri türleri için bulunmayan veri türleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="724a9-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="724a9-115">A `sql_variant` büyük `varchar` bir veri türü içeremez.</span><span class="sxs-lookup"><span data-stu-id="724a9-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="724a9-116">Büyük `varchar` sütunlar bir dizinteki anahtar sütun olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="724a9-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="724a9-117">Kümelenmiş olmayan bir dizinde dahil edilmiş bir sütunda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="724a9-118">Büyük `varchar` sütunlar, anahtar sütunları bölümleme olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="724a9-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="724a9-119">Transact-SQL'de Büyük Değer Türleri ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="724a9-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="724a9-120">Transact-SQL `OPENROWSET` işlevi, uzak verileri bağlamak ve erişmek için tek seferlik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="724a9-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="724a9-121">Bir OLE DB veri kaynağından uzak verilere erişmek için gereken tüm bağlantı bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="724a9-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="724a9-122">`OPENROWSET`bir sorgunun FROM yan tümcesinde tablo adıymış gibi başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="724a9-123">OLE DB sağlayıcısının yeteneklerine bağlı olarak bir INSERT, UPDATE veya DELETE deyiminin hedef tablosu olarak da başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="724a9-124">İşlev, `OPENROWSET` `BULK` verileri hedef tabloya yüklemeden verileri doğrudan bir dosyadan okumanızı sağlayan satır kümesi sağlayıcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="724a9-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="724a9-125">Bu, basit bir `OPENROWSET` INSERT SELECT deyiminde kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="724a9-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="724a9-126">Seçenek `OPENROWSET BULK` bağımsız değişkenleri, okuma verilerinin nereden başlanacağı ve sonlanacağı, hatalarla nasıl başa çıkılabilen ve verilerin nasıl yorumlanacağı konusunda önemli denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="724a9-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="724a9-127">Örneğin, veri dosyasının tek satırlı, tek sütunlu bir satır türü `varbinary`, `varchar`veya `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="724a9-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="724a9-128">Sözdiziminin ve seçeneklerin tamamı için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="724a9-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="724a9-129">Aşağıdaki örnek, AdventureWorks örnek veritabanındaki ProductPhoto tablosuna bir fotoğraf ekler.</span><span class="sxs-lookup"><span data-stu-id="724a9-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="724a9-130">Sağlayıcıkullanırken, `BULK OPENROWSET` her sütuna değerler eklemeseniz bile adlandırılmış sütun listesini sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="724a9-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="724a9-131">Bu durumda birincil anahtar bir kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="724a9-132">`OPENROWSET` Ayrıca, bu durumda ThumbnailPhoto olan bildirimin sonunda bir korelasyon adı sağlamanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="724a9-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="724a9-133">Bu, dosyanın yüklendiği `ProductPhoto` tablodaki sütunla ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="724a9-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="724a9-134">UPDATE kullanarak Verileri Güncelleme . Yazmak</span><span class="sxs-lookup"><span data-stu-id="724a9-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="724a9-135">Transact-SQL UPDATE deyimi, sütunların `varchar(max)` `nvarchar(max)`veya `varbinary(max)` sütunların içeriğini değiştirmek için yeni WRITE sözdizimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="724a9-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="724a9-136">Bu, verilerin kısmi güncelleştirmelerini gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="724a9-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="724a9-137">GÜNCELLEME . WRITE sözdizimi burada kısaltılmış biçimde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="724a9-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="724a9-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="724a9-138">UPDATE</span></span>  
  
 <span data-ttu-id="724a9-139">{ \* \<nesne>\* }</span><span class="sxs-lookup"><span data-stu-id="724a9-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="724a9-140">SET</span><span class="sxs-lookup"><span data-stu-id="724a9-140">SET</span></span>  
  
 <span data-ttu-id="724a9-141">{ *column_name* = { . WRITE *expression* ( @Offset ifade @Length , , ) }</span><span class="sxs-lookup"><span data-stu-id="724a9-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="724a9-142">WRITE yöntemi, *column_name* değerinin bir bölümünün değiştirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="724a9-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="724a9-143">İfade, *column_name*kopyalanacak `@Offset` değerdir, ifadenin yazılacağı başlangıç noktasıdır ve `@Length` bağımsız değişken sütundaki bölümün uzunluğudur.</span><span class="sxs-lookup"><span data-stu-id="724a9-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="724a9-144">Eğer</span><span class="sxs-lookup"><span data-stu-id="724a9-144">If</span></span>|<span data-ttu-id="724a9-145">Ardından</span><span class="sxs-lookup"><span data-stu-id="724a9-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="724a9-146">İfade NULL olarak ayarlanır</span><span class="sxs-lookup"><span data-stu-id="724a9-146">The expression is set to NULL</span></span>|<span data-ttu-id="724a9-147">`@Length`yoksayılmalı ve *column_name* değeri belirtilen `@Offset`de kesilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="724a9-148">`@Offset`NULL olduğunu</span><span class="sxs-lookup"><span data-stu-id="724a9-148">`@Offset` is NULL</span></span>|<span data-ttu-id="724a9-149">Güncelleştirme işlemi, varolan *column_name* değerinin sonundaki ifadeyi ekler ve `@Length` yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="724a9-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="724a9-150">`@Offset`column_name değerinin uzunluğundan büyüktür</span><span class="sxs-lookup"><span data-stu-id="724a9-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="724a9-151">SQL Server bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="724a9-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="724a9-152">`@Length`NULL olduğunu</span><span class="sxs-lookup"><span data-stu-id="724a9-152">`@Length` is NULL</span></span>|<span data-ttu-id="724a9-153">Güncelleştirme `column_name` işlemi, değerin `@Offset` sonuna kadar tüm verileri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="724a9-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="724a9-154">Negatif `@Offset` `@Length` sayı ne de olabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="724a9-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="724a9-155">Example</span></span>  
 <span data-ttu-id="724a9-156">Bu Transact-SQL örneği, AdventureWorks veritabanındaki `nvarchar(max)` Belge tablosundaki bir sütun olan DocumentSummary'de kısmi bir değeri güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="724a9-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="724a9-157">'Bileşenler' sözcüğü, değiştirilen sözcük, varolan verilerde değiştirilecek sözcüğün başlangıç konumu (mahsup) ve değiştirilecek karakter sayısı (uzunluk) belirtilerek 'özellikler' sözcüğü yle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="724a9-158">Örnek, sonuçları karşılaştırmak için UPDATE deyiminden önce ve sonra SELECT deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="724a9-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="724a9-159">ADO.NET Büyük Değer Türleri ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="724a9-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="724a9-160">ADO.NET'da büyük değer türleri ile bir sonuç <xref:System.Data.SqlClient.SqlParameter> kümesini döndürmek <xref:System.Data.SqlClient.SqlDataReader> için büyük değer türlerini <xref:System.Data.SqlClient.SqlDataAdapter> nesneler olarak `DataSet` / `DataTable`belirterek veya bir .</span><span class="sxs-lookup"><span data-stu-id="724a9-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="724a9-161">Büyük bir değer türüyle çalışma şekliniz ile ilgili, daha küçük değer veri türü arasında hiçbir fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="724a9-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="724a9-162">Veri Almak için GetSqlBytes kullanma</span><span class="sxs-lookup"><span data-stu-id="724a9-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="724a9-163"><xref:System.Data.SqlClient.SqlDataReader> Yöntem bir `varbinary(max)` `GetSqlBytes` sütunun içeriğini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="724a9-164">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> bir `cmd` tablodan `varbinary(max)` veri seçen adlı <xref:System.Data.SqlClient.SqlDataReader> bir `reader` nesneyi ve verileri <xref:System.Data.SqlTypes.SqlBytes>. olarak alan adlı bir nesneyi varsayar</span><span class="sxs-lookup"><span data-stu-id="724a9-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="724a9-165">Veri Almak için GetSqlChars kullanma</span><span class="sxs-lookup"><span data-stu-id="724a9-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="724a9-166">Yöntem, `GetSqlChars` bir `varchar(max)` veya `nvarchar(max)` sütunun içeriğini almak için kullanılabilir. <xref:System.Data.SqlClient.SqlDataReader></span><span class="sxs-lookup"><span data-stu-id="724a9-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="724a9-167">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> bir `cmd` tablodan `nvarchar(max)` veri seçen adlandırılmış <xref:System.Data.SqlClient.SqlDataReader> bir `reader` nesneyi ve verileri alan adlı bir nesneyi varsayar.</span><span class="sxs-lookup"><span data-stu-id="724a9-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="724a9-168">Veri Almak için GetSqlBinary kullanma</span><span class="sxs-lookup"><span data-stu-id="724a9-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="724a9-169">Bir `GetSqlBinary` `varbinary(max)` sütunun <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için bir yöntem kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="724a9-170">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> bir `cmd` tablodan `varbinary(max)` veri seçen adlandırılmış <xref:System.Data.SqlClient.SqlDataReader> bir `reader` nesneyi ve verileri <xref:System.Data.SqlTypes.SqlBinary> akış olarak alan adlı bir nesneyi varsayar.</span><span class="sxs-lookup"><span data-stu-id="724a9-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="724a9-171">Veri Almak için GetBytekullanma</span><span class="sxs-lookup"><span data-stu-id="724a9-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="724a9-172">Bir `GetBytes` yöntem, <xref:System.Data.SqlClient.SqlDataReader> belirtilen sütun ofset bir bayt akışı okur belirtilen dizi ofset başlayan bir bayt dizi.</span><span class="sxs-lookup"><span data-stu-id="724a9-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="724a9-173">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> bayt `reader` dizisini alan adlandırılmış bir nesneyi varsayar.</span><span class="sxs-lookup"><span data-stu-id="724a9-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="724a9-174">Aksine, `GetSqlBytes` `GetBytes` dizi arabelleği için bir boyut gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="724a9-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="724a9-175">Veri Almak için GetValue'i kullanma</span><span class="sxs-lookup"><span data-stu-id="724a9-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="724a9-176">Bir `GetValue` <xref:System.Data.SqlClient.SqlDataReader> yöntem, belirtilen sütun ofset bir dizi içine değeri okur.</span><span class="sxs-lookup"><span data-stu-id="724a9-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="724a9-177">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> ilk `reader` sütun ofsetinden ikili veri alan ve ardından ikinci sütun ofsetinden veri dizen adlı bir nesneyi varsayar.</span><span class="sxs-lookup"><span data-stu-id="724a9-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="724a9-178">Büyük Değer Türlerinden CLR Türlerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="724a9-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="724a9-179">Bir `varchar(max)` veya `nvarchar(max)` sütunun içeriğini dize dönüştürme yöntemlerinden herhangi `ToString`birini kullanarak dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="724a9-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="724a9-180">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> verileri `reader` alan adlı bir nesneyi varsayar.</span><span class="sxs-lookup"><span data-stu-id="724a9-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="724a9-181">Örnek</span><span class="sxs-lookup"><span data-stu-id="724a9-181">Example</span></span>  
 <span data-ttu-id="724a9-182">Aşağıdaki kod, `LargePhoto` `ProductPhoto` `AdventureWorks` veritabanındaki tablodan adı ve nesneyi alır ve bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="724a9-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="724a9-183">Derlemenin <xref:System.Drawing> ad alanına bir başvuruyla derlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="724a9-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="724a9-184">Bir <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> `Stream` özelliği <xref:System.Data.SqlClient.SqlDataReader> ortaya <xref:System.Data.SqlTypes.SqlBytes> çıkaran bir nesneyi döndürür yöntemi.</span><span class="sxs-lookup"><span data-stu-id="724a9-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="724a9-185">Kod bunu yeni `Bitmap` bir nesne oluşturmak için kullanır ve sonra `ImageFormat`Gif'e kaydeder.</span><span class="sxs-lookup"><span data-stu-id="724a9-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="724a9-186">Büyük Değer Türü Parametrelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="724a9-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="724a9-187">Büyük değer türleri, <xref:System.Data.SqlClient.SqlParameter> nesnelerde daha küçük değer türlerini <xref:System.Data.SqlClient.SqlParameter> kullandığınız gibi nesnelerde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="724a9-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="724a9-188">Aşağıdaki örnekte gösterildiği <xref:System.Data.SqlClient.SqlParameter> gibi, büyük değer türlerini değer olarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="724a9-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="724a9-189">Kod, AdventureWorks örnek veritabanında aşağıdaki GetDocumentSummary depolanan yordamın var olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="724a9-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="724a9-190">Depolanan yordam, adlı @DocumentID bir giriş parametresi alır ve @DocumentSummary çıkış parametresinde DocumentSummary sütununun içeriğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="724a9-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="724a9-191">Örnek</span><span class="sxs-lookup"><span data-stu-id="724a9-191">Example</span></span>  
 <span data-ttu-id="724a9-192">ADO.NET kodu, <xref:System.Data.SqlClient.SqlConnection> GetDocumentSummary depolanan yordamı yürütmek ve büyük bir değer türü olarak depolanan belge özetini almak için oluşturur ve <xref:System.Data.SqlClient.SqlCommand> nesneler.</span><span class="sxs-lookup"><span data-stu-id="724a9-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="724a9-193">Kod giriş parametresi @DocumentID için bir değer geçirir ve Konsol @DocumentSummary penceresindeçıktı parametresinde geçirilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="724a9-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="724a9-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="724a9-194">See also</span></span>

- [<span data-ttu-id="724a9-195">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="724a9-195">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="724a9-196">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="724a9-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="724a9-197">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="724a9-197">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="724a9-198">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="724a9-198">ADO.NET Overview</span></span>](../ado-net-overview.md)
