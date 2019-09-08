---
title: SQL-CLR Tür Uyumsuzlukları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 27708f4bb8e191156f578132602570bc4a6337b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781204"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="610e1-102">SQL-CLR Tür Uyumsuzlukları</span><span class="sxs-lookup"><span data-stu-id="610e1-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="610e1-103">nesne modeli ve SQL Server arasındaki çevirinin çoğunu otomatik hale getirir.</span><span class="sxs-lookup"><span data-stu-id="610e1-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="610e1-104">Bununla birlikte, bazı durumlar tam çeviriyi önler.</span><span class="sxs-lookup"><span data-stu-id="610e1-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="610e1-105">Bu anahtar, ortak dil çalışma zamanı (CLR) türleri ve SQL Server veritabanı türleri arasındaki uyuşmazlıkları aşağıdaki bölümlerde özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="610e1-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="610e1-106">[SQL-CLR türü eşlemesinde](sql-clr-type-mapping.md) ve [veri türlerinde ve işlevlerde](data-types-and-functions.md)belirli tür eşlemeleri ve işlev çevirisi hakkında daha fazla ayrıntı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="610e1-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](sql-clr-type-mapping.md) and [Data Types and Functions](data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="610e1-107">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="610e1-107">Data Types</span></span>

<span data-ttu-id="610e1-108">CLR ve SQL Server arasında çeviri, bir sorgu veritabanına gönderilirken ve sonuçlar nesne modelinize geri gönderildiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="610e1-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="610e1-109">Örneğin, aşağıdaki Transact-SQL sorgusu iki değer dönüştürmesi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="610e1-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="610e1-110">Sorgu SQL Server üzerinde yürütülmeden önce Transact-SQL parametresinin değeri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="610e1-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="610e1-111">Bu örnekte, `id` veritabanının değerin ne olduğunu anlayabilmesi için önce parametre değeri bir <xref:System.Int32?displayProperty=nameWithType> CLR türünden SQL Server `INT` türüne çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="610e1-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="610e1-112">Ardından sonuçları almak için SQL Server `DateOfBirth` sütunu, nesne modelinde kullanılmak üzere bir SQL Server `DATETIME` türünden clr <xref:System.DateTime?displayProperty=nameWithType> türüne çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="610e1-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="610e1-113">Bu örnekte, CLR nesne modeli ve SQL Server veritabanındaki türler doğal eşlemelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="610e1-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="610e1-114">Ancak, bu her zaman durum değildir.</span><span class="sxs-lookup"><span data-stu-id="610e1-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="610e1-115">Eksik karşılıkları</span><span class="sxs-lookup"><span data-stu-id="610e1-115">Missing Counterparts</span></span>

<span data-ttu-id="610e1-116">Aşağıdaki türlerin makul karşılıkları yoktur.</span><span class="sxs-lookup"><span data-stu-id="610e1-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="610e1-117">CLR <xref:System> ad alanındaki uyuşmazlıklar:</span><span class="sxs-lookup"><span data-stu-id="610e1-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="610e1-118">**İşaretsiz tamsayılar**.</span><span class="sxs-lookup"><span data-stu-id="610e1-118">**Unsigned integers**.</span></span> <span data-ttu-id="610e1-119">Bu türler genellikle, taşmamak için daha büyük boyuttaki imzalı karşılıklarına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="610e1-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="610e1-120">Değişmez değerler, değere göre aynı veya daha küçük olan işaretli bir sayısal değere dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="610e1-121">**Boole değeri**.</span><span class="sxs-lookup"><span data-stu-id="610e1-121">**Boolean**.</span></span> <span data-ttu-id="610e1-122">Bu türler, bir bit veya daha büyük sayısal ya da dizeye eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="610e1-123">Değişmez değer aynı değere değerlendirilen bir ifadeye eşleştirilebilir (örneğin, SQL 'de, `1=1` CLS içinde için `True` ).</span><span class="sxs-lookup"><span data-stu-id="610e1-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="610e1-124">**TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="610e1-124">**TimeSpan**.</span></span> <span data-ttu-id="610e1-125">Bu tür, iki `DateTime` değer arasındaki farkı temsil eder ve SQL Server karşılık `timestamp` gelmez.</span><span class="sxs-lookup"><span data-stu-id="610e1-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="610e1-126">CLR <xref:System.TimeSpan?displayProperty=nameWithType> , bazı durumlarda SQL Server `TIME` türü ile de eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="610e1-127">SQL Server `TIME` türü yalnızca 24 saatten daha az pozitif değerler temsil etmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="610e1-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="610e1-128">CLR <xref:System.TimeSpan> 'de çok daha büyük bir Aralık vardır.</span><span class="sxs-lookup"><span data-stu-id="610e1-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="610e1-129">İçindeki <xref:System.Data.SqlTypes> SQL Server özel .NET Framework türleri bu karşılaştırmaya dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="610e1-129">SQL Server-specific .NET Framework types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="610e1-130">SQL Server uyuşmazlıkları:</span><span class="sxs-lookup"><span data-stu-id="610e1-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="610e1-131">**Sabit uzunlukta karakter türleri**.</span><span class="sxs-lookup"><span data-stu-id="610e1-131">**Fixed length character types**.</span></span> <span data-ttu-id="610e1-132">Transact-SQL, Unicode ve Unicode olmayan kategoriler arasında ayrım yapar ve her kategoride üç farklı türe sahiptir: sabit uzunluk `nchar` `varchar` / `char`, değişken uzunluğu `nvarchar`ve / daha büyük boyutlu `ntext`. / `text`</span><span class="sxs-lookup"><span data-stu-id="610e1-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="610e1-133">Sabit uzunluklu karakter türleri, karakterleri almak için clr <xref:System.Char?displayProperty=nameWithType> türü ile eşleştirilebilir, ancak dönüştürmelerde ve davranıştaki aynı türe karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="610e1-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="610e1-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="610e1-134">**Bit**.</span></span> <span data-ttu-id="610e1-135">Etki alanı aynı sayıda `Nullable<Boolean>`değere sahip olsa da, ikisi farklı türlerdir. `bit`</span><span class="sxs-lookup"><span data-stu-id="610e1-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="610e1-136">`Bit`değerlerini `1` alır ve `0` yerine `true`Boolean ifadelerineeşdeğerolarakkullanılamaz./ `false`</span><span class="sxs-lookup"><span data-stu-id="610e1-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="610e1-137">**Zaman damgası**.</span><span class="sxs-lookup"><span data-stu-id="610e1-137">**Timestamp**.</span></span> <span data-ttu-id="610e1-138">CLR <xref:System.TimeSpan?displayProperty=nameWithType> türünden farklı olarak SQL Server `TIMESTAMP` türü, her bir güncelleştirme için benzersiz olan veritabanı tarafından oluşturulan 8 baytlık bir sayıyı temsil eder ve değerler arasındaki <xref:System.DateTime> farka göre değildir.</span><span class="sxs-lookup"><span data-stu-id="610e1-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="610e1-139">**Para** ve küçük **para**.</span><span class="sxs-lookup"><span data-stu-id="610e1-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="610e1-140">Bu türler, ile <xref:System.Decimal> eşleştirilir ancak temelde farklı türlerdir ve sunucu tabanlı işlevlere ve Dönüştürmelere göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="610e1-141">Birden çok eşleme</span><span class="sxs-lookup"><span data-stu-id="610e1-141">Multiple Mappings</span></span>

<span data-ttu-id="610e1-142">Bir veya daha fazla CLR veri türüyle eşleyebileceğiniz pek çok SQL Server veri türü vardır.</span><span class="sxs-lookup"><span data-stu-id="610e1-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="610e1-143">Bir veya daha fazla SQL Server türüne eşleyebileceğiniz birçok CLR türü de vardır.</span><span class="sxs-lookup"><span data-stu-id="610e1-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="610e1-144">Bir eşlemenin LINQ to SQL tarafından desteklenmesine rağmen, CLR ve SQL Server arasında eşlenen iki türün duyarlık, Aralık ve semantiklerde kusursuz bir eşleşme olduğu anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="610e1-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="610e1-145">Bazı eşlemeler bu boyutların herhangi birinde veya tümünde farkları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="610e1-146">[SQL-CLR tür eşlemesinde](sql-clr-type-mapping.md)çeşitli eşleme olanakları için bu olası farklılıklar hakkındaki ayrıntıları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="610e1-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="610e1-147">Kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="610e1-147">User-defined Types</span></span>

<span data-ttu-id="610e1-148">Kullanıcı tanımlı CLR türleri, tür sistem boşluğunu köprülemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="610e1-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="610e1-149">Bununla birlikte, tür sürümü oluşturma hakkında ilginç sorunlar ortaya alırlar.</span><span class="sxs-lookup"><span data-stu-id="610e1-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="610e1-150">İstemcideki sürümde bir değişiklik, veritabanı sunucusunda depolanan türdeki bir değişiklik ile eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="610e1-151">Böyle bir değişiklik, tür semantiğinin eşleşmediği ve sürüm boşluğunun görünür olma olasılığı olan başka tür uyuşmazlığına neden olur.</span><span class="sxs-lookup"><span data-stu-id="610e1-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="610e1-152">Devralma hiyerarşileri birbirini izleyen sürümlerde yeniden düzenlenmiş, daha karmaşıklıklar oluşur.</span><span class="sxs-lookup"><span data-stu-id="610e1-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="610e1-153">İfade semantikleri</span><span class="sxs-lookup"><span data-stu-id="610e1-153">Expression Semantics</span></span>

<span data-ttu-id="610e1-154">CLR ve veritabanı türleri arasında ikili uyumsuzluğa ek olarak, ifadeler uyuşmazlığa karmaşıklık ekler.</span><span class="sxs-lookup"><span data-stu-id="610e1-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="610e1-155">İşleç semantiğinin, işlev semantiğinin, örtük tür dönüştürmenin ve öncelik kurallarının uyuşmazlıkları göz önünde bulundurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="610e1-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="610e1-156">Aşağıdaki alt bölümlerde benzer ifadeler arasındaki uyuşmazlık gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="610e1-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="610e1-157">Belirli bir CLR ifadesine anlamsal olarak eşdeğer olan SQL ifadeleri oluşturmak mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="610e1-158">Ancak, benzer ifadeler arasındaki anlam farklılıklarının bir CLR kullanıcısına açık olup olmadığını ve bu nedenle anlamsal denklik için gereken değişikliklerin amaçlanıp düşünülmeyeceğini net değildir.</span><span class="sxs-lookup"><span data-stu-id="610e1-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="610e1-159">Bir ifade bir değer kümesi için değerlendirildiğinde bu özellikle kritik bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="610e1-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="610e1-160">Farkın görünürlüğü verilere bağlı olabilir ve kodlama ve hata ayıklama sırasında belirlenmesi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="610e1-161">Null Semantikler</span><span class="sxs-lookup"><span data-stu-id="610e1-161">Null Semantics</span></span>

<span data-ttu-id="610e1-162">SQL ifadeleri, Boole ifadeleri için üç değerli mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="610e1-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="610e1-163">Sonuç doğru, yanlış veya null olabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-163">The result can be true, false, or null.</span></span> <span data-ttu-id="610e1-164">Buna karşılık, CLR null değerleri içeren karşılaştırmalar için iki değerli Boole sonucu belirtir.</span><span class="sxs-lookup"><span data-stu-id="610e1-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="610e1-165">Aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="610e1-165">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="610e1-166">İki değerli sonuçların varsayımıyla ilgili benzer bir sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="610e1-166">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="610e1-167">Önceki durumda, SQL oluşturma ile eşdeğer bir davranış edinebilirsiniz, ancak çeviri amacınız doğru şekilde yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="610e1-168">SQL üzerinde karşılaştırma C# `null` semantiğini `nothing` uygulamaz veya Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="610e1-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="610e1-169">Karşılaştırma işleçleri, sözdizimsel olarak SQL eşdeğerlerine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="610e1-170">Semantik, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiğini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="610e1-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="610e1-171">İki null değer, varsayılan SQL Server ayarları altında eşit olarak değerlendirilir (ancak semantiğini değiştirmek için ayarları değiştirebilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="610e1-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="610e1-172">Ne olursa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] olsun, sorgu çevirisi 'nde sunucu ayarlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="610e1-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="610e1-173">Değişmez değer `null` (`nothing`) ile karşılaştırma uygun SQL sürümüne (`is null` veya `is not null`) çevrilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="610e1-174">Harmanlama içindeki `null` (`nothing`) değeri SQL Server tarafından tanımlanır; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlamayı değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="610e1-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="610e1-175">Tür dönüştürme ve yükseltme</span><span class="sxs-lookup"><span data-stu-id="610e1-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="610e1-176">SQL, İfadelerdeki zengin bir örtük dönüştürme kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="610e1-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="610e1-177">İçindeki C# benzer ifadeler açık bir tür dönüştürme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="610e1-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="610e1-178">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="610e1-178">For example:</span></span>

