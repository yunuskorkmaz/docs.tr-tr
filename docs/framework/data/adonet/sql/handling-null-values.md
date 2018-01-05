---
title: "Boş değerler işleme"
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
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8467d1748cec216c01756049d889ea29f02c3c7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-null-values"></a><span data-ttu-id="6f48e-102">Boş değerler işleme</span><span class="sxs-lookup"><span data-stu-id="6f48e-102">Handling Null Values</span></span>
<span data-ttu-id="6f48e-103">Bir sütundaki değeri bilinmeyen ya da eksik olduğunda ilişkisel bir veritabanındaki bir null değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-103">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="6f48e-104">Bir null, boş bir dize (karakter veya tarih/saat veri türleri) ne (sayısal veri türleri için) sıfır değeri olur.</span><span class="sxs-lookup"><span data-stu-id="6f48e-104">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="6f48e-105">Böylece tüm null değerlere tutarlı bir şekilde işlenir ANSI SQL-92 belirtimi null tüm veri türleri için aynı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f48e-105">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="6f48e-106"><xref:System.Data.SqlTypes> Ad alanı uygulayarak null semantiği sağlar <xref:System.Data.SqlTypes.INullable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6f48e-106">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="6f48e-107">Her veri türlerini <xref:System.Data.SqlTypes> kendi `IsNull` özelliği ve `Null` bu veri türünün bir örneğine atanan değer.</span><span class="sxs-lookup"><span data-stu-id="6f48e-107">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f48e-108">Temel alınan türü tüm değerleri temsil etmek için bir değer türü genişletmek programcıları izin boş değer atanabilir türler için .NET Framework 2.0 sürümünde sunulan desteği.</span><span class="sxs-lookup"><span data-stu-id="6f48e-108">The .NET Framework version 2.0 introduced support for nullable types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="6f48e-109">Bu CLR boş değer atanabilir türler örneği temsil eden <xref:System.Nullable> yapısı.</span><span class="sxs-lookup"><span data-stu-id="6f48e-109">These CLR nullable types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="6f48e-110">Nesne türleri ile uyumluluk türleri Kutulu ve, yürütmeyi sarmalanmamış değeri Gelişmiş olduğunda bu beceri özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="6f48e-110">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="6f48e-111">CLR boş değer atanabilir türler belirtmezseniz veritabanı null değerlere depolama için bir ANSI SQL null aynı şekilde davranır değil çünkü bir `null` başvurusu (veya `Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="6f48e-111">CLR nullable types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="6f48e-112">Veritabanı ANSI SQL null değerler ile çalışmak için kullanmak <xref:System.Data.SqlTypes> null değerlere yerine <xref:System.Nullable>.</span><span class="sxs-lookup"><span data-stu-id="6f48e-112">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="6f48e-113">CLR ile çalışma hakkında daha fazla bilgi için bkz: Visual Basic'te boş değer atanabilir türleri [boş değer atanabilir değer türlerinin](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)ve C# bakın [kullanarak boş değer atanabilir türler](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="6f48e-113">For more information on working with CLR nullable types in Visual Basic see [Nullable Value Types](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Using Nullable Types](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="6f48e-114">Null değerler ve üç değerli mantığı</span><span class="sxs-lookup"><span data-stu-id="6f48e-114">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="6f48e-115">Sütun tanımlarında null değerlere izin veren üç değerli mantığı uygulamanıza tanıtır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-115">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="6f48e-116">Bir karşılaştırma üç koşullardan biri değerlendirilebilir:</span><span class="sxs-lookup"><span data-stu-id="6f48e-116">A comparison can evaluate to one of three conditions:</span></span>  
  
-   <span data-ttu-id="6f48e-117">Doğru</span><span class="sxs-lookup"><span data-stu-id="6f48e-117">True</span></span>  
  
-   <span data-ttu-id="6f48e-118">False</span><span class="sxs-lookup"><span data-stu-id="6f48e-118">False</span></span>  
  
-   <span data-ttu-id="6f48e-119">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="6f48e-119">Unknown</span></span>  
  
 <span data-ttu-id="6f48e-120">Null bilinmeyen olarak kabul edilir çünkü birbirlerine Karşılaştırılan iki null değerleri eşit dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="6f48e-120">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="6f48e-121">İşlenen hiçbirinde null ise aritmetik işleçler kullanarak da ifadeler de null sonucudur.</span><span class="sxs-lookup"><span data-stu-id="6f48e-121">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="6f48e-122">Null değerler ve SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="6f48e-122">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="6f48e-123">Herhangi bir karşılaştırması <xref:System.Data.SqlTypes> döndürülecek bir <xref:System.Data.SqlTypes.SqlBoolean>.</span><span class="sxs-lookup"><span data-stu-id="6f48e-123">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="6f48e-124">`IsNull` İşlevi her `SqlType` döndüren bir <xref:System.Data.SqlTypes.SqlBoolean> ve null değerler için denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f48e-124">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="6f48e-125">Aşağıdaki gerçekte Göster nasıl tabloları ve OR ve NOT işleçleri işlevi null değeri varlığında.</span><span class="sxs-lookup"><span data-stu-id="6f48e-125">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="6f48e-126">(T = true, F = false ve U = bilinmeyen ya da null.)</span><span class="sxs-lookup"><span data-stu-id="6f48e-126">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="6f48e-127">![Doğru tablosu](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="6f48e-127">![Truth Table](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansinulls-option"></a><span data-ttu-id="6f48e-128">ANSI_NULLS seçeneği anlama</span><span class="sxs-lookup"><span data-stu-id="6f48e-128">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="6f48e-129"><xref:System.Data.SqlTypes>ANSI_NULLS seçeneği açık SQL Server'da ayarlandığında olarak aynı semantiği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f48e-129"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="6f48e-130">Tüm aritmetik işleçler (+, -, *, /, %), bit düzeyinde işleçler (~ &, &#124;), ve çoğu işlevler işlenen veya bağımsız değişkenler hariç özelliği null ise null döndürür `IsNull`.</span><span class="sxs-lookup"><span data-stu-id="6f48e-130">All arithmetic operators (+, -, *, /, %), bitwise operators (~, &, &#124;), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="6f48e-131">ANSI SQL-92 standart desteklemediği *columnName* WHERE yan tümcesinde = NULL.</span><span class="sxs-lookup"><span data-stu-id="6f48e-131">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="6f48e-132">SQL Server'da ANSI_NULLS seçeneği hem varsayılan NULL atanabilirlik veritabanı ve değerlendirme karşılaştırma null değerler karşı denetler.</span><span class="sxs-lookup"><span data-stu-id="6f48e-132">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="6f48e-133">ANSI_NULLS (varsayılan) etkinleştirdiyseniz, IS NULL işleci için null değerler sınarken ifadelerinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-133">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="6f48e-134">Örneğin, ANSI_NULLS açık olduğunda aşağıdaki karşılaştırmaya her zaman bilinmeyen verir:</span><span class="sxs-lookup"><span data-stu-id="6f48e-134">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```  
colname > NULL  
```  
  
 <span data-ttu-id="6f48e-135">Bir null değeri de içeren bir değişken karşılaştırma bilinmeyen verir:</span><span class="sxs-lookup"><span data-stu-id="6f48e-135">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```  
colname > @MyVariable  
```  
  
 <span data-ttu-id="6f48e-136">IS NULL veya IS NOT NULL karşılaştırma için bir null değer sınamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f48e-136">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="6f48e-137">WHERE yan tümcesine bu karmaşıklık ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f48e-137">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="6f48e-138">Örneğin, AdventureWorks Müşteri tablosundaki TerritoryID sütunu null değerlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="6f48e-138">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="6f48e-139">Bir SELECT deyimi, diğerlerinin yanı sıra null değerler için test etmek için ise, boş bir koşulu şunları içermelidir:</span><span class="sxs-lookup"><span data-stu-id="6f48e-139">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="6f48e-140">ANSI_NULLS SQL Server ayarlarsanız, null karşılaştırma için eşitlik işleci kullanan ifadeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f48e-140">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="6f48e-141">Ancak, bu bağlantı için null seçeneklerini ayarlama farklı bağlantıların engelleyemez.</span><span class="sxs-lookup"><span data-stu-id="6f48e-141">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="6f48e-142">Null değerler için her zaman bağlantı ANSI_NULLS ayarlarına bakılmaksızın works sınamak için IS NULL kullanma.</span><span class="sxs-lookup"><span data-stu-id="6f48e-142">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="6f48e-143">Ayarını devre dışı ANSI_NULLS desteklenmez bir `DataSet`, hangi her zaman uyar null değerleri işlemek için ANSI SQL-92 standart <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="6f48e-143">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="6f48e-144">Null değerler atama</span><span class="sxs-lookup"><span data-stu-id="6f48e-144">Assigning Null Values</span></span>  
 <span data-ttu-id="6f48e-145">Null değerler özel ve kendi depolama ve atama semantiği farklı türde sistemleri ve depolama sistemlerini arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f48e-145">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="6f48e-146">A `Dataset` farklı türü ve depolama sistemlerini ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-146">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="6f48e-147">Bu bölüm için null değerler atama için null semantiğini açıklar bir <xref:System.Data.DataColumn> içinde bir <xref:System.Data.DataRow> farklı sistemler arasında.</span><span class="sxs-lookup"><span data-stu-id="6f48e-147">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="6f48e-148">Bu atama için geçerli bir `DataColumn` herhangi bir türde.</span><span class="sxs-lookup"><span data-stu-id="6f48e-148">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="6f48e-149">Türü uyguluyorsa `INullable`, `DBNull.Value` uygun kesin türü belirtilmiş Null değeri yüklenen.</span><span class="sxs-lookup"><span data-stu-id="6f48e-149">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="6f48e-150">Tüm <xref:System.Data.SqlTypes> veri türleri uygulayan `INullable`.</span><span class="sxs-lookup"><span data-stu-id="6f48e-150">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="6f48e-151">Sütunun veri türüne örtük atama işleçleri kullanarak kesin türü belirtilmiş null değeri dönüştürülebilir ise atama geçtikleri.</span><span class="sxs-lookup"><span data-stu-id="6f48e-151">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="6f48e-152">Aksi takdirde geçersiz yayın özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f48e-152">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="6f48e-153">'Null' geçerli bir değer ise verilen `DataColumn` veri türü, bunu uygun yüklenen `DbNull.Value` veya `Null` ile ilişkili `INullable` türü (`SqlType.Null`)</span><span class="sxs-lookup"><span data-stu-id="6f48e-153">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="6f48e-154">UDT sütunlar için null değerler her zaman ilişkili türüne göre depolanan `DataColumn`.</span><span class="sxs-lookup"><span data-stu-id="6f48e-154">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="6f48e-155">İle ilişkili bir UDT durumunu göz önünde bulundurun bir `DataColumn` , uygulamıyor `INullable` kendi alt sınıfı değil ancak.</span><span class="sxs-lookup"><span data-stu-id="6f48e-155">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="6f48e-156">Bu durumda, türetilmiş sınıf ile ilişkili kesin türü belirtilmiş bir null değer atanmazsa depolandığı bir türsüz olarak `DbNull.Value`, null depolama her zaman DataColumn nesnesinin veri türüyle tutarlı olduğundan.</span><span class="sxs-lookup"><span data-stu-id="6f48e-156">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f48e-157">`Nullable<T>` Veya <xref:System.Nullable> yapısı şu anda desteklenmez `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="6f48e-157">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="6f48e-158">Birden çok sütun (satır) atama</span><span class="sxs-lookup"><span data-stu-id="6f48e-158">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="6f48e-159">`DataTable.Add`, `DataTable.LoadDataRow`, ya da kabul diğer API'leri bir <xref:System.Data.DataRow.ItemArray%2A> satır eşlenen, 'DataColumn nesnesinin varsayılan değer olarak null' harita.</span><span class="sxs-lookup"><span data-stu-id="6f48e-159">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="6f48e-160">Bir dizi nesnesi içeriyorsa `DbNull.Value` veya kesin türü belirtilmiş karşılığı, yukarıdaki aynı kuralları açıklandığı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-160">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="6f48e-161">Ayrıca, bir örneği için aşağıdaki kurallar geçerli `DataRow.["columnName"]` null atamaları:</span><span class="sxs-lookup"><span data-stu-id="6f48e-161">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1.  <span data-ttu-id="6f48e-162">Varsayılan *varsayılan* değer `DbNull.Value` tümü olduğu uygun kesinlikle kesin türü belirtilmiş null sütunlar null değer belirtilmiş dışında.</span><span class="sxs-lookup"><span data-stu-id="6f48e-162">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2.  <span data-ttu-id="6f48e-163">Null değerler hiçbir zaman XML dosyaları (olduğu gibi "xsi: nil") için serileştirme sırasında yazılır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-163">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3.  <span data-ttu-id="6f48e-164">Varsayılan değerleri dahil olmak üzere tüm null olmayan değerler her zaman XML serileştirirken yazılır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-164">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="6f48e-165">Burada bir null değer (xsi: nil) açık ve varsayılan değer örtük XSD/XML semantiği budur (XML içinde mevcut değil, doğrulama ayrıştırıcı, ilişkili bir XSD şemadan alabilirsiniz varsa).</span><span class="sxs-lookup"><span data-stu-id="6f48e-165">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="6f48e-166">Tersidir için doğru bir `DataTable`: bir null değer örtük ve açık varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6f48e-166">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4.  <span data-ttu-id="6f48e-167">XML girdiden okunan satırlar için tüm eksik sütun değerleri NULL atanır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-167">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="6f48e-168">Kullanılarak oluşturulan satırları <xref:System.Data.DataTable.NewRow%2A> veya benzer yöntemler DataColumn nesnesinin varsayılan değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="6f48e-168">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5.  <span data-ttu-id="6f48e-169"><xref:System.Data.DataRow.IsNull%2A> Yöntemi döndürür `true` her ikisi için de `DbNull.Value` ve `INullable.Null`.</span><span class="sxs-lookup"><span data-stu-id="6f48e-169">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="6f48e-170">Null değerler atama</span><span class="sxs-lookup"><span data-stu-id="6f48e-170">Assigning Null Values</span></span>  
 <span data-ttu-id="6f48e-171">Varsayılan değer herhangi <xref:System.Data.SqlTypes> örneği null.</span><span class="sxs-lookup"><span data-stu-id="6f48e-171">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="6f48e-172">İçinde null değerlere <xref:System.Data.SqlTypes> türüne özgü ve tek bir değer tarafından gibi gösterilemez `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="6f48e-172">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="6f48e-173">Kullanım `IsNull` özelliği için null değerler denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6f48e-173">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="6f48e-174">Null değerler atanabilen bir <xref:System.Data.DataColumn> aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="6f48e-174">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="6f48e-175">Null değerler için doğrudan atayabilir `SqlTypes` bir özel durum harekete olmadan değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="6f48e-175">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f48e-176">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f48e-176">Example</span></span>  
 <span data-ttu-id="6f48e-177">Aşağıdaki kod örneği oluşturur bir <xref:System.Data.DataTable> olarak tanımlanan iki sütunlarla <xref:System.Data.SqlTypes.SqlInt32> ve <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="6f48e-177">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="6f48e-178">Kod bilinen değerlerin bir satır ekler, bir satır null değerler ve ardından dolaşır <xref:System.Data.DataTable>değişkenlere değerler atama ve çıkış konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6f48e-178">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="6f48e-179">Bu örnekte aşağıdaki sonuçları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="6f48e-179">This example displays the following results:</span></span>  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="6f48e-180">Null değerler SqlTypes ve CLR Türleri ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="6f48e-180">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="6f48e-181">Null değerler karşılaştırılırken biçimini arasındaki farkı anlamak önemlidir `Equals` yöntemi null değerlerini değerlendirir <xref:System.Data.SqlTypes> CLR türleriyle çalışma şeklini karşılaştırıldığında.</span><span class="sxs-lookup"><span data-stu-id="6f48e-181">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="6f48e-182">Tüm <xref:System.Data.SqlTypes> `Equals` yöntemleri null değerler değerlendirmesi için veritabanı semantiği kullanın: birini veya ikisini değerleri ise null, null karşılaştırma verir.</span><span class="sxs-lookup"><span data-stu-id="6f48e-182">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="6f48e-183">Diğer taraftan, CLR kullanarak `Equals` iki yöntemi <xref:System.Data.SqlTypes> her ikisi de null olduğunda true sunacak.</span><span class="sxs-lookup"><span data-stu-id="6f48e-183">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="6f48e-184">Bu CLR gibi örnek yöntemi kullanarak arasındaki farkı yansıtır `String.Equals` yöntemi ve statik ve paylaşılan yöntemini kullanarak `SqlString.Equals`.</span><span class="sxs-lookup"><span data-stu-id="6f48e-184">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="6f48e-185">Aşağıdaki örnek, sonuçları farkı gösterir `SqlString.Equals` yöntemi ve `String.Equals` her bir değer çifti null ve boş dizeler çifti geçirildiğinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6f48e-185">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="6f48e-186">Kod şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="6f48e-186">The code produces the following output:</span></span>  
  
```  
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a><span data-ttu-id="6f48e-187">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f48e-187">See Also</span></span>  
 [<span data-ttu-id="6f48e-188">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6f48e-188">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="6f48e-189">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="6f48e-189">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
