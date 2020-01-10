---
title: Group yan tümcesi C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713466"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="df153-102">group tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="df153-102">group clause (C# Reference)</span></span>

<span data-ttu-id="df153-103">`group` yan tümcesi, grup için anahtar değeriyle eşleşen sıfır veya daha fazla öğe içeren bir <xref:System.Linq.IGrouping%602> nesneleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="df153-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="df153-104">Örneğin, her bir dizedeki ilk harfe göre bir dizi dizeyi gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df153-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="df153-105">Bu durumda, ilk harf anahtardır ve bir tür [char](../builtin-types/char.md)içerir ve her <xref:System.Linq.IGrouping%602> nesnesinin `Key` özelliğinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="df153-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="df153-106">Derleyici, anahtarın türünü haller.</span><span class="sxs-lookup"><span data-stu-id="df153-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="df153-107">Aşağıdaki örnekte gösterildiği gibi, bir sorgu ifadesini `group` yan tümcesiyle sona erdirmek isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df153-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="df153-108">Her grupta ek sorgu işlemleri gerçekleştirmek [istiyorsanız, ' ın bağlamsal anahtar](into.md) sözcüğünü kullanarak geçici bir tanımlayıcı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df153-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="df153-109">`into`kullandığınızda, sorguyla devam etmeniz ve sonunda aşağıdaki alıntıda gösterildiği gibi bir `select` deyimi veya başka bir `group` yan tümcesiyle sona erdirmek gerekir:</span><span class="sxs-lookup"><span data-stu-id="df153-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="df153-110">Bu makalenin örnek bölümünde `into` ve olmadan `group` kullanımı için daha kapsamlı örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df153-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="df153-111">Bir grup sorgusunun sonuçlarını numaralandırma</span><span class="sxs-lookup"><span data-stu-id="df153-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="df153-112">Bir `group` sorgusu tarafından oluşturulan <xref:System.Linq.IGrouping%602> nesneleri temelde bir liste listesi olduğundan, her bir gruptaki öğelere erişmek için iç içe geçmiş bir [foreach](foreach-in.md) döngüsü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="df153-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="df153-113">Dış döngü grup anahtarlarının üzerinde yinelenir ve iç döngü gruptaki her öğe için yinelenir.</span><span class="sxs-lookup"><span data-stu-id="df153-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="df153-114">Bir grupta anahtar olabilir ancak öğe yok.</span><span class="sxs-lookup"><span data-stu-id="df153-114">A group may have a key but no elements.</span></span> <span data-ttu-id="df153-115">Aşağıda, önceki kod örneklerinde sorguyu yürüten `foreach` döngüsü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="df153-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="df153-116">Anahtar türleri</span><span class="sxs-lookup"><span data-stu-id="df153-116">Key types</span></span>

<span data-ttu-id="df153-117">Grup anahtarları dize, yerleşik bir sayısal tür veya Kullanıcı tanımlı adlandırılmış tür veya anonim tür gibi herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="df153-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="df153-118">Dizeye göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="df153-118">Grouping by string</span></span>

<span data-ttu-id="df153-119">Önceki kod örnekleri bir `char`kullandı.</span><span class="sxs-lookup"><span data-stu-id="df153-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="df153-120">Bunun yerine bir dize anahtarı kolayca belirtilmelidir, örneğin, son soyadı adı:</span><span class="sxs-lookup"><span data-stu-id="df153-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="df153-121">Bool ile gruplandırma</span><span class="sxs-lookup"><span data-stu-id="df153-121">Grouping by bool</span></span>

<span data-ttu-id="df153-122">Aşağıdaki örnek, sonuçları iki gruba bölmek için bir anahtar için bool değer kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="df153-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="df153-123">Değerin `group` yan tümcesindeki bir alt ifade tarafından üretildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df153-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="df153-124">Sayısal aralığa göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="df153-124">Grouping by numeric range</span></span>