- <span data-ttu-id="610e1-179">`Nvarchar`ve `DateTime` türleri herhangi bir açık yayını olmadan SQL 'de karşılaştırılabilir; C# açık dönüştürme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="610e1-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="610e1-180">`Decimal`örtük olarak SQL 'e `DateTime` dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="610e1-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="610e1-181">C#örtük dönüştürmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="610e1-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="610e1-182">Benzer şekilde, temel alınan türler farklı olduğundan Transact-SQL içindeki tür C# önceliği, içindeki tür önceliğine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="610e1-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="610e1-183">Aslında, öncelik listeleri arasında şifresiz bir alt küme/üst küme ilişkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="610e1-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="610e1-184">Örneğin `nvarchar` , bir `varchar` ile karşılaştırmak `varchar` ifadenin örtük `nvarchar`dönüştürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="610e1-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="610e1-185">CLR eşdeğer bir yükseltme sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="610e1-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="610e1-186">Basit durumlarda bu farklılıklar, CLR deyimlerinin karşılık gelen bir SQL ifadesi için gereksiz olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="610e1-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="610e1-187">Daha da önemlisi, bir SQL ifadesinin ara sonuçları örtük olarak ' ın içinde C#karşılığı olmayan bir türe yükseltilebilir ve tam tersi olabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="610e1-188">Genel, test, hata ayıklama ve bu ifadelerin doğrulanması kullanıcıya önemli bir yük ekler.</span><span class="sxs-lookup"><span data-stu-id="610e1-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="610e1-189">Harmanlama</span><span class="sxs-lookup"><span data-stu-id="610e1-189">Collation</span></span>

