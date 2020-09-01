---
description: Group yan tümcesi-C# başvurusu
title: Group yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 5e642492b4b36bb0464baf16baa80c58c19ba9f1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138234"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="4a234-103">group tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4a234-103">group clause (C# Reference)</span></span>

<span data-ttu-id="4a234-104">`group`Yan tümcesi, <xref:System.Linq.IGrouping%602> Grup için anahtar değeriyle eşleşen sıfır veya daha fazla öğe içeren bir nesne dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a234-104">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="4a234-105">Örneğin, her bir dizedeki ilk harfe göre bir dizi dizeyi gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a234-105">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="4a234-106">Bu durumda, ilk harf anahtardır ve bir tür [char](../builtin-types/char.md)içerir ve `Key` her nesnenin özelliğinde saklanır <xref:System.Linq.IGrouping%602> .</span><span class="sxs-lookup"><span data-stu-id="4a234-106">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="4a234-107">Derleyici, anahtarın türünü haller.</span><span class="sxs-lookup"><span data-stu-id="4a234-107">The compiler infers the type of the key.</span></span>

<span data-ttu-id="4a234-108">`group`Aşağıdaki örnekte gösterildiği gibi bir sorgu ifadesini yan tümcesiyle sona erdirmek için:</span><span class="sxs-lookup"><span data-stu-id="4a234-108">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="4a234-109">Her grupta ek sorgu işlemleri gerçekleştirmek [istiyorsanız, ' ın bağlamsal anahtar](into.md) sözcüğünü kullanarak geçici bir tanımlayıcı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a234-109">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="4a234-110">`into`' I kullandığınızda sorgu ile devam etmeniz ve sonunda `select` aşağıdaki alıntıda gösterildiği gibi bir deyimi ya da başka bir yan tümcesini sona erdirmek gerekir `group` :</span><span class="sxs-lookup"><span data-stu-id="4a234-110">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="4a234-111">`group`Bu makalenin örnek bölümünde ile ve olmadan kullanımı için daha kapsamlı örnekler verilmiştir `into` .</span><span class="sxs-lookup"><span data-stu-id="4a234-111">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="4a234-112">Bir grup sorgusunun sonuçlarını numaralandırma</span><span class="sxs-lookup"><span data-stu-id="4a234-112">Enumerating the results of a group query</span></span>

<span data-ttu-id="4a234-113"><xref:System.Linq.IGrouping%602>Bir sorgu tarafından üretilen nesneler `group` temelde bir liste listesi olduğundan, her bir gruptaki öğelere erişmek için iç içe geçmiş bir [foreach](foreach-in.md) döngüsü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a234-113">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="4a234-114">Dış döngü grup anahtarlarının üzerinde yinelenir ve iç döngü gruptaki her öğe için yinelenir.</span><span class="sxs-lookup"><span data-stu-id="4a234-114">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="4a234-115">Bir grupta anahtar olabilir ancak öğe yok.</span><span class="sxs-lookup"><span data-stu-id="4a234-115">A group may have a key but no elements.</span></span> <span data-ttu-id="4a234-116">Aşağıda, `foreach` önceki kod örneklerinde sorguyu yürüten döngü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a234-116">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="4a234-117">Anahtar türleri</span><span class="sxs-lookup"><span data-stu-id="4a234-117">Key types</span></span>

<span data-ttu-id="4a234-118">Grup anahtarları dize, yerleşik bir sayısal tür veya Kullanıcı tanımlı adlandırılmış tür veya anonim tür gibi herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a234-118">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="4a234-119">Dizeye göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="4a234-119">Grouping by string</span></span>

<span data-ttu-id="4a234-120">Önceki kod örnekleri bir kullanır `char` .</span><span class="sxs-lookup"><span data-stu-id="4a234-120">The previous code examples used a `char`.</span></span> <span data-ttu-id="4a234-121">Bunun yerine bir dize anahtarı kolayca belirtilmelidir, örneğin, son soyadı adı:</span><span class="sxs-lookup"><span data-stu-id="4a234-121">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="4a234-122">Bool ile gruplandırma</span><span class="sxs-lookup"><span data-stu-id="4a234-122">Grouping by bool</span></span>

<span data-ttu-id="4a234-123">Aşağıdaki örnek, sonuçları iki gruba bölmek için bir anahtar için bool değer kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a234-123">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="4a234-124">Değerin yan tümce içindeki bir alt ifade tarafından üretildiğini unutmayın `group` .</span><span class="sxs-lookup"><span data-stu-id="4a234-124">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="4a234-125">Sayısal aralığa göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="4a234-125">Grouping by numeric range</span></span>

<span data-ttu-id="4a234-126">Sonraki örnek, bir yüzdebirlik aralığını temsil eden sayısal grup anahtarları oluşturmak için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a234-126">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="4a234-127">Bir yöntem çağrı sonucunu depolamak için uygun bir konum olarak [izin ver](let-clause.md) öğesinin kullanımını unutmayın. bu sayede yöntemi yan tümcesinde iki kez çağırmak zorunda kalmazsınız `group` .</span><span class="sxs-lookup"><span data-stu-id="4a234-127">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="4a234-128">Sorgu ifadelerinde yöntemleri güvenle kullanma hakkında daha fazla bilgi için bkz. [sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4a234-128">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="4a234-129">Bileşik anahtarlara göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="4a234-129">Grouping by composite keys</span></span>

<span data-ttu-id="4a234-130">Öğeleri birden fazla anahtara göre gruplandırmak istediğinizde bileşik anahtar kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a234-130">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="4a234-131">Anahtar öğesini tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak bileşik anahtar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="4a234-131">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="4a234-132">Aşağıdaki örnekte, bir sınıfının `Person` ve adlı üyelerle bildirildiği varsayılır `surname` `city` .</span><span class="sxs-lookup"><span data-stu-id="4a234-132">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="4a234-133">`group`Yan tümcesi, aynı soyadı ve aynı şehirde bulunan her kişi kümesi için ayrı bir grup oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4a234-133">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="4a234-134">Sorgu değişkenini başka bir yönteme geçirmeniz gerekiyorsa adlandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a234-134">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="4a234-135">Anahtarlar için otomatik uygulanan özellikler kullanarak özel bir sınıf oluşturun ve ardından <xref:System.Object.Equals%2A> ve yöntemlerini geçersiz kılın <xref:System.Object.GetHashCode%2A> .</span><span class="sxs-lookup"><span data-stu-id="4a234-135">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="4a234-136">Ayrıca, bu yöntemleri kesin bir şekilde geçersiz kılmak zorunda değilsiniz bir yapı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a234-136">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="4a234-137">Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [bir dizin ağacındaki yinelenen dosyaları sorgulama](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="4a234-137">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="4a234-138">İkinci makalede, adlandırılmış tür ile bileşik anahtarın nasıl kullanılacağını gösteren bir kod örneği bulunur.</span><span class="sxs-lookup"><span data-stu-id="4a234-138">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="4a234-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a234-139">Example</span></span>

<span data-ttu-id="4a234-140">Aşağıdaki örnek, gruplara ek sorgu mantığı uygulanırken kaynak verileri gruplara sıralamak için standart düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a234-140">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="4a234-141">Bu, devamlılık olmadan gruplandırma olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4a234-141">This is called a grouping without a continuation.</span></span> <span data-ttu-id="4a234-142">Dizeler dizisindeki öğeler, ilk harfine göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="4a234-142">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="4a234-143">Sorgunun sonucu, <xref:System.Linq.IGrouping%602> türünde public bir `Key` özelliği `char` ve <xref:System.Collections.Generic.IEnumerable%601> gruplandırmadaki her öğeyi içeren bir koleksiyonu içeren bir türdür.</span><span class="sxs-lookup"><span data-stu-id="4a234-143">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="4a234-144">`group`Yan tümcesinin sonucu bir dizi dizidir.</span><span class="sxs-lookup"><span data-stu-id="4a234-144">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="4a234-145">Bu nedenle, döndürülen her grup içindeki ayrı öğelere erişmek için, `foreach` Aşağıdaki örnekte gösterildiği gibi, döngü içinde grup anahtarlarını yineleyen iç içe bir döngü kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a234-145">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="4a234-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a234-146">Example</span></span>

<span data-ttu-id="4a234-147">Bu örnek, ile *devam* eden kullanarak gruplar üzerinde nasıl ek mantık gerçekleştirileceğini gösterir `into` .</span><span class="sxs-lookup"><span data-stu-id="4a234-147">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="4a234-148">Daha fazla bilgi için bkz [..](into.md)</span><span class="sxs-lookup"><span data-stu-id="4a234-148">For more information, see [into](into.md).</span></span> <span data-ttu-id="4a234-149">Aşağıdaki örnek, her bir grubu yalnızca anahtar değerini bir sesli harf olarak seçmek üzere sorgular.</span><span class="sxs-lookup"><span data-stu-id="4a234-149">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="4a234-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a234-150">Remarks</span></span>

<span data-ttu-id="4a234-151">Derleme zamanında, `group` yan tümceler yöntemine yapılan çağrılara çevrilir <xref:System.Linq.Enumerable.GroupBy%2A> .</span><span class="sxs-lookup"><span data-stu-id="4a234-151">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a234-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a234-152">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="4a234-153">Sorgu Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4a234-153">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="4a234-154">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4a234-154">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="4a234-155">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a234-155">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="4a234-156">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="4a234-156">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="4a234-157">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4a234-157">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
