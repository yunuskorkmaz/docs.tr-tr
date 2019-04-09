---
title: SQL-CLR Tür Uyumsuzlukları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 77090a9f22dcf3d55739aa03535bee863793d858
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172893"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="f3d1b-102">SQL-CLR Tür Uyumsuzlukları</span><span class="sxs-lookup"><span data-stu-id="f3d1b-102">SQL-CLR Type Mismatches</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f3d1b-103">nesne modeli ve SQL Server arasındaki çeviriyi çoğunu otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="f3d1b-104">Bununla birlikte, bazı durumlarda, tam çeviri engelleyin.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="f3d1b-105">Aşağıdaki bölümlerde bu anahtar uyuşmazlıklarını ortak dil çalışma zamanı (CLR) türleri ve SQL Server veritabanı türleri özetlenir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="f3d1b-106">Özel tür eşlemeleri ve işlev çeviri sırasında hakkında daha fazla ayrıntı bulabilirsiniz [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) ve [veri türleri ve işlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) and [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f3d1b-107">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f3d1b-107">Data Types</span></span>  
 <span data-ttu-id="f3d1b-108">Çeviri CLR ve SQL Server arasındaki bir sorgu için veritabanı gönderildiğinde ve sonuçları, nesne modeline geri gönderildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="f3d1b-109">Örneğin, aşağıdaki Transact-SQL sorgusunu iki değer dönüştürmeleri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-109">For example, the following Transact-SQL query requires two value conversions:</span></span>  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 <span data-ttu-id="f3d1b-110">SQL Server'da sorgu yürütülmeden önce Transact-SQL parametresi için değer belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="f3d1b-111">Bu örnekte, `id` parametre değeri bir CLR önce çevrilmelidir <xref:System.Int32?displayProperty=nameWithType> türü bir SQL Server'a `INT` veritabanı değeri ne olduğunu anlayabilmeniz yazın.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="f3d1b-112">Sonuçları, SQL Server'ı almak için `DateOfBirth` SQL Server'dan sütunun çevrilmiş `DATETIME` bir CLR türüne <xref:System.DateTime?displayProperty=nameWithType> türü için nesne modeli kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="f3d1b-113">Bu örnekte, SQL Server veritabanı ve CLR nesne modeli türlerinde doğal eşlemelere sahip.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="f3d1b-114">Ancak bu her zaman böyle değildir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-114">But, this is not always the case.</span></span>  
  
### <a name="missing-counterparts"></a><span data-ttu-id="f3d1b-115">Ortaklarınıza eksik</span><span class="sxs-lookup"><span data-stu-id="f3d1b-115">Missing Counterparts</span></span>  
 <span data-ttu-id="f3d1b-116">Aşağıdaki türleri makul ortaklarınıza yok.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-116">The following types do not have reasonable counterparts.</span></span>  
  
-   <span data-ttu-id="f3d1b-117">CLR içinde eşleşmiyor <xref:System> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-117">Mismatches in the CLR <xref:System> namespace:</span></span>  
  
    -   <span data-ttu-id="f3d1b-118">**İşaretsiz tamsayılar**.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-118">**Unsigned integers**.</span></span> <span data-ttu-id="f3d1b-119">Bu türler, genellikle taşması önlemek için imzalı karşılıkları daha büyük boyutta için eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="f3d1b-120">Değişmez değerler, imzalı bir sayısal değere göre aynı veya daha küçük boyutta dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>  
  
    -   <span data-ttu-id="f3d1b-121">**Boole**.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-121">**Boolean**.</span></span> <span data-ttu-id="f3d1b-122">Bu tür bir bit veya daha büyük sayısal ya da dize olarak eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="f3d1b-123">Aynı değer için değerlendirilen bir ifade bir sabit değer eşlenebilir (örneğin, `1=1` için SQL'de `True` CLS içinde).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>  
  
    -   <span data-ttu-id="f3d1b-124">**TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-124">**TimeSpan**.</span></span> <span data-ttu-id="f3d1b-125">Bu tür iki arasındaki farkı temsil eder `DateTime` değerleri ve gelmiyor `timestamp` SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="f3d1b-126">CLR <xref:System.TimeSpan?displayProperty=nameWithType> SQL Server'a da eşleyebilir `TIME` bazı durumlarda türü.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="f3d1b-127">SQL Server `TIME` türü 24 saatten az pozitif değerleri temsil etmek için yalnızca tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="f3d1b-128">CLR <xref:System.TimeSpan> kadar büyük aralığı yok.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3d1b-129">SQL Server'a özgü [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] türlerini <xref:System.Data.SqlTypes> bu Karşılaştırmada dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-129">SQL Server-specific [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>  
  
-   <span data-ttu-id="f3d1b-130">SQL Server'da uyuşmazlığı:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-130">Mismatches in SQL Server:</span></span>  
  
    -   <span data-ttu-id="f3d1b-131">**Karakter türleri uzunluğu sabit**.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-131">**Fixed length character types**.</span></span> <span data-ttu-id="f3d1b-132">Transact-SQL Unicode ve Unicode olmayan kategorilere ayırır ve her kategoride üç ayrı türü vardır: uzunluğu sabit `nchar` / `char`, değişken uzunluğu `nvarchar` / `varchar`, ve daha büyük boyutlu `ntext` / `text`.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="f3d1b-133">Sabit uzunluk karakter türleri için CLR eşleştirilebilir <xref:System.Char?displayProperty=nameWithType> almak için tür karakter, ancak bunlar gerçekten aynı türe dönüştürme ve davranışı karşılık gelmez.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>  
  
    -   <span data-ttu-id="f3d1b-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-134">**Bit**.</span></span> <span data-ttu-id="f3d1b-135">Ancak `bit` etki alanına sahip değer olarak aynı sayıda `Nullable<Boolean>`, iki farklı tür aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> `Bit` <span data-ttu-id="f3d1b-136">değerleri alır `1` ve `0` yerine `true` / `false`, Boolean ifadeler için eşdeğer olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-136">takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>  
  
    -   <span data-ttu-id="f3d1b-137">**Zaman damgası**.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-137">**Timestamp**.</span></span> <span data-ttu-id="f3d1b-138">CLR aksine <xref:System.TimeSpan?displayProperty=nameWithType> türü, SQL Server `TIMESTAMP` türünü temsil eden arasındaki fark temel almaz ve her güncelleştirme için benzersiz olan veritabanı tarafından oluşturulan bir 8-bayt sayısı <xref:System.DateTime> değerleri.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>  
  
    -   <span data-ttu-id="f3d1b-139">**Para** ve **küçük para**.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="f3d1b-140">Bu tür eşlenebilir <xref:System.Decimal> ancak temelde farklı türleri ve bu nedenle, sunucu tabanlı işlevleri ve dönüştürmeler tarafından kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>  
  
### <a name="multiple-mappings"></a><span data-ttu-id="f3d1b-141">Birden çok eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="f3d1b-141">Multiple Mappings</span></span>  
 <span data-ttu-id="f3d1b-142">Bir veya daha fazla CLR veri türleri eşleyebilirsiniz birçok SQL Server veri türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="f3d1b-143">Bir veya daha fazla SQL Server türlerini eşleyebilirsiniz birçok CLR türü vardır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="f3d1b-144">LINQ to SQL ile bir eşleme desteklenmiyor olabilir ancak CLR ve SQL Server arasında eşlenen iki tür kusursuz kesinliği, aralık ve semantiği olduğunu gelmez.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="f3d1b-145">Bazı eşlemeleri, tüm bu boyutlara farklılıkları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="f3d1b-146">Çeşitli eşleme olasılıklara olası farklar hakkındaki ayrıntıları bulabilirsiniz [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
### <a name="user-defined-types"></a><span data-ttu-id="f3d1b-147">Kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="f3d1b-147">User-defined Types</span></span>  
 <span data-ttu-id="f3d1b-148">Kullanıcı tanımlı CLR türleri, tür sistem boşluğu yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="f3d1b-149">Yine de bunlar türü sürüm oluşturma hakkında ilginç sorunları ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="f3d1b-150">İstemci sürümünde değişikliğe veritabanı sunucusunda depolanan tür değişikliği eşlenmesi değil.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="f3d1b-151">Herhangi bir değişiklik burada türü anlamları eşleşmeyebilir ve sürüm aralığı görünür hale gelmiş büyük olasılıkla başka bir tür uyuşmazlığı neden olur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="f3d1b-152">Devralma hiyerarşilerini birbirini izleyen sürümlerde yeniden düzenlenen gibi diğer zorluklar oluşur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>  
  
## <a name="expression-semantics"></a><span data-ttu-id="f3d1b-153">İfade semantiği</span><span class="sxs-lookup"><span data-stu-id="f3d1b-153">Expression Semantics</span></span>  
 <span data-ttu-id="f3d1b-154">CLR ve veritabanı türler arasında ikili uyuşmazlığı yanı sıra ifadeler için uyuşmazlık karmaşıklık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="f3d1b-155">İşleci semantik, işlev semantiği, örtük tür dönüştürme ve öncelik kuralları uyuşmazlıkları dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>  
  
 <span data-ttu-id="f3d1b-156">Aşağıdaki alt bölümleri görünüşe göre benzer ifadeler arasındaki uyumsuzluk göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="f3d1b-157">Verilen bir CLR ifade için anlamsal olarak eşdeğer SQL deyimlerini oluşturmak mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="f3d1b-158">Ancak, bu görünüşe göre benzer ifadeler anlam farklarını CLR kullanıcı için yetkisiz değiştirmeye karşı korumalı olup ve bu nedenle anlam denklik için gerekli olan değişiklikleri veya yöneliktir açık değil.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="f3d1b-159">Bir dizi için bir ifade değerlendirildiğinde bu özellikle önemli bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="f3d1b-160">Fark görünürlüğünü bağımlı veri - ve kodlama ve hata ayıklama sırasında belirlemek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>  
  
### <a name="null-semantics"></a><span data-ttu-id="f3d1b-161">Null Semantikler</span><span class="sxs-lookup"><span data-stu-id="f3d1b-161">Null Semantics</span></span>  
 <span data-ttu-id="f3d1b-162">SQL deyimleri, Boolean ifadeler için üç değerli mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="f3d1b-163">Sonucu true, false veya null olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-163">The result can be true, false, or null.</span></span> <span data-ttu-id="f3d1b-164">Bunun aksine, CLR iki değerli Boolean sonucu null değerler içeren karşılaştırmaları için belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="f3d1b-165">Aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-165">Consider the following code:</span></span>  
  
 [!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
 [!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]  
  
```  
-- Assume col1 and col2 are integer columns with null values.   
-- Assume that ANSI null behavior has not been explicitly  
--    turned off.  
Select …  
From …  
Where col1 = col2  
-- Evaluates to null, not true and the corresponding row is not  
--     selected.  
-- To obtain matching behavior (i -> col1, j -> col2) change  
--     the query to the following:  
Select …  
From …  
Where  
    col1 = col2   
or (col1 is null and col2 is null)  
-- (Visual Basic 'Nothing'.)  
```  
  
 <span data-ttu-id="f3d1b-166">İki değerli sonuçlarıyla ilgili varsayım benzer bir sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-166">A similar problem occurs with the assumption about two-valued results.</span></span>  
  
 [!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
 [!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]  
  
```  
-- Assume col1 and col2 are nullable columns.  
-- Assume that ANSI null behavior has not been explicitly  
--     turned off.  
Select …  
From …  
Where  
    col1 = col2        
or col1 != col2  
-- Visual Basic: col1 <> col2.  
  
-- Excludes the case where the boolean expression evaluates  
--     to null. Therefore the where clause does not always  
--     evaluate to true.  
```  
  
 <span data-ttu-id="f3d1b-167">Önceki örnekte SQL oluşturma, eşdeğer bir davranış elde edebilirsiniz, ancak çevirisi amacınız doğru yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f3d1b-168">değil uygulamaktadır C# `null` veya Visual Basic `nothing` SQL karşılaştırma semantiği.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="f3d1b-169">Karşılaştırma işleçleri sözdizimsel olarak SQL eşdeğerlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="f3d1b-170">Sunucu veya bağlantı ayarları tarafından tanımlandığı şekilde, semantiği SQL semantiği yansıtır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="f3d1b-171">(Semantiği değiştirmek için ayarları değiştirebilirsiniz ancak) iki null değerler varsayılan SQL Server Ayarları altında eşit olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="f3d1b-172">Ne olursa olsun, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu çevirisi sunucu ayarlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>  
  
 <span data-ttu-id="f3d1b-173">Değişmez değer ile bir karşılaştırması `null` (`nothing`) en uygun SQL sürümüne çevrilir (`is null` veya `is not null`).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>  
  
 <span data-ttu-id="f3d1b-174">Değerini `null` (`nothing`) harmanlamasında SQL Server tarafından tanımlanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlama değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>  
  
### <a name="type-conversion-and-promotion"></a><span data-ttu-id="f3d1b-175">Tür dönüştürme ve yükseltme</span><span class="sxs-lookup"><span data-stu-id="f3d1b-175">Type Conversion and Promotion</span></span>  
 <span data-ttu-id="f3d1b-176">SQL ifadelerinde zengin örtülü dönüştürmeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="f3d1b-177">Benzer ifadelerinde C# açık bir tür dönüştürme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="f3d1b-178">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-178">For example:</span></span>  
  
-   `Nvarchar` <span data-ttu-id="f3d1b-179">ve `DateTime` türleri karşılaştırılabilir SQL'de açık tüm atamaları; C# açık dönüştürme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-179">and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>  
  
-   `Decimal` <span data-ttu-id="f3d1b-180">örtük olarak dönüştürülür `DateTime` SQL.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-180">is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="f3d1b-181">C#bir örtük dönüştürmelerine izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-181">C# does not allow for an implicit conversion.</span></span>  
  
 <span data-ttu-id="f3d1b-182">Benzer şekilde, Transact-SQL türü önceliği türü önceliği farklıdır C# temel türleri kümesini farklı olduğu için.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="f3d1b-183">Aslında, öncelik listeler arasında NET alt/üst ilişkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="f3d1b-184">Örneğin, karşılaştırma bir `nvarchar` ile bir `varchar` örtük dönüştürülmesi neden `varchar` ifadesine `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="f3d1b-185">CLR hiçbir eşdeğer yükseltme sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-185">The CLR provides no equivalent promotion.</span></span>  
  
 <span data-ttu-id="f3d1b-186">Basit durumda, bu farklılıkları CLR ifadeler için karşılık gelen bir SQL ifadesi yedekli olacak şekilde yayınları neden.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="f3d1b-187">Daha da önemlisi, Ara sonuçlar bir SQL ifadesi örtük olarak hiçbir doğru karşılığı yoktur, bir tür yükseltilmesi C#ve bunun tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="f3d1b-188">Genel olarak, test etme, hata ayıklama ve doğrulama gibi ifadelerin ekler önemli yük kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>  
  
### <a name="collation"></a><span data-ttu-id="f3d1b-189">Harmanlama</span><span class="sxs-lookup"><span data-stu-id="f3d1b-189">Collation</span></span>  
 <span data-ttu-id="f3d1b-190">Transact-SQL açık harmanlamaları karakter dize türleri için ek açıklamaları olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="f3d1b-191">Bu harmanlamaları belirli karşılaştırmalar geçerliliğini belirler.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="f3d1b-192">Örneğin, iki sütun farklı açık harmanlamaları ile karşılaştıran bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="f3d1b-193">Basitleştirilmiş çok CTS dize türü kullanımı gibi hataları neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="f3d1b-194">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-194">Consider the following example:</span></span>  
  
```  
create table T2 (  
    Col1 nvarchar(10),  
    Col2      nvarchar(10) collate Latin_general_ci_as  
)  
```  
  
 [!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
 [!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]  
  
```  
Select …  
From …  
Where Col1 = Col2  
-- Error, collation conflict.  
```  
  
 <span data-ttu-id="f3d1b-195">Aslında, harmanlama tümce oluşturur bir *kısıtlı türü* değiştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>  
  
 <span data-ttu-id="f3d1b-196">Benzer şekilde, sıralama türü sistem arasında önemli ölçüde farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="f3d1b-197">Bu farkın, sonuçlarını sıralama etkiler.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-197">This difference affects the sorting of results.</span></span> <xref:System.Guid> <span data-ttu-id="f3d1b-198">tüm 16 bayt sözlük sırasına göre sıralanabilir (`IComparable()`) T-SQL GUID'leri şu sırayla karşılaştırır bilgileriyse: node(10-15) clock-seq(8-9), time-high(6-7) time-mid(4-5), time-low(0-3).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-198">is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="f3d1b-199">Bu sıralama, NT tarafından oluşturulan GUID sekizli böyle bir siparişin başlattıklarında SQL 7. 0'yapıldı.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="f3d1b-200">Yaklaşım GUID'leri aynı düğüm kümesi oluşturulan sıralı zaman damgasına göre gelen olmasını sağladı.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="f3d1b-201">Yaklaşım (haline ekler yerine rastgele IOs ekler) dizin oluşturma için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="f3d1b-202">Daha sonra Windows içinde sırasını Gizlilik sorunları nedeniyle karıştırılmış, ancak SQL uyumluluğu sürdürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="f3d1b-203">Geçici bir çözüm kullanmaktır <xref:System.Data.SqlTypes.SqlGuid> yerine <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>  
  
### <a name="operator-and-function-differences"></a><span data-ttu-id="f3d1b-204">İşleç ve işlev farklılıkları</span><span class="sxs-lookup"><span data-stu-id="f3d1b-204">Operator and Function Differences</span></span>  
 <span data-ttu-id="f3d1b-205">İşleçler ve temelde benzer işlevler farenizin farklı semantiklere sahip.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="f3d1b-206">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-206">For example:</span></span>  
  
-   <span data-ttu-id="f3d1b-207">C#kısa devre semantiği için mantıksal işleçler işlenenlerin sözcük düzenine dayanan belirtir `&&` ve `||`.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="f3d1b-208">SQL, diğer taraftan kümesi tabanlı sorgular için hedeflenen ve bu nedenle iyileştirici yürütme sırası karar özgürlüğü sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="f3d1b-209">Bazı uygulamaları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-209">Some of the implications include the following:</span></span>  
  
    -   <span data-ttu-id="f3d1b-210">Anlamsal olarak eşdeğer çeviri gerektirir "`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="f3d1b-210">Semantically equivalent translation would require "`CASE` …</span></span> `WHEN` <span data-ttu-id="f3d1b-211">…</span><span class="sxs-lookup"><span data-stu-id="f3d1b-211">…</span></span> `THEN`<span data-ttu-id="f3d1b-212">"yeniden sıralama işlenen yürütülmesini önlemek için SQL'de oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-212">" construct in SQL to avoid reordering of operand execution.</span></span>  
  
    -   <span data-ttu-id="f3d1b-213">Gevşek bir çeviri `AND` / `OR` işleçleri, beklenmeyen hatalar neden C# ifade değerlendirme birinci işlenenin sonucuna göre ikinci işlenenin değerlendirmeye kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>  
  
-   `Round()` <span data-ttu-id="f3d1b-214">işlev farklı semantiğe sahip [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ve T-SQL.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-214">function has different semantics in [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] and in T-SQL.</span></span>  
  
-   <span data-ttu-id="f3d1b-215">Dizeler için başlangıç dizini 1'de SQL CLR içinde 0 nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="f3d1b-216">Bu nedenle, dizin olan herhangi bir işlev dizin çeviri gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-216">Therefore, any function that has index needs index translation.</span></span>  
  
-   <span data-ttu-id="f3d1b-217">CLR, kayan noktalı sayıları ('%') modulus işleci destekler, ancak SQL yoktur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>  
  
-   <span data-ttu-id="f3d1b-218">`Like` İşleci etkili bir şekilde otomatik aşırı örtük dönüştürmeleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="f3d1b-219">Ancak `Like` işleci karakter dize türleri, sayısal türleri arasında örtük dönüşüm üzerinde çalışılacak tanımlanır veya `DateTime` türleri ile kullanılmak üzere bu dize olmayan türlerde sağlar `Like` ekleyebiliyorsa.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="f3d1b-220">CTS içinde karşılaştırılabilir örtük dönüştürmelerin yok.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="f3d1b-221">Bu nedenle, aşırı ek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-221">Therefore, additional overloads are needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3d1b-222">Bu `Like` işleci davranışı uygular C# yalnızca; Visual Basic `Like` anahtar sözcüğü, değişmez.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>  
  
-   <span data-ttu-id="f3d1b-223">Taşma her zaman SQL ile işaretli, ancak açıkça belirtilmesi gerekir C# (içinde olmayan adresle önlemek için VisualBasic).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="f3d1b-224">Tamsayı sütunlarını C1, C2 ve C3, C1 + C2 C3 içinde depolanıyorsa, verilen (güncelleştirme T ayarlamak C3 = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>  
  
    ```  
    create table T3 (  
        Col1      integer,  
        Col2      integer  
    )  
    insert into T3 (col1, col2) values (2147483647, 5)  
    -- Valid values: max integer value and 5.  
    select * from T3 where col1 + col2 < 0  
    -- Produces arithmetic overflow error.  
    ```  
  
 [!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
 [!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]  
  
-   <span data-ttu-id="f3d1b-225">SQL simetrik aritmetiği gerçekleştirir çalışırken yuvarlama [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] kullandığı banker yuvarlama.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-225">SQL performs symmetric arithmetic rounding while [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] uses banker’s rounding.</span></span> <span data-ttu-id="f3d1b-226">Bilgi Bankası makalesi 196652 ek ayrıntılar için bkz.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-226">See Knowledgebase article 196652 for additional details.</span></span>  
  
-   <span data-ttu-id="f3d1b-227">Ortak yerel ayarlar için varsayılan SQL karakter dize karşılaştırmaları duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="f3d1b-228">Visual Basic hem de C#, bunlar büyük küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="f3d1b-229">Örneğin, `s == "Food"` (`s = "Food"` Visual Basic'te) ve `s == "Food"` ise farklı sonuçlar verecek `s` olduğu `food`.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>  
  
    ```  
    -- Assume default US-English locale (case insensitive).  
    create table T4 (  
        Col1      nvarchar (256)  
    )  
    insert into T4 values (‘Food’)   
    insert into T4 values (‘FOOD’)  
    select * from T4 where Col1 = ‘food’  
    -- Both the rows are returned because of case-insensitive matching.  
    ```  
  
 [!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
 [!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]  
  
-   <span data-ttu-id="f3d1b-230">İşleçler / SQL sabit uzunluk karakter tür bağımsız değişkenleri için uygulanan işlevleri aynı işleçler/CLR ile uygulanan işlevleri daha önemli ölçüde farklı semantiğe sahip <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3d1b-231">Bu da bir uzantısı türleri hakkında bölümünde ele alınan eksik karşılığı sorunu olarak görüntülenmesine.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>  
  
    ```  
    create table T4 (  
        Col1      nchar(4)  
    )  
    Insert into T5(Col1) values ('21');  
    Insert into T5(Col1) values ('1021');  
    Select * from T5 where Col1 like '%1'  
    -- Only the second row with Col1 = '1021' is returned.  
    -- Not the first row!  
    ```  
  
     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]  
  
     <span data-ttu-id="f3d1b-232">Dize birleştirme ile benzer bir sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-232">A similar problem occurs with string concatenation.</span></span>  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 <span data-ttu-id="f3d1b-233">Özet olarak, bir karışık çeviri CLR ifadeler için gerekli olabilir ve ek işleçler/işlevler SQL işlevselliği göstermek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>  
  
### <a name="type-casting"></a><span data-ttu-id="f3d1b-234">Tür atama</span><span class="sxs-lookup"><span data-stu-id="f3d1b-234">Type Casting</span></span>  
 <span data-ttu-id="f3d1b-235">İçinde C# ve SQL'de kullanıcılar ifade varsayılan semantikleri açık tür atamaları kullanarak değiştirebilirsiniz (`Cast` ve `Convert`).</span><span class="sxs-lookup"><span data-stu-id="f3d1b-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="f3d1b-236">Ancak, bu özellik türü sistem sınırından ifşa eden bir ikilemle doğurur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="f3d1b-237">İstenen semantiği sağlar bir SQL atama ilgili bir kolayca çevrilemez C# cast.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="f3d1b-238">Öte yandan, bir C# atama doğrudan çevrilemez dönüştürme türü uyuşmazlığı, eksik ortaklarınıza ve farklı tür öncelik hiyerarşileri nedeniyle eşdeğer olan bir SQL oturum.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="f3d1b-239">Tür sistemi uyuşmazlığı gösterme ve ifadenin önemli güç kaybı arasında bir ilişki yoktur.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>  
  
 <span data-ttu-id="f3d1b-240">Diğer durumlarda, tür atama ya da etki alanındaki bir ifadenin doğrulama için gerekli olmayan ancak varsayılan olmayan eşleme ifade doğru uygulandığından emin olmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>  
  
```  
-- Example from "Non-default Mapping" section extended  
create table T5 (  
    Col1      nvarchar(10),  
    Col2      nvarchar(10)  
)  
Insert into T5(col1, col2) values (‘3’, ‘2’);  
```  
  
 [!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
 [!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]  
  
```  
Select *  
From T5  
Where Col1 + Col2 > 4     
-- "Col1 + Col2" expr evaluates to '32'   
```  
  
## <a name="performance-issues"></a><span data-ttu-id="f3d1b-241">Performans sorunları</span><span class="sxs-lookup"><span data-stu-id="f3d1b-241">Performance Issues</span></span>  
 <span data-ttu-id="f3d1b-242">Bazı SQL Server CLR için hesap türü farkları performans türü sistemleri CLR ve SQL Server arasında geçen zaman neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="f3d1b-243">Performansı etkileyen senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f3d1b-243">Examples of scenarios impacting performance include the following:</span></span>  
  
-   <span data-ttu-id="f3d1b-244">İçin değerlendirme sırası zorlandı mantıksal ve/veya işleçler</span><span class="sxs-lookup"><span data-stu-id="f3d1b-244">Forced order of evaluation for logical and/or operators</span></span>  
  
-   <span data-ttu-id="f3d1b-245">Koşul değerlendirme sırası zorlamak için SQL oluşturma, SQL iyileştirici'nin yeteneğini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>  
  
-   <span data-ttu-id="f3d1b-246">Tür dönüştürmeleri, nesne ilişkisel sorgu uygulamaya veya bir CLR derleyici tarafından sunulan olmadığını dizin kullanım curtail.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>  
  
     <span data-ttu-id="f3d1b-247">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="f3d1b-247">For example,</span></span>  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     <span data-ttu-id="f3d1b-248">İfade çevirisini göz önünde bulundurun `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>  
  
    ```  
    -- Corresponding part of SQL where clause  
    Where …  
    Col1 = SOME_STRING_CONSTANT  
    -- This expression is of the form <varchar> = <nvarchar>.  
    -- Hence SQL introduces a conversion from varchar to nvarchar,  
    --     resulting in  
    Where …  
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT  
    -- Cannot use the index for column Col1 for some implementations.  
    ```  
  
 <span data-ttu-id="f3d1b-249">Anlam farklılıklara ek olarak, CLR türü sistemleri ve SQL Server arasında geçen zaman performans etkilerini dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="f3d1b-250">Büyük veri kümeleri için bu tür performans sorunlarını, uygulama dağıtılabilir olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d1b-251">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3d1b-251">See also</span></span>

- [<span data-ttu-id="f3d1b-252">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="f3d1b-252">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