<span data-ttu-id="610e1-190">Transact-SQL, karakter dize türlerine ek açıklama olarak açık harmanlamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="610e1-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="610e1-191">Bu harmanlamalar, bazı karşılaştırmaların geçerliliğini tespit edilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="610e1-192">Örneğin, iki sütunu farklı açık harmanlamalarla karşılaştırmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="610e1-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="610e1-193">Çok Basitleştirilmiş CTS dize türü kullanımı bu tür hatalara neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="610e1-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="610e1-194">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="610e1-194">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="610e1-195">Aslında, harmanlama alt yan tümcesi Substitutable olmayan bir *kısıtlanmış tür* oluşturur.</span><span class="sxs-lookup"><span data-stu-id="610e1-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="610e1-196">Benzer şekilde, sıralama düzeni tür sistemleri genelinde önemli ölçüde farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="610e1-197">Bu fark sonuçların sıralanmasını etkiler.</span><span class="sxs-lookup"><span data-stu-id="610e1-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="610e1-198"><xref:System.Guid>lexicographic Order (`IComparable()`) tarafından tüm 16 baytlara göre sıralanır, ancak T-SQL GUID 'leri şu sırayla karşılaştırır: düğüm (10-15), saat-SEQ (8-9), zaman-yüksek (6-7), zaman-Orta (4-5), saat-düşük (0-3).</span><span class="sxs-lookup"><span data-stu-id="610e1-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="610e1-199">Bu sıralama SQL 7,0 ' de, NT tarafından üretilen GUID 'lerde bu tür bir Sekizli sıra olduğunda yapılır.</span><span class="sxs-lookup"><span data-stu-id="610e1-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="610e1-200">Aynı düğüm kümesinde oluşturulan GUID 'Ler, zaman damgasına göre sıralı sırayla birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="610e1-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="610e1-201">Yaklaşım ayrıca dizinler oluşturmak için de yararlıdır (rastgele IOs yerine ekleme ekler).</span><span class="sxs-lookup"><span data-stu-id="610e1-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="610e1-202">Bu sipariş gizlilik sorunları nedeniyle Windows 'da daha sonra karıştırılırsa, ancak SQL 'in uyumluluk koruması gerekir.</span><span class="sxs-lookup"><span data-stu-id="610e1-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="610e1-203">Bunun yerine bir geçici çözüm kullanılır. <xref:System.Guid> <xref:System.Data.SqlTypes.SqlGuid></span><span class="sxs-lookup"><span data-stu-id="610e1-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="610e1-204">İşleç ve Işlev farklılıkları</span><span class="sxs-lookup"><span data-stu-id="610e1-204">Operator and Function Differences</span></span>

