---
title: group tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 8e3ddea3ba733cb9ba32e510b050a58407a7a477
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404521"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="8fde9-102">group tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8fde9-102">group clause (C# Reference)</span></span>

<span data-ttu-id="8fde9-103">`group` Yan tümcesi bir dizi döndürür <xref:System.Linq.IGrouping%602> grubu için anahtar değerle eşleşen sıfır veya daha fazla öğe içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="8fde9-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="8fde9-104">Örneğin, bir dizi dize her bir dizenin ilk harfini göre gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fde9-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="8fde9-105">Bu durumda, ilk harfi anahtarı ve bir türe sahip [char](char.md)ve depolanan `Key` her özellik <xref:System.Linq.IGrouping%602> nesne.</span><span class="sxs-lookup"><span data-stu-id="8fde9-105">In this case, the first letter is the key and has a type [char](char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="8fde9-106">Derleyicinin anahtar türünü çıkarsar.</span><span class="sxs-lookup"><span data-stu-id="8fde9-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="8fde9-107">Bir sorgu ifadesi ile sona erdirebilirsiniz bir `group` yan tümcesi, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="8fde9-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="8fde9-108">Her grupta ek sorgu işlemleri gerçekleştirmek istiyorsanız, kullanarak geçici bir tanımlayıcı belirtebilirsiniz [içine](into.md) bağlamsal anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="8fde9-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="8fde9-109">Kullanırken `into`, devam edip sonunda ile son bir `select` deyimi veya başka bir `group` aşağıdaki alıntıda gösterildiği yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="8fde9-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="8fde9-110">Daha da kullanımı örnekleri'ni tamamlamak `group` olmadan `into` bu makalede örnek bölümünde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8fde9-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="8fde9-111">Bir grup sorgunun sonuçlarını numaralandırma</span><span class="sxs-lookup"><span data-stu-id="8fde9-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="8fde9-112">Çünkü <xref:System.Linq.IGrouping%602> nesneleri tarafından üretilen bir `group` sorgu temelde listelerinin bir listesini, iç içe bir kullanmalısınız [foreach](foreach-in.md) döngü her gruptaki öğeleri erişmek için.</span><span class="sxs-lookup"><span data-stu-id="8fde9-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="8fde9-113">Dış döngü Grup anahtarları yinelenir ve iç döngü gruptaki her öğe üzerinde yinelenir.</span><span class="sxs-lookup"><span data-stu-id="8fde9-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="8fde9-114">Bir grubu, bir anahtar vardır, ancak hiçbir öğe olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fde9-114">A group may have a key but no elements.</span></span> <span data-ttu-id="8fde9-115">Aşağıdaki `foreach` önceki kod örneklerinde Sorguyu yürüten döngü:</span><span class="sxs-lookup"><span data-stu-id="8fde9-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="8fde9-116">Anahtar türü</span><span class="sxs-lookup"><span data-stu-id="8fde9-116">Key types</span></span>

<span data-ttu-id="8fde9-117">Gibi bir dize, bir yerleşik sayısal tür veya kullanıcı tanımlı tür veya anonim tür adlı Grup anahtarları herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fde9-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="8fde9-118">Dizeye göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="8fde9-118">Grouping by string</span></span>

<span data-ttu-id="8fde9-119">Yukarıdaki kod örnekleri kullanılan bir `char`.</span><span class="sxs-lookup"><span data-stu-id="8fde9-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="8fde9-120">Bir dize anahtarı kolayca bunun yerine, örneğin tam son adı belirtilmedi:</span><span class="sxs-lookup"><span data-stu-id="8fde9-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="8fde9-121">Bool göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="8fde9-121">Grouping by bool</span></span>

<span data-ttu-id="8fde9-122">Aşağıdaki örnek, sonuçları iki gruplara bölmek bir anahtar için bir bool değeri kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fde9-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="8fde9-123">Bir alt ifadenin, değerini oluşturduğu Not `group` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8fde9-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="8fde9-124">Sayısal Aralık göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="8fde9-124">Grouping by numeric range</span></span>

<span data-ttu-id="8fde9-125">Sonraki örnek, bir dilim aralığı temsil eden sayısal Grup anahtarları oluşturmak için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fde9-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="8fde9-126">Kullanımına dikkat edin [izin](let-clause.md) yöntemini iki kez çağırmak zorunda kalmazsınız bir yöntem depolamak için uygun bir konum arama sonucu, `group` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8fde9-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="8fde9-127">Ayrıca unutmayın `group` "sıfıra" özel durumdan kaçınmak için kod Öğrenci sıfır ortalama sahip olmadığından emin olmak için kontrol eder, yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8fde9-127">Note also in the `group` clause that to avoid a "divide by zero" exception the code checks to make sure that the student doesn't have an average of zero.</span></span> <span data-ttu-id="8fde9-128">Güvenli bir şekilde sorgu ifadelerinde yöntemleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Sorgu ifadelerinde özel durumları işlemek](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8fde9-128">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="8fde9-129">Bileşik anahtarlara göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="8fde9-129">Grouping by composite keys</span></span>

<span data-ttu-id="8fde9-130">Birden fazla anahtar göre grup öğeleri için istediğiniz zaman bir bileşik anahtarı kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fde9-130">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="8fde9-131">Bileşik anahtar, anahtar öğesi tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8fde9-131">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="8fde9-132">Aşağıdaki örnekte, varsayımında bir sınıf `Person` adlı üye ile bildirilmiş `surname` ve `city`.</span><span class="sxs-lookup"><span data-stu-id="8fde9-132">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="8fde9-133">`group` Yan tümcesi kişilerin son aynı ada ve aynı şehirdeki her bir kümesi için oluşturulacak farklı bir grup neden olur.</span><span class="sxs-lookup"><span data-stu-id="8fde9-133">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="8fde9-134">Sorgu değişkeni başka yönteme geçirin, adlandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fde9-134">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="8fde9-135">Otomatik uygulanan özellikler anahtarlarını kullanarak özel bir sınıf oluşturun ve daha sonra geçersiz <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8fde9-135">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="8fde9-136">Bu durumda, kesin olarak bu yöntemleri geçersiz kılmanız gerekmez, bir yapı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fde9-136">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="8fde9-137">Daha fazla bilgi için [nasıl yapılır: bir basit sınıf Implemented Properties ile uygulama](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [nasıl yapılır: bir dizin ağacındaki yinelenen dosyalar için sorgu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="8fde9-137">For more information see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="8fde9-138">Sonraki makalede, türü adlandırılmış bir bileşik anahtarı kullanmayı gösteren bir kod örneği bulunur.</span><span class="sxs-lookup"><span data-stu-id="8fde9-138">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="8fde9-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fde9-139">Example</span></span>

<span data-ttu-id="8fde9-140">Aşağıdaki örnek, hiçbir ek sorgu mantıksal gruplara uygulandığında gruplar halinde kaynak verileri sıralama için standart deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fde9-140">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="8fde9-141">Bu, bir devamlılık olmadan bir gruplandırma olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8fde9-141">This is called a grouping without a continuation.</span></span> <span data-ttu-id="8fde9-142">Dizelerden oluşan bir dizi öğeleri, ilk harfi göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="8fde9-142">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="8fde9-143">Sorgu sonucu bir <xref:System.Linq.IGrouping%602> içeren genel bir tür `Key` türünün özelliği `char` ve <xref:System.Collections.Generic.IEnumerable%601> gruplandırma her öğe içeren koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="8fde9-143">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="8fde9-144">Sonucu bir `group` yan tümcesi ise sıralarının.</span><span class="sxs-lookup"><span data-stu-id="8fde9-144">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="8fde9-145">Bu nedenle, döndürülen her grup içindeki tek tek öğelerine erişmek için bir iç içe kullanın `foreach` Grup anahtarları, aşağıdaki örnekte gösterildiği gibi yinelenen döngü içinde döngü.</span><span class="sxs-lookup"><span data-stu-id="8fde9-145">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="8fde9-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fde9-146">Example</span></span>

<span data-ttu-id="8fde9-147">Bu örnek gösterir kullanarak bunları oluşturduktan sonra ek mantık gruplarında gerçekleştirmek nasıl bir *devamlılık* ile `into`.</span><span class="sxs-lookup"><span data-stu-id="8fde9-147">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="8fde9-148">Daha fazla bilgi için [içine](into.md).</span><span class="sxs-lookup"><span data-stu-id="8fde9-148">For more information, see [into](into.md).</span></span> <span data-ttu-id="8fde9-149">Aşağıdaki örnek, her grup, yalnızca anahtar değeri olan bir sesli seçmek için sorgular.</span><span class="sxs-lookup"><span data-stu-id="8fde9-149">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="8fde9-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fde9-150">Remarks</span></span>

<span data-ttu-id="8fde9-151">Derleme zamanında `group` yan tümceleri çevrilmiş çağrıları içine <xref:System.Linq.Enumerable.GroupBy%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fde9-151">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fde9-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fde9-152">See also</span></span>

<xref:System.Linq.IGrouping%602>  
<xref:System.Linq.Enumerable.GroupBy%2A>  
<xref:System.Linq.Enumerable.ThenBy%2A>  
<xref:System.Linq.Enumerable.ThenByDescending%2A>  
[<span data-ttu-id="8fde9-153">Sorgu Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8fde9-153">Query Keywords</span></span>](query-keywords.md)  
[<span data-ttu-id="8fde9-154">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8fde9-154">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)  
[<span data-ttu-id="8fde9-155">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fde9-155">Create a nested group</span></span>](../../linq/create-a-nested-group.md)  
[<span data-ttu-id="8fde9-156">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="8fde9-156">Group query results</span></span>](../../linq/group-query-results.md)  
[<span data-ttu-id="8fde9-157">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="8fde9-157">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)