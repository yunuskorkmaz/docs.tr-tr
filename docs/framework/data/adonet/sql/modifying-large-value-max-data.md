---
title: ADO.NET içinde büyük değerli (Maks) verileri değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: ea079a0b55dde8df7b3442f3d604b2b6467ba785
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778675"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="e91d2-102">ADO.NET içinde büyük değerli (Maks) verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="e91d2-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="e91d2-103">Büyük nesne (LOB) veri türleri 8 kilobayt (KB) maksimum satır boyutu aşan olanlardır.</span><span class="sxs-lookup"><span data-stu-id="e91d2-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="e91d2-104">SQL Server sağlayan bir `max` tanımlayıcısı için `varchar`, `nvarchar`, ve `varbinary` veri türleri değerlerinin depolama 2 büyüklüğünde izin vermek için ^ 32 bayt.</span><span class="sxs-lookup"><span data-stu-id="e91d2-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="e91d2-105">Tablo sütunları ve Transact-SQL değişkenleri belirtin `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="e91d2-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="e91d2-106">ADO.NET, `max` veri türleri getirilen tarafından bir `DataReader`ve iki giriş ve çıkış parametresi değerleri olmadan herhangi bir özel işleme olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="e91d2-107">İçin büyük `varchar` veri türleri, veriler alınır ve artımlı olarak güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="e91d2-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="e91d2-108">`max` Veri türleri, birleştirme ve karşılaştırma, Transact-SQL değişkenleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="e91d2-109">Bunlar ayrıca DISTINCT, ORDER BY, GROUP BY yan tümcesi SELECT deyiminin toplamalar, birleştirmeler ve alt sorgularda yanı sıra kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="e91d2-110">Aşağıdaki tabloda, SQL Server Books Online belgelerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e91d2-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e91d2-111">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="e91d2-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="e91d2-112">Büyük değerli veri türlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="e91d2-112">Using Large-Value Data Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="e91d2-113">Büyük bir değer türü kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="e91d2-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="e91d2-114">Aşağıdaki kısıtlamalar uygulamak `max` veri türleri, daha küçük veri türleri için mevcut değildir:</span><span class="sxs-lookup"><span data-stu-id="e91d2-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
-   <span data-ttu-id="e91d2-115">A `sql_variant` büyük içeremez `varchar` veri türü.</span><span class="sxs-lookup"><span data-stu-id="e91d2-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
-   <span data-ttu-id="e91d2-116">Büyük `varchar` sütunları dizin anahtar sütunu olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="e91d2-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="e91d2-117">Kümelenmemiş bir dizin içinde bulunan bir sütunda verilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
-   <span data-ttu-id="e91d2-118">Büyük `varchar` sütunları bölümleme anahtar sütunu olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e91d2-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="e91d2-119">Transact-SQL büyük değerli türlerle çalışma</span><span class="sxs-lookup"><span data-stu-id="e91d2-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="e91d2-120">Transact-SQL `OPENROWSET` işlev, bağlanma ve uzak veri erişim tek seferlik bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="e91d2-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="e91d2-121">Tüm bir OLE DB veri kaynağından uzak verilere erişmek gerekli bağlantı bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="e91d2-122">`OPENROWSET` işlevmiş gibi bir tablo adı sorgusunun FROM yan tümcesinde başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="e91d2-123">Ayrıca bir INSERT, UPDATE, hedef tablo olarak başvurulabilir veya silme deyiminin, OLE DB sağlayıcısı yeteneklerini tabidir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="e91d2-124">`OPENROWSET` İşlevi içeren `BULK` satır kümesi sağlayıcısı, bir hedef tabloya veri yüklenirken olmadan doğrudan bir dosyadan veri okumanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="e91d2-125">Bu sayede kullanılacak `OPENROWSET` basit INSERT SELECT deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="e91d2-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="e91d2-126">`OPENROWSET BULK` Seçeneği bağımsız değişkenleri nereden başlamalı ve bitmelidir verileri okuma, hatalarla başa çıkma ve verileri nasıl yorumlanacağını üzerinde önemli denetim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e91d2-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="e91d2-127">Örneğin, veri dosyasındaki bir türü tek satır, tek bir sütun kümesi okunacak belirtebilirsiniz `varbinary`, `varchar`, veya `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="e91d2-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="e91d2-128">Tam sözdizimi ve seçenekleri için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="e91d2-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e91d2-129">Aşağıdaki örnekte, AdventureWorks örnek veritabanındaki ProductPhoto tabloya bir fotoğraf ekler.</span><span class="sxs-lookup"><span data-stu-id="e91d2-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="e91d2-130">Kullanırken `BULK OPENROWSET` sağlayıcısı, sağlaması gerekir sütun bile adlandırılmış listesi değerleri her sütununa ekleme değil ise.</span><span class="sxs-lookup"><span data-stu-id="e91d2-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="e91d2-131">Birincil anahtarı bu durumda kimlik sütunu olarak tanımlanır ve sütun listesinden dahil edilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="e91d2-132">Ayrıca, sonunda bir bağıntı adı sağlamanız gerektiğini unutmayın `OPENROWSET` ThumbnailPhoto bu durumda olan ifade.</span><span class="sxs-lookup"><span data-stu-id="e91d2-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="e91d2-133">Bu sütunda ile ilişkilendiren `ProductPhoto` tablo, dosya yüklenirken içine.</span><span class="sxs-lookup"><span data-stu-id="e91d2-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
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
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="e91d2-134">Güncelleştirme kullanarak verileri güncelleştiriliyor. YAZMA</span><span class="sxs-lookup"><span data-stu-id="e91d2-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="e91d2-135">Transact-SQL UPDATE deyiminin içeriğini değiştirmek için yeni yazma söz dizimine sahip `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` sütunları.</span><span class="sxs-lookup"><span data-stu-id="e91d2-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="e91d2-136">Bu, verileri kısmi güncelleştirmelerin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e91d2-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="e91d2-137">GÜNCELLEŞTİRME. Söz dizimi burada kısaltılmış formunda gösterilen yazma:</span><span class="sxs-lookup"><span data-stu-id="e91d2-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="e91d2-138">GÜNCELLEŞTİR</span><span class="sxs-lookup"><span data-stu-id="e91d2-138">UPDATE</span></span>  
  
 <span data-ttu-id="e91d2-139">{  *\<Nesne >* }</span><span class="sxs-lookup"><span data-stu-id="e91d2-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="e91d2-140">AYARLAYIN</span><span class="sxs-lookup"><span data-stu-id="e91d2-140">SET</span></span>  
  
 <span data-ttu-id="e91d2-141">{ *column_name* = {. YAZMA ( *ifade* , @Offset , @Length )}</span><span class="sxs-lookup"><span data-stu-id="e91d2-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="e91d2-142">YAZMA yönteminin belirten değerinin bir bölümü *column_name* değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="e91d2-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="e91d2-143">İfade kopyalanacağı değerdir *column_name*, `@Offset` başlangıçtan ifade yazılır, başlangıç noktasıdır ve `@Length` bağımsız değişkeni olan sütun bölümde uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e91d2-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="e91d2-144">Eğer</span><span class="sxs-lookup"><span data-stu-id="e91d2-144">If</span></span>|<span data-ttu-id="e91d2-145">Ardından</span><span class="sxs-lookup"><span data-stu-id="e91d2-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="e91d2-146">İfade NULL olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="e91d2-146">The expression is set to NULL</span></span>|<span data-ttu-id="e91d2-147">`@Length` göz ardı edilir ve değer *column_name* kesilmiş belirtilen `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="e91d2-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="e91d2-148">`@Offset` null</span><span class="sxs-lookup"><span data-stu-id="e91d2-148">`@Offset` is NULL</span></span>|<span data-ttu-id="e91d2-149">Güncelleştirme işlemi sonunda varolan ifade ekler *column_name* değeri ve `@Length` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="e91d2-150">`@Offset` column_name değeri uzunluğundan büyüktür</span><span class="sxs-lookup"><span data-stu-id="e91d2-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="e91d2-151">SQL Server bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="e91d2-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="e91d2-152">`@Length` null</span><span class="sxs-lookup"><span data-stu-id="e91d2-152">`@Length` is NULL</span></span>|<span data-ttu-id="e91d2-153">Güncelleştirme işlemi tüm verileri kaldırır `@Offset` sonuna `column_name` değeri.</span><span class="sxs-lookup"><span data-stu-id="e91d2-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e91d2-154">Ne `@Offset` ya da `@Length` negatif bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e91d2-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="e91d2-155">Example</span></span>  
 <span data-ttu-id="e91d2-156">Bu Transact-SQL örnek DocumentSummary, kısmi bir değer güncelleştirmeleri bir `nvarchar(max)` AdventureWorks veritabanını Belge tablosuna sütun.</span><span class="sxs-lookup"><span data-stu-id="e91d2-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="e91d2-157">' % S'sözcük 'Bileşenler' sözcük 'Özellikler' değiştirme metni, mevcut verileri ve değiştirilen (uzunluk) olacak şekilde karakter sayısına göre değiştirilecek Word'ün başlangıç konumunu (kaydırma) belirterek değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="e91d2-158">Örnek, önce ve sonra sonuçları karşılaştırmak için UPDATE deyiminin SELECT deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="e91d2-159">ADO.NET içinde büyük değerli türlerle çalışma</span><span class="sxs-lookup"><span data-stu-id="e91d2-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="e91d2-160">Büyük bir değer türleri olarak belirterek ADO.NET içinde büyük değer türleri ile çalışabilir <xref:System.Data.SqlClient.SqlParameter> nesneler bir <xref:System.Data.SqlClient.SqlDataReader> kullanarak veya kümesinden bir sonuç döndürmek için bir <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için bir `DataSet` / `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="e91d2-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="e91d2-161">Büyük bir değer türüyle çalışma biçiminizi ve ilgili, daha küçük değer veri türü arasında bir fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="e91d2-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="e91d2-162">Veri almak için GetSqlBytes kullanma</span><span class="sxs-lookup"><span data-stu-id="e91d2-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="e91d2-163">`GetSqlBytes` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun.</span><span class="sxs-lookup"><span data-stu-id="e91d2-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="e91d2-164">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodaki verileri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="e91d2-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="e91d2-165">Veri almak için GetSqlChars kullanma</span><span class="sxs-lookup"><span data-stu-id="e91d2-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="e91d2-166">`GetSqlChars` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varchar(max)` veya `nvarchar(max)` sütun.</span><span class="sxs-lookup"><span data-stu-id="e91d2-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="e91d2-167">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `nvarchar(max)` bir tablodaki verileri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , verileri alır.</span><span class="sxs-lookup"><span data-stu-id="e91d2-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="e91d2-168">Veri almak için GetSqlBinary kullanma</span><span class="sxs-lookup"><span data-stu-id="e91d2-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="e91d2-169">`GetSqlBinary` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun.</span><span class="sxs-lookup"><span data-stu-id="e91d2-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="e91d2-170">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodaki verileri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır bir <xref:System.Data.SqlTypes.SqlBinary> akış.</span><span class="sxs-lookup"><span data-stu-id="e91d2-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="e91d2-171">Veri almak için GetBytes kullanma</span><span class="sxs-lookup"><span data-stu-id="e91d2-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="e91d2-172">`GetBytes` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> belirtilen uzaklıkta başlayan belirli bir bayt dizisi olarak belirtilen sütun uzaklığı bayt akışı okur.</span><span class="sxs-lookup"><span data-stu-id="e91d2-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="e91d2-173">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , bayt bayt dizisine alır.</span><span class="sxs-lookup"><span data-stu-id="e91d2-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="e91d2-174">Aksine, Not `GetSqlBytes`, `GetBytes` dizi arabelleği için bir boyut gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e91d2-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="e91d2-175">GetValue veri almak için kullanma</span><span class="sxs-lookup"><span data-stu-id="e91d2-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="e91d2-176">`GetValue` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> değeri belirtilen sütun uzaklığı bir diziye okur.</span><span class="sxs-lookup"><span data-stu-id="e91d2-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="e91d2-177">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` ilk sütun ikili verilerden alır uzaklığı ve ardından verileri ikinci sütun uzaklığı dize.</span><span class="sxs-lookup"><span data-stu-id="e91d2-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="e91d2-178">CLR türlerine büyük değer türlerinden dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e91d2-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="e91d2-179">İçeriğini dönüştürebilirsiniz bir `varchar(max)` veya `nvarchar(max)` gibi dize dönüştürme yöntemlerinden herhangi birini kullanarak sütun `ToString`.</span><span class="sxs-lookup"><span data-stu-id="e91d2-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="e91d2-180">Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , verileri alır.</span><span class="sxs-lookup"><span data-stu-id="e91d2-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="e91d2-181">Örnek</span><span class="sxs-lookup"><span data-stu-id="e91d2-181">Example</span></span>  
 <span data-ttu-id="e91d2-182">Aşağıdaki kod adını alır ve `LargePhoto` nesnesinden `ProductPhoto` tablosundaki `AdventureWorks` veritabanı ve bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e91d2-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="e91d2-183">Derlemeyi bir başvuru ile derlenmesi gerekiyor <xref:System.Drawing> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e91d2-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="e91d2-184"><xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Yöntemi <xref:System.Data.SqlClient.SqlDataReader> döndürür bir <xref:System.Data.SqlTypes.SqlBytes> kullanıma sunan bir nesne bir `Stream` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e91d2-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="e91d2-185">Bu yeni bir kullanan kod `Bitmap` nesne ve sonra GIF kaydeder `ImageFormat`.</span><span class="sxs-lookup"><span data-stu-id="e91d2-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="e91d2-186">Büyük bir değer türü parametrelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="e91d2-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="e91d2-187">Büyük değer türleri kullanılabilir <xref:System.Data.SqlClient.SqlParameter> daha küçük değer kullandığınız aynı şekilde türleri, nesneleri <xref:System.Data.SqlClient.SqlParameter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e91d2-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="e91d2-188">Büyük bir değer türleri olarak alabilir <xref:System.Data.SqlClient.SqlParameter> , aşağıdaki örnekte gösterildiği gibi değerleri.</span><span class="sxs-lookup"><span data-stu-id="e91d2-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="e91d2-189">Kod aşağıdaki GetDocumentSummary depolanan yordamı AdventureWorks örnek veritabanındaki var olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="e91d2-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="e91d2-190">Saklı yordam adlı giriş parametresi alan @DocumentID ve DocumentSummary sütununda içeriğini döndürür @DocumentSummary çıkış parametresi.</span><span class="sxs-lookup"><span data-stu-id="e91d2-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="e91d2-191">Örnek</span><span class="sxs-lookup"><span data-stu-id="e91d2-191">Example</span></span>  
 <span data-ttu-id="e91d2-192">ADO.NET kod oluşturur <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> büyük değer türü olarak depolanan GetDocumentSummary saklı yordamı yürütme ve Özet, belge almak için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e91d2-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="e91d2-193">Kod bir değer geçirir @DocumentID giriş parametresi ve sonuçları geçirilen geri görüntüler @DocumentSummary çıkış parametresi konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="e91d2-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e91d2-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e91d2-194">See Also</span></span>  
 [<span data-ttu-id="e91d2-195">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="e91d2-195">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="e91d2-196">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="e91d2-196">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="e91d2-197">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="e91d2-197">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="e91d2-198">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="e91d2-198">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