<span data-ttu-id="610e1-205">Esas olarak karşılaştırılabilir operatörler ve işlevler, daha az farklı semantiklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="610e1-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="610e1-206">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="610e1-206">For example:</span></span>

- <span data-ttu-id="610e1-207">C#mantıksal işleçler `&&` ve `||`için işlenen nesnelerin sözlü sırası temelinde kısa devre semantiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="610e1-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="610e1-208">Diğer taraftan SQL, küme tabanlı sorgulara yöneliktir ve bu nedenle, yürütme sırasına karar vermek için iyileştiricinin daha fazla özgürlüğü sağlar.</span><span class="sxs-lookup"><span data-stu-id="610e1-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="610e1-209">Bazı etkileri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="610e1-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="610e1-210">Anlamsal olarak eşdeğer çeviri şunları gerektirir`CASE` "...</span><span class="sxs-lookup"><span data-stu-id="610e1-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="610e1-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="610e1-211">`WHEN` …</span></span> <span data-ttu-id="610e1-212">`THEN`"işleneni yürütmenin yeniden sıralanmasını önlemek için SQL 'de oluşturun.</span><span class="sxs-lookup"><span data-stu-id="610e1-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="610e1-213">İfade, birinci işlenenin `AND` değerlendirmesi sonucuna bağlı olarak ikinci işleneni değerlendirmede kullanıyorsa, `OR` işleçlere gevşek çeviri / beklenmeyen hatalara neden olabilir. C#</span><span class="sxs-lookup"><span data-stu-id="610e1-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="610e1-214">`Round()`işlevin .NET Framework ve T-SQL içinde farklı anlamları vardır.</span><span class="sxs-lookup"><span data-stu-id="610e1-214">`Round()` function has different semantics in .NET Framework and in T-SQL.</span></span>

