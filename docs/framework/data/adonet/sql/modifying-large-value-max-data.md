---
title: "ADO.NET büyük değer (Maks) verileri değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3a80f316ffc3380408802fefe1a26d71e5e76ac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="2ad10-102">ADO.NET büyük değer (Maks) verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="2ad10-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="2ad10-103">Büyük nesne (LOB) veri türleri 8 kilobayt (KB) en fazla satır boyutunu aşan olanlardır.</span><span class="sxs-lookup"><span data-stu-id="2ad10-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="2ad10-104">SQL Server sağlayan bir `max` tanımlayıcısı için `varchar`, `nvarchar`, ve `varbinary` değerlerin depolama 2 büyüklüğünde izin vermek için veri türleri ^ 32 bayt.</span><span class="sxs-lookup"><span data-stu-id="2ad10-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="2ad10-105">Tablo sütunları ve Transact-SQL değişkenleri belirtebilir `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="2ad10-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="2ad10-106">ADO.NET, `max` veri türleri getirilen tarafından bir `DataReader`ve herhangi bir özel işleme yapılmadan hem giriş ve çıkış parametresi değerleri olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="2ad10-107">İçin büyük `varchar` veri türleri, veri alınır ve artımlı olarak güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="2ad10-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="2ad10-108">`max` Transact-SQL değişkenleri olarak karşılaştırmaları ve birleştirme için veri türleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="2ad10-109">Bunlar, DISTINCT, ORDER BY, GROUP BY yan tümcesi SELECT deyiminin ve aynı zamanda toplamalar, birleştirmeler ve alt sorgular da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="2ad10-110">Aşağıdaki tabloda, SQL Server Books Online'da belgelere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ad10-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="2ad10-111">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="2ad10-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="2ad10-112">Değer büyük veri türlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad10-112">Using Large-Value Data Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="2ad10-113">Büyük değer türü kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="2ad10-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="2ad10-114">Aşağıdaki kısıtlamalar uygulamak `max` daha küçük veri türleri için yok, veri türleri:</span><span class="sxs-lookup"><span data-stu-id="2ad10-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
-   <span data-ttu-id="2ad10-115">A `sql_variant` büyük içeremez `varchar` veri türü.</span><span class="sxs-lookup"><span data-stu-id="2ad10-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
-   <span data-ttu-id="2ad10-116">Büyük `varchar` sütunları, dizinde anahtar sütunu olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="2ad10-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="2ad10-117">Kümelenmemiş bir dizin bulunan bir sütun kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
-   <span data-ttu-id="2ad10-118">Büyük `varchar` sütunlar anahtar sütunlarını bölümleme olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2ad10-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="2ad10-119">Transact-SQL büyük değer türleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="2ad10-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="2ad10-120">Transact-SQL `OPENROWSET` işlevidir bağlanma ve uzak veri erişim tek seferlik bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="2ad10-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="2ad10-121">Tüm bir OLE DB veri kaynağından uzak verilere erişmek gerekli bağlantı bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="2ad10-122">`OPENROWSET`dizinindeymiş gibi bir tablo adı bir sorgu FROM yan tümcesinde başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="2ad10-123">Ayrıca bir INSERT, UPDATE, hedef tablo olarak başvurulabilir veya OLE DB sağlayıcısı yeteneklerine tabi deyimi SİLİN.</span><span class="sxs-lookup"><span data-stu-id="2ad10-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="2ad10-124">`OPENROWSET` İşlevi içeren `BULK` doğrudan bir dosyadan bir hedef tabloya veri yüklemeden okumaya izin veren satır kümesi sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2ad10-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="2ad10-125">Bu kullanmanızı sağlayan `OPENROWSET` basit INSERT SELECT deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="2ad10-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="2ad10-126">`OPENROWSET``BULK` Seçenek bağımsız başlamak ve verileri okuma bitiş konumu, hatalarla ilgilenir etme ve verilerin nasıl yorumlanacağını üzerinde önemli denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ad10-126">The `OPENROWSET``BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="2ad10-127">Örneğin, veri dosyası türü tek satır, tek sütunlu satır okunacak belirtebilirsiniz `varbinary`, `varchar`, veya `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="2ad10-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="2ad10-128">Tam sözdizimi ve seçenekler için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="2ad10-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="2ad10-129">Aşağıdaki örnekte AdventureWorks örnek veritabanını ProductPhoto tabloda bir fotoğraf ekler.</span><span class="sxs-lookup"><span data-stu-id="2ad10-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="2ad10-130">Kullanırken `BULK``OPENROWSET` sağlayıcısı sağlamanız sütunlar bile adlandırılmış listesi değerleri her sütununa ekleme olmayan durumunda.</span><span class="sxs-lookup"><span data-stu-id="2ad10-130">When using the `BULK``OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="2ad10-131">Birincil anahtar bu durumda kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="2ad10-132">Ayrıca, sonunda bir bağıntı adı sağlamanız gerektiğini unutmayın `OPENROWSET` ThumbnailPhoto bu durumda olan ifade.</span><span class="sxs-lookup"><span data-stu-id="2ad10-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="2ad10-133">Bu sütunda ile karşılık gelen `ProductPhoto` tablo hangi dosya yükleniyor içine.</span><span class="sxs-lookup"><span data-stu-id="2ad10-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="2ad10-134">Güncelleştirme kullanarak verileri güncelleştiriliyor. YAZMA</span><span class="sxs-lookup"><span data-stu-id="2ad10-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="2ad10-135">Transact-SQL UPDATE deyiminin içeriğini değiştirmek için yeni yazma sözdizimine sahip `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` sütun.</span><span class="sxs-lookup"><span data-stu-id="2ad10-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="2ad10-136">Bu verilerin kısmi güncelleştirmeler gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ad10-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="2ad10-137">GÜNCELLEŞTİRME. Sözdizimi kısaltılmış formunda burada gösterilen yazma:</span><span class="sxs-lookup"><span data-stu-id="2ad10-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="2ad10-138">GÜNCELLEŞTİR</span><span class="sxs-lookup"><span data-stu-id="2ad10-138">UPDATE</span></span>  
  
 <span data-ttu-id="2ad10-139">{  *\<nesnesi >* }</span><span class="sxs-lookup"><span data-stu-id="2ad10-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="2ad10-140">AYARLAMA</span><span class="sxs-lookup"><span data-stu-id="2ad10-140">SET</span></span>  
  
 <span data-ttu-id="2ad10-141">{ *column_name* = {. YAZMA ( *ifade* , @Offset , @Length )}</span><span class="sxs-lookup"><span data-stu-id="2ad10-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="2ad10-142">WRITE yöntemi belirleyen değerinin bir bölümünü *column_name* değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="2ad10-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="2ad10-143">İfade kopyalanacak değerdir *column_name*, `@Offset` hangi ifade yazılır, başlangıç noktasıdır ve `@Length` bağımsız değişkeni olan sütun bölümünde uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2ad10-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="2ad10-144">Eğer</span><span class="sxs-lookup"><span data-stu-id="2ad10-144">If</span></span>|<span data-ttu-id="2ad10-145">Ardından</span><span class="sxs-lookup"><span data-stu-id="2ad10-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="2ad10-146">İfade NULL olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="2ad10-146">The expression is set to NULL</span></span>|<span data-ttu-id="2ad10-147">`@Length`göz ardı edilir ve değer *column_name* kesilir belirtilen `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="2ad10-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="2ad10-148">`@Offset`NULL.</span><span class="sxs-lookup"><span data-stu-id="2ad10-148">`@Offset` is NULL</span></span>|<span data-ttu-id="2ad10-149">Güncelleştirme işlemi var olan sonunda ifade ekler *column_name* değeri ve `@Length` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="2ad10-150">`@Offset`column_name değeri uzunluğundan daha büyük</span><span class="sxs-lookup"><span data-stu-id="2ad10-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="2ad10-151">SQL Server hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ad10-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="2ad10-152">`@Length`NULL.</span><span class="sxs-lookup"><span data-stu-id="2ad10-152">`@Length` is NULL</span></span>|<span data-ttu-id="2ad10-153">Güncelleştirme işlemi tüm verileri kaldırır `@Offset` sonuna `column_name` değeri.</span><span class="sxs-lookup"><span data-stu-id="2ad10-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2ad10-154">Ne `@Offset` ya da `@Length` negatif bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ad10-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ad10-155">Example</span></span>  
 <span data-ttu-id="2ad10-156">Bu Transact-SQL örneği DocumentSummary, kısmi bir değerinde güncelleştirmeleri bir `nvarchar(max)` AdventureWorks veritabanını belge tablodaki sütun.</span><span class="sxs-lookup"><span data-stu-id="2ad10-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="2ad10-157">Word 'Bileşenleri' sözcük 'Özellikler' değiştirme word, var olan verileri ve değiştirilen (uzunluk) olacak şekilde karakter sayısını değiştirilmesi için Word'ü başlangıç konumunu (uzaklık) belirterek değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="2ad10-158">Örnek önce ve sonra sonuçları karşılaştırmak için UPDATE deyiminin SELECT deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```  
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="2ad10-159">ADO.NET büyük değer türleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="2ad10-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="2ad10-160">ADO.NET büyük değer türlerinde büyük değer türleri olarak belirterek çalışabileceğiniz <xref:System.Data.SqlClient.SqlParameter> nesnelerini bir <xref:System.Data.SqlClient.SqlDataReader> bir sonuç kümesinden veya kullanarak döndürmek için bir <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için bir `DataSet` / `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="2ad10-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="2ad10-161">Büyük değer türü ile çalışmayı yolu ile ilgili, daha küçük değer veri türü arasında fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="2ad10-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="2ad10-162">Veri almak için GetSqlBytes kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad10-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="2ad10-163">`GetSqlBytes` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun.</span><span class="sxs-lookup"><span data-stu-id="2ad10-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="2ad10-164">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodan veri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="2ad10-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="2ad10-165">Veri almak için GetSqlChars kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad10-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="2ad10-166">`GetSqlChars` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varchar(max)` veya `nvarchar(max)` sütun.</span><span class="sxs-lookup"><span data-stu-id="2ad10-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="2ad10-167">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `nvarchar(max)` bir tablodan veri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` verileri alır.</span><span class="sxs-lookup"><span data-stu-id="2ad10-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="2ad10-168">Veri almak için GetSqlBinary kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad10-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="2ad10-169">`GetSqlBinary` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun.</span><span class="sxs-lookup"><span data-stu-id="2ad10-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="2ad10-170">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodan veri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır bir <xref:System.Data.SqlTypes.SqlBinary> akış.</span><span class="sxs-lookup"><span data-stu-id="2ad10-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="2ad10-171">Veri almak için GetBytes kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad10-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="2ad10-172">`GetBytes` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> belirtilen dizi uzaklıkta başlayan bir bayt dizisi halinde belirtilen sütun uzaklığı bayt akışı okur.</span><span class="sxs-lookup"><span data-stu-id="2ad10-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="2ad10-173">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , baytı bir bayt dizisine alır.</span><span class="sxs-lookup"><span data-stu-id="2ad10-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="2ad10-174">Farklı Not `GetSqlBytes`, `GetBytes` dizi arabellek için bir boyut gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2ad10-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="2ad10-175">GetValue veri almak için kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad10-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="2ad10-176">`GetValue` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> değeri belirtilen sütun uzaklığı bir diziye okur.</span><span class="sxs-lookup"><span data-stu-id="2ad10-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="2ad10-177">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` alır ikili verileri ilk sütun uzaklığı ve ikinci sütun uzaklığı verilerden dize.</span><span class="sxs-lookup"><span data-stu-id="2ad10-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="2ad10-178">CLR türleri için büyük değer türlerini dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2ad10-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="2ad10-179">İçeriğini dönüştürebilirsiniz bir `varchar(max)` veya `nvarchar(max)` gibi dize dönüştürme yöntemlerden birini kullanarak sütun `ToString`.</span><span class="sxs-lookup"><span data-stu-id="2ad10-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="2ad10-180">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` verileri alır.</span><span class="sxs-lookup"><span data-stu-id="2ad10-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="2ad10-181">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ad10-181">Example</span></span>  
 <span data-ttu-id="2ad10-182">Aşağıdaki kod adını alır ve `LargePhoto` nesnesinin `ProductPhoto` tablosundaki `AdventureWorks` veritabanı ve bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2ad10-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="2ad10-183">Derleme başvuru derlenmesi gerekiyor <xref:System.Drawing> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2ad10-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="2ad10-184"><xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Yöntemi <xref:System.Data.SqlClient.SqlDataReader> döndüren bir <xref:System.Data.SqlTypes.SqlBytes> gösteren nesne bir `Stream` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2ad10-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="2ad10-185">Bu yeni bir oluşturmak için kodunu kullanır `Bitmap` nesne ve GIF kaydeder `ImageFormat`.</span><span class="sxs-lookup"><span data-stu-id="2ad10-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="2ad10-186">Büyük değer türü parametrelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad10-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="2ad10-187">Büyük değer türleri kullanılabilir <xref:System.Data.SqlClient.SqlParameter> daha küçük olan değeri kullandığınız aynı şekilde türleri nesneleri <xref:System.Data.SqlClient.SqlParameter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2ad10-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="2ad10-188">Büyük değer türleri olarak alabilir <xref:System.Data.SqlClient.SqlParameter> , aşağıdaki örnekte gösterildiği gibi değerler.</span><span class="sxs-lookup"><span data-stu-id="2ad10-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="2ad10-189">Kod GetDocumentSummary saklı yordamını AdventureWorks örnek veritabanında var olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="2ad10-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="2ad10-190">Saklı yordam adlı bir giriş parametresi alan @DocumentID ve DocumentSummary sütununda içeriğini döndürür @DocumentSummary çıkış parametresi.</span><span class="sxs-lookup"><span data-stu-id="2ad10-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```  
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
  
### <a name="example"></a><span data-ttu-id="2ad10-191">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ad10-191">Example</span></span>  
 <span data-ttu-id="2ad10-192">ADO.NET kod oluşturur <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> büyük değer türü olarak depolanan GetDocumentSummary saklı yordamı yürütme ve belge özeti, almak için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2ad10-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="2ad10-193">Bir değer kodu geçirir @DocumentID giriş parametresi ve sonuçları geçirilen geri görüntüler @DocumentSummary çıkış konsol penceresinde parametresi.</span><span class="sxs-lookup"><span data-stu-id="2ad10-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2ad10-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ad10-194">See Also</span></span>  
 [<span data-ttu-id="2ad10-195">SQL Server ikili ve değeri büyük veri</span><span class="sxs-lookup"><span data-stu-id="2ad10-195">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="2ad10-196">SQL Server veri türü eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="2ad10-196">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="2ad10-197">SQL Server veri işlemleri ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2ad10-197">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="2ad10-198">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="2ad10-198">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
