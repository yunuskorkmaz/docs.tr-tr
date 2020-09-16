---
title: Büyük değer (max) verilerini değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 8a077c56f4de5a88e9c2a6f932c9a8b5ffc6b974
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556973"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="dda9e-102">ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="dda9e-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="dda9e-103">Büyük nesne (LOB) veri türleri, 8 kilobayt (KB) olan en büyük satır boyutunu aşacak olanlardır.</span><span class="sxs-lookup"><span data-stu-id="dda9e-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="dda9e-104">SQL Server,, `max` `varchar` `nvarchar` ve veri türleri için, `varbinary` 2 ^ 32 bayt kadar büyük değerler depolamaya izin vermek için bir tanımlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dda9e-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="dda9e-105">Tablo sütunları ve Transact-SQL değişkenleri `varchar(max)` , `nvarchar(max)` veya `varbinary(max)` veri türlerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="dda9e-106">ADO.NET ' de, `max` veri türleri bir tarafından getirilebilir `DataReader` ve özel bir işleme olmadan hem giriş hem de çıkış parametre değerleri olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="dda9e-107">Büyük `varchar` veri türleri için veriler artımlı olarak alınabilir ve güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="dda9e-108">`max`Veri türleri, karşılaştırmalar Için Transact-SQL değişkenleri olarak ve birleştirme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="dda9e-109">Ayrıca, bir SELECT ifadesinin yanı sıra toplamaların, birleşimlerin ve alt sorgularda DISTINCT, ORDER BY, GROUP BY yan tümcelerinde de kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="dda9e-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="dda9e-110">Aşağıdaki tabloda SQL Server Books Online 'daki belgelerin bağlantıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="dda9e-111">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="dda9e-111">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="dda9e-112">[Büyük değer veri türlerini kullanma](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="dda9e-112">[Using Large-Value Data Types](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="dda9e-113">Büyük değer türü kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="dda9e-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="dda9e-114">Aşağıdaki kısıtlamalar `max` , daha küçük veri türleri için mevcut olmayan veri türleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="dda9e-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="dda9e-115">`sql_variant`, Büyük bir `varchar` veri türü içeremez.</span><span class="sxs-lookup"><span data-stu-id="dda9e-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="dda9e-116">Büyük `varchar` sütunlar, bir dizinde anahtar sütun olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="dda9e-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="dda9e-117">Bunlar, kümelenmemiş bir dizinde içerilen bir sütunda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="dda9e-118">Büyük `varchar` sütunlar bölümlendirme anahtar sütunları olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dda9e-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="dda9e-119">Transact-SQL ' de büyük değer türleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="dda9e-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="dda9e-120">Transact-SQL `OPENROWSET` işlevi, uzak verilere bağlanmak ve bu verilere erişmek için tek seferlik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="dda9e-121">Bir OLE DB veri kaynağından uzak verilere erişmek için gereken tüm bağlantı bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="dda9e-122">`OPENROWSET` bir sorgunun FROM yan tümcesinde tablo adı gibi bir sorgu oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="dda9e-123">Ayrıca, bir INSERT, UPDATE veya DELETE deyimlerinin hedef tablosu olarak, OLE DB sağlayıcının özelliklerine tabi olabilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="dda9e-124">`OPENROWSET`İşlevi, `BULK` verileri bir hedef tabloya yüklemeden doğrudan bir dosyadan okumanıza olanak sağlayan satır kümesi sağlayıcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="dda9e-125">Bu, `OPENROWSET` Basit BIR INSERT SELECT ifadesinde kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="dda9e-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="dda9e-126">`OPENROWSET BULK`Seçenek bağımsız değişkenleri, verilerin okunması ve bitmesi, hatalarla ilgilenme ve verilerin nasıl yorumlanacağı konusunda önemli bir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="dda9e-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="dda9e-127">Örneğin, veri dosyasının, veya türünde tek satırlık, tek sütunlu satır kümesi olarak okunacağını belirtebilirsiniz `varbinary` `varchar` `nvarchar` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="dda9e-128">Tüm sözdizimi ve seçenekler için bkz. Books Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dda9e-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="dda9e-129">Aşağıdaki örnek, AdventureWorks örnek veritabanındaki ProductPhoto tablosuna bir fotoğraf ekler.</span><span class="sxs-lookup"><span data-stu-id="dda9e-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="dda9e-130">`BULK OPENROWSET`Sağlayıcıyı kullanırken, her sütuna değer yerleştirmeseniz bile adlandırılmış sütun listesini sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="dda9e-131">Bu örnekte birincil anahtar bir kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="dda9e-132">Ayrıca, bu örnekte ThumbnailPhoto olan deyimin sonunda bir bağıntı adı belirtmeniz gerektiğini unutmayın `OPENROWSET` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="dda9e-133">Bu, `ProductPhoto` dosyanın yüklendiği tablodaki sütunuyla ilişkili olur.</span><span class="sxs-lookup"><span data-stu-id="dda9e-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
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
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="dda9e-134">GÜNCELLEŞTIRME kullanılarak veriler güncelleştiriliyor. YAZARKEN</span><span class="sxs-lookup"><span data-stu-id="dda9e-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="dda9e-135">Transact-SQL UPDATE bildiriminde,, veya sütunlarının içeriğini değiştirmek için yeni yazma sözdizimi `varchar(max)` vardır `nvarchar(max)` `varbinary(max)` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="dda9e-136">Bu, verilerin kısmi güncelleştirmelerini gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dda9e-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="dda9e-137">GÜNCELLEŞTIRME. WRITE söz dizimi kısaltılmış biçimde gösteriliyor:</span><span class="sxs-lookup"><span data-stu-id="dda9e-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="dda9e-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="dda9e-138">UPDATE</span></span>  
  
 <span data-ttu-id="dda9e-139">{ *\<object>* }</span><span class="sxs-lookup"><span data-stu-id="dda9e-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="dda9e-140">SET</span><span class="sxs-lookup"><span data-stu-id="dda9e-140">SET</span></span>  
  
 <span data-ttu-id="dda9e-141">{ *column_name* = {. YAZMA ( *ifade* , @Offset , @Length )}</span><span class="sxs-lookup"><span data-stu-id="dda9e-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="dda9e-142">WRITE yöntemi, *column_name* değerinin bir bölümünün değiştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="dda9e-143">İfade, *column_name*kopyalanacak değerdir, `@Offset` ifadenin yazılacağı başlangıç noktasıdır ve `@Length` bağımsız değişken, sütundaki bölümün uzunluğudur ve bağımsız değişkeni, sütununda bulunan bölümdür.</span><span class="sxs-lookup"><span data-stu-id="dda9e-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="dda9e-144">Eğer</span><span class="sxs-lookup"><span data-stu-id="dda9e-144">If</span></span>|<span data-ttu-id="dda9e-145">Ardından</span><span class="sxs-lookup"><span data-stu-id="dda9e-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="dda9e-146">İfade NULL olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="dda9e-146">The expression is set to NULL</span></span>|<span data-ttu-id="dda9e-147">`@Length` yok sayılır ve *column_name* değeri belirtilen şekilde kesilir `@Offset` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="dda9e-148">`@Offset` NULL</span><span class="sxs-lookup"><span data-stu-id="dda9e-148">`@Offset` is NULL</span></span>|<span data-ttu-id="dda9e-149">Güncelleştirme işlemi, ifadeyi varolan *column_name* değerinin sonuna ekler ve `@Length` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dda9e-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="dda9e-150">`@Offset` column_name değerinin uzunluğundan büyük</span><span class="sxs-lookup"><span data-stu-id="dda9e-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="dda9e-151">SQL Server bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="dda9e-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="dda9e-152">`@Length` NULL</span><span class="sxs-lookup"><span data-stu-id="dda9e-152">`@Length` is NULL</span></span>|<span data-ttu-id="dda9e-153">Güncelleştirme işlemi, tüm verileri içinden `@Offset` değeri sonuna kaldırır `column_name` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="dda9e-154">Ne `@Offset` de `@Length` negatif bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dda9e-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="dda9e-155">Example</span></span>  
 <span data-ttu-id="dda9e-156">Bu Transact-SQL örneği, `nvarchar(max)` AdventureWorks veritabanındaki belge tablosundaki bir sütun olan DocumentSummary içindeki kısmi bir değeri günceller.</span><span class="sxs-lookup"><span data-stu-id="dda9e-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="dda9e-157">"Bileşenler" sözcüğünün yerini, var olan verilerde değiştirilecek sözcüğün başlangıç konumunu (kaydır) ve değiştirilecek karakter sayısını (uzunluk) belirterek ' Özellikler ' sözcüğü ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="dda9e-158">Örnek, sonuçları karşılaştırmak için UPDATE deyiminden önce ve sonra SELECT deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dda9e-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="dda9e-159">ADO.NET 'de büyük değerli türlerle çalışma</span><span class="sxs-lookup"><span data-stu-id="dda9e-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="dda9e-160">Büyük değer türlerini <xref:System.Data.SqlClient.SqlParameter> bir sonuç kümesi döndürmek için bir içinde nesne olarak belirterek veya bir öğesini dolduracak şekilde kullanarak ADO.NET içinde büyük değer türleriyle çalışabilirsiniz <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataAdapter> `DataSet` / `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="dda9e-161">Büyük bir değer türü ve ilgili, daha küçük değer veri türü ile çalışma şekli arasında fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="dda9e-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="dda9e-162">Verileri almak için GetSqlBytes kullanma</span><span class="sxs-lookup"><span data-stu-id="dda9e-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="dda9e-163">`GetSqlBytes`Öğesinin yöntemi <xref:System.Data.SqlClient.SqlDataReader> bir sütunun içeriğini almak için kullanılabilir `varbinary(max)` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="dda9e-164">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> `cmd` bir tablodan veri seçen adlı bir nesne `varbinary(max)` ve <xref:System.Data.SqlClient.SqlDataReader> verileri olarak alan adlı bir nesne olduğunu varsayar `reader` <xref:System.Data.SqlTypes.SqlBytes> .</span><span class="sxs-lookup"><span data-stu-id="dda9e-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="dda9e-165">Verileri almak için GetSqlChars kullanma</span><span class="sxs-lookup"><span data-stu-id="dda9e-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="dda9e-166">`GetSqlChars`Yöntemi <xref:System.Data.SqlClient.SqlDataReader> bir veya sütununun içeriğini almak için kullanılabilir `varchar(max)` `nvarchar(max)` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="dda9e-167">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> `cmd` bir tablodan verileri seçen adlı bir `nvarchar(max)` nesne ve verileri alan adlı bir <xref:System.Data.SqlClient.SqlDataReader> nesne olduğunu varsayar `reader` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="dda9e-168">Verileri almak için GetSqlBinary kullanma</span><span class="sxs-lookup"><span data-stu-id="dda9e-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="dda9e-169">`GetSqlBinary`Bir <xref:System.Data.SqlClient.SqlDataReader> sütunun içeriğini almak için, bir yöntemi kullanılabilir `varbinary(max)` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="dda9e-170">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> `cmd` bir tablodan veri seçen adlı bir nesne `varbinary(max)` ve <xref:System.Data.SqlClient.SqlDataReader> `reader` verileri akış olarak alan adlı bir nesne olarak varsayar <xref:System.Data.SqlTypes.SqlBinary> .</span><span class="sxs-lookup"><span data-stu-id="dda9e-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="dda9e-171">Verileri almak için GetBytes kullanma</span><span class="sxs-lookup"><span data-stu-id="dda9e-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="dda9e-172">`GetBytes`Bir a yöntemi belirtilen <xref:System.Data.SqlClient.SqlDataReader> sütundan bir bayt akışını belirtilen dizi uzaklığında başlayarak bir bayt dizisine okur.</span><span class="sxs-lookup"><span data-stu-id="dda9e-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="dda9e-173">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> `reader` bayt dizisine bayt alan adlı bir nesne olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="dda9e-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="dda9e-174">Öğesinin aksine, `GetSqlBytes` `GetBytes` dizi arabelleği için bir boyut gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dda9e-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="dda9e-175">Verileri almak için GetValue 'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="dda9e-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="dda9e-176">`GetValue`Bir öğesinin yöntemi, <xref:System.Data.SqlClient.SqlDataReader> belirtilen sütun içindeki değeri bir diziye okur.</span><span class="sxs-lookup"><span data-stu-id="dda9e-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="dda9e-177">Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> `reader` ilk sütun kaydırından ikili verileri alan adlı bir nesneyi ve sonra ikinci sütun kaydırından dize verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="dda9e-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="dda9e-178">Büyük değer türlerinden CLR türlerine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dda9e-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="dda9e-179">Bir `varchar(max)` veya `nvarchar(max)` sütununun içeriğini, gibi dize dönüştürme yöntemlerinden herhangi birini kullanarak dönüştürebilirsiniz `ToString` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="dda9e-180">Aşağıdaki kod parçası, verileri alan <xref:System.Data.SqlClient.SqlDataReader> adlı bir nesnenin olduğunu varsayar `reader` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="dda9e-181">Örnek</span><span class="sxs-lookup"><span data-stu-id="dda9e-181">Example</span></span>  
 <span data-ttu-id="dda9e-182">Aşağıdaki kod, `LargePhoto` veritabanındaki tablodaki adı ve nesneyi alır `ProductPhoto` `AdventureWorks` ve bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="dda9e-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="dda9e-183">Derlemenin ad alanı başvurusuyla derlenmesi gerekir <xref:System.Drawing> .</span><span class="sxs-lookup"><span data-stu-id="dda9e-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="dda9e-184"><xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>Öğesinin yöntemi, <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlTypes.SqlBytes> bir özelliği kullanıma sunan bir nesne döndürür `Stream` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="dda9e-185">Kod bunu, yeni bir nesne oluşturmak için kullanır `Bitmap` ve ardından gif öğesine kaydeder `ImageFormat` .</span><span class="sxs-lookup"><span data-stu-id="dda9e-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="dda9e-186">Büyük değer türü parametrelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="dda9e-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="dda9e-187">Büyük değer türleri nesnelerde <xref:System.Data.SqlClient.SqlParameter> , nesnelerde daha küçük değer türlerini kullandığınız şekilde de kullanılabilir <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="dda9e-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="dda9e-188"><xref:System.Data.SqlClient.SqlParameter>Aşağıdaki örnekte gösterildiği gibi büyük değer türlerini değer olarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dda9e-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="dda9e-189">Kod, AdventureWorks örnek veritabanında aşağıdaki GetDocumentSummary saklı yordamının bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="dda9e-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="dda9e-190">Saklı yordam adlı bir giriş parametresi alır @DocumentID ve çıkış parametresindeki DocumentSummary sütununun içeriğini döndürür @DocumentSummary .</span><span class="sxs-lookup"><span data-stu-id="dda9e-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="dda9e-191">Örnek</span><span class="sxs-lookup"><span data-stu-id="dda9e-191">Example</span></span>  
 <span data-ttu-id="dda9e-192">ADO.NET kodu, <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlCommand> GetDocumentSummary saklı yordamını yürütmek ve büyük bir değer türü olarak depolanan belge özetini almak için nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dda9e-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="dda9e-193">Kod, giriş parametresi için bir değer geçirir @DocumentID ve @DocumentSummary konsol penceresinde çıkış parametresine geri geçirilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dda9e-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dda9e-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dda9e-194">See also</span></span>

- [<span data-ttu-id="dda9e-195">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="dda9e-195">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="dda9e-196">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="dda9e-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="dda9e-197">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dda9e-197">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="dda9e-198">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dda9e-198">ADO.NET Overview</span></span>](../ado-net-overview.md)