- <span data-ttu-id="610e1-215">Dizeler için başlangıç dizini, CLR 'de 0, SQL 'de 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="610e1-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="610e1-216">Bu nedenle, dizini olan herhangi bir işlev Dizin çevirisine ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="610e1-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="610e1-217">CLR, kayan noktalı sayılar için mod ('% ') işlecini destekler, ancak SQL desteklemez.</span><span class="sxs-lookup"><span data-stu-id="610e1-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="610e1-218">`Like` İşleci örtük dönüştürmeleri temel alarak otomatik aşırı yüklemeleri etkin bir şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="610e1-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="610e1-219">İşleci karakter dize türleri üzerinde çalışmak üzere tanımlansa da, sayısal türlerden veya `DateTime` türlerden örtük dönüştürme, bu dize olmayan `Like` türlerin de aynı zamanda kullanılmasını sağlar. `Like`</span><span class="sxs-lookup"><span data-stu-id="610e1-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="610e1-220">CTS 'de, karşılaştırılabilir örtük dönüştürmeler yok.</span><span class="sxs-lookup"><span data-stu-id="610e1-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="610e1-221">Bu nedenle, ek aşırı yüklemeler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="610e1-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="610e1-222">Bu `Like` işleç davranışı yalnızca için C# geçerlidir; Visual Basic `Like` anahtar sözcüğü değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="610e1-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="610e1-223">Taşma her zaman SQL 'de işaretlendi, ancak wraparound kaçınmak için (Visual Basic değil C# ) içinde açıkça belirtilmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="610e1-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="610e1-224">C1 ve C2, C3 (güncelleştirme T kümesi C3 = C1 + C2) içinde depolanıyorsa, C1, C2 ve C3 tamsayı sütunları veriliyor.</span><span class="sxs-lookup"><span data-stu-id="610e1-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
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