<span data-ttu-id="df153-125">Sonraki örnek, bir yüzdebirlik aralığını temsil eden sayısal grup anahtarları oluşturmak için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="df153-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="df153-126">Yöntem çağrı sonucunu depolamak için uygun bir konum olarak [izin ver](let-clause.md) öğesinin kullanımını unutmayın. bu sayede yöntemi `group` yan tümcesinde iki kez çağırmak zorunda kalmazsınız.</span><span class="sxs-lookup"><span data-stu-id="df153-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="df153-127">Sorgu ifadelerinde yöntemleri güvenle kullanma hakkında daha fazla bilgi için bkz. [sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="df153-127">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="df153-128">Bileşik anahtarlara göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="df153-128">Grouping by composite keys</span></span>

<span data-ttu-id="df153-129">Öğeleri birden fazla anahtara göre gruplandırmak istediğinizde bileşik anahtar kullanın.</span><span class="sxs-lookup"><span data-stu-id="df153-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="df153-130">Anahtar öğesini tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak bileşik anahtar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="df153-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="df153-131">Aşağıdaki örnekte, bir sınıf `Person` `surname` ve `city`adlı üyelerle bildirildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="df153-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="df153-132">`group` yan tümcesi, aynı soyadı ve aynı şehirde bulunan her kişi kümesi için ayrı bir grubun oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="df153-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="df153-133">Sorgu değişkenini başka bir yönteme geçirmeniz gerekiyorsa adlandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="df153-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="df153-134">Anahtarlar için otomatik uygulanan özellikler kullanarak özel bir sınıf oluşturun ve ardından <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> yöntemlerini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="df153-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="df153-135">Ayrıca, bu yöntemleri kesin bir şekilde geçersiz kılmak zorunda değilsiniz bir yapı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df153-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="df153-136">Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [bir dizin ağacındaki yinelenen dosyaları sorgulama](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="df153-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="df153-137">İkinci makalede, adlandırılmış tür ile bileşik anahtarın nasıl kullanılacağını gösteren bir kod örneği bulunur.</span><span class="sxs-lookup"><span data-stu-id="df153-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="df153-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="df153-138">Example</span></span>

<span data-ttu-id="df153-139">Aşağıdaki örnek, gruplara ek sorgu mantığı uygulanırken kaynak verileri gruplara sıralamak için standart düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="df153-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="df153-140">Bu, devamlılık olmadan gruplandırma olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="df153-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="df153-141">Dizeler dizisindeki öğeler, ilk harfine göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="df153-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="df153-142">Sorgunun sonucu, `char` türünde ortak bir `Key` özelliği ve gruplandırmadaki her öğeyi içeren bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu içeren <xref:System.Linq.IGrouping%602> türüdür.</span><span class="sxs-lookup"><span data-stu-id="df153-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="df153-143">`group` yan tümcesinin sonucu bir dizi dizidir.</span><span class="sxs-lookup"><span data-stu-id="df153-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="df153-144">Bu nedenle, döndürülen her grup içindeki ayrı öğelere erişmek için, aşağıdaki örnekte gösterildiği gibi, döngü içinde, bir iç içe `foreach` döngüsünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="df153-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="df153-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="df153-145">Example</span></span>

<span data-ttu-id="df153-146">Bu örnek, `into`ile devam eden bir *devamlılığın* kullanıldığı gruplar üzerinde ek mantığın nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="df153-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="df153-147">Daha fazla bilgi için bkz [..](into.md)</span><span class="sxs-lookup"><span data-stu-id="df153-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="df153-148">Aşağıdaki örnek, her bir grubu yalnızca anahtar değerini bir sesli harf olarak seçmek üzere sorgular.</span><span class="sxs-lookup"><span data-stu-id="df153-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="df153-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df153-149">Remarks</span></span>

<span data-ttu-id="df153-150">Derleme zamanında, `group` yan tümceleri <xref:System.Linq.Enumerable.GroupBy%2A> yöntemine yapılan çağrılara çevrilir.</span><span class="sxs-lookup"><span data-stu-id="df153-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="df153-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df153-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="df153-152">Sorgu Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="df153-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="df153-153">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="df153-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="df153-154">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="df153-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="df153-155">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="df153-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="df153-156">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="df153-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