- <span data-ttu-id="610e1-225">SQL, .NET Framework Banker yuvarlama kullandığından, simetrik aritmetik yuvarlama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="610e1-225">SQL performs symmetric arithmetic rounding while .NET Framework uses banker’s rounding.</span></span> <span data-ttu-id="610e1-226">Daha fazla ayrıntı için bkz. Bilgi Bankası makalesi 196652.</span><span class="sxs-lookup"><span data-stu-id="610e1-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="610e1-227">Varsayılan olarak, ortak yerel ayarlarda karakter dizesi karşılaştırmaları SQL 'de büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="610e1-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="610e1-228">Visual Basic ve içinde C#, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="610e1-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="610e1-229">Örneğin `s == "Food"` , (`s = "Food"` Visual Basic) ve `s == "Food"` `s` ise`food`farklı sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
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

- <span data-ttu-id="610e1-230">SQL 'deki sabit uzunluklu karakter türü bağımsız değişkenlerine uygulanan operatörler/işlevler, CLR <xref:System.String?displayProperty=nameWithType>'ye uygulanmış aynı işleçlere/işlevlere göre önemli ölçüde farklı semantiklerdir.</span><span class="sxs-lookup"><span data-stu-id="610e1-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="610e1-231">Bu, türler hakkında bölümünde ele alınan eksik karşılığı sorununun bir uzantısı olarak da görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
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

     <span data-ttu-id="610e1-232">Dize birleştirme ile benzer bir sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="610e1-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="610e1-233">Özet bölümünde, bir genişletilmiş çeviri CLR ifadeleri için gerekli olabilir ve SQL işlevselliğini göstermek için ek işleçler/işlevler gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="610e1-234">Tür atama</span><span class="sxs-lookup"><span data-stu-id="610e1-234">Type Casting</span></span>

<span data-ttu-id="610e1-235">C# Ve SQL 'de, kullanıcılar açık tür yayınları (`Cast` ve `Convert`) kullanarak ifadelerin varsayılan semantiğini geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="610e1-236">Ancak, bu özelliği sistem sınırları genelinde göstermek bir dilimon ma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="610e1-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="610e1-237">İstenen semantiğini sağlayan bir SQL cast, bunlara karşılık gelen C# bir tür dönüştürmeye kolayca çevrilemez.</span><span class="sxs-lookup"><span data-stu-id="610e1-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="610e1-238">Öte yandan, tür uyuşmazlıkları C# , eksik karşılıkları ve farklı tür önceliği hiyerarşileri nedeniyle, bir dönüştürme doğrudan eşdeğer bir SQL türüne çevrilemez.</span><span class="sxs-lookup"><span data-stu-id="610e1-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="610e1-239">Sistem uyuşmazlığını ortaya çıkaran ve ifadenin önemli kuvvetinin kaybolması arasında bir denge vardır.</span><span class="sxs-lookup"><span data-stu-id="610e1-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="610e1-240">Diğer durumlarda, bir ifadenin doğrulanması için her iki etki alanında tür atama gerekmeyebilir ve varsayılan olmayan bir eşlemenin ifadeye doğru bir şekilde uygulandığından emin olmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="610e1-241">Performans sorunları</span><span class="sxs-lookup"><span data-stu-id="610e1-241">Performance Issues</span></span>

<span data-ttu-id="610e1-242">Bazı SQL Server CLR tür farklılıkları için hesaplama, CLR ve SQL Server tür sistemleri arasında geçiş yaparken performansın düşmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="610e1-243">Performansı etkileyen senaryolara örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="610e1-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="610e1-244">Mantıksal ve/veya işleçler için zorlanan değerlendirme sıralaması</span><span class="sxs-lookup"><span data-stu-id="610e1-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="610e1-245">Koşul değerlendirmesi sırasını zorlamak için SQL oluşturmak, SQL iyileştiricinin yeteneğini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="610e1-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="610e1-246">Tür dönüştürmeleri, bir CLR derleyicisi tarafından veya nesne Ilişkisel bir sorgu uygulamasıyla tanıtılıp, dizin kullanımını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="610e1-247">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="610e1-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="610e1-248">İfadenin `(s = SOME_STRING_CONSTANT)`çevirisini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="610e1-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="610e1-249">Anlamsal farklılıklara ek olarak, SQL Server ile CLR tür sistemleri arasında geçiş yaparken performansı etkilerini göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="610e1-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="610e1-250">Büyük veri kümeleri için, bu performans sorunları bir uygulamanın dağıtılabilir olup olmadığını belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="610e1-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="610e1-251">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="610e1-251">See also</span></span>

- [<span data-ttu-id="610e1-252">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="610e1-252">Background Information</span></span>](background-information.md)
