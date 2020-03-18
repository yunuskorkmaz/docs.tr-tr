---
title: grup yan tümcesi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713466"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="529f1-102">group tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="529f1-102">group clause (C# Reference)</span></span>

<span data-ttu-id="529f1-103">Yan `group` tümce, <xref:System.Linq.IGrouping%602> grup için anahtar değeriyle eşleşen sıfır veya daha fazla öğe içeren bir nesne dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="529f1-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="529f1-104">Örneğin, her dizedeki ilk harfe göre bir dize dizisini gruplandırmayapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="529f1-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="529f1-105">Bu durumda, ilk harf anahtardır ve bir tür [char](../builtin-types/char.md)vardır `Key` ve her <xref:System.Linq.IGrouping%602> nesnenin özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="529f1-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="529f1-106">Derleyici anahtarın türünü çıkartıyor.</span><span class="sxs-lookup"><span data-stu-id="529f1-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="529f1-107">Bir sorgu ifadesini aşağıdaki `group` örnekte gösterildiği gibi bir yan tümceyle sonlandırmak için:</span><span class="sxs-lookup"><span data-stu-id="529f1-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="529f1-108">Her grupta ek sorgu işlemleri gerçekleştirmek istiyorsanız, [bağlamsal](into.md) anahtar sözcüğü kullanarak geçici bir tanımlayıcı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="529f1-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="529f1-109">Kullandığınızda, `into`sorguya devam etmeli ve sonunda aşağıdaki alıntıda `select` gösterildiği `group` gibi bir deyim veya başka bir yan tümceyle sonlandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="529f1-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="529f1-110">Bu makalenin Örnek `group` bölümünde, `into` ile ve olmadan kullanımı daha eksiksiz örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="529f1-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="529f1-111">Grup sorgusunun sonuçlarını derecelendirme</span><span class="sxs-lookup"><span data-stu-id="529f1-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="529f1-112">Sorgu <xref:System.Linq.IGrouping%602> `group` tarafından üretilen nesneler aslında bir liste listesi olduğundan, her gruptaki öğelere erişmek için iç içe geçen bir [döngü](foreach-in.md) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="529f1-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="529f1-113">Dış döngü grup anahtarları üzerinde yineler ve iç döngü grubun kendisindeki her öğenin üzerinde yineler.</span><span class="sxs-lookup"><span data-stu-id="529f1-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="529f1-114">Bir grubun anahtarı olabilir, ancak öğe yoktur.</span><span class="sxs-lookup"><span data-stu-id="529f1-114">A group may have a key but no elements.</span></span> <span data-ttu-id="529f1-115">Önceki kod `foreach` örneklerinde sorguyu yürüten döngü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="529f1-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="529f1-116">Anahtar türleri</span><span class="sxs-lookup"><span data-stu-id="529f1-116">Key types</span></span>

<span data-ttu-id="529f1-117">Grup anahtarları, dize, yerleşik sayısal tür veya kullanıcı tanımlı adlandırılmış tür veya anonim tür gibi herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="529f1-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="529f1-118">Dize göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="529f1-118">Grouping by string</span></span>

<span data-ttu-id="529f1-119">Önceki kod örnekleri `char`nde bir .</span><span class="sxs-lookup"><span data-stu-id="529f1-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="529f1-120">Bunun yerine bir dize tuşu kolayca belirtilmiş olabilir, örneğin soyadının tamamı:</span><span class="sxs-lookup"><span data-stu-id="529f1-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="529f1-121">Bool'a göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="529f1-121">Grouping by bool</span></span>

<span data-ttu-id="529f1-122">Aşağıdaki örnek, sonuçları iki gruba ayırmak için bir anahtar için bool değerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="529f1-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="529f1-123">Değerin `group` yan tümcedeki bir alt ifade yle üretildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="529f1-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="529f1-124">Sayısal aralıkla gruplandırma</span><span class="sxs-lookup"><span data-stu-id="529f1-124">Grouping by numeric range</span></span>

<span data-ttu-id="529f1-125">Sonraki örnek, yüzdelik aralığını temsil eden sayısal grup anahtarları oluşturmak için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="529f1-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="529f1-126">Bir yöntem arama sonucunu depolamak için uygun bir konum olarak izin verme nin kullanımına dikkat edin, böylece metodu yan tümcede iki kez çağırmak zorunda kalmamalısınız. [let](let-clause.md) `group`</span><span class="sxs-lookup"><span data-stu-id="529f1-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="529f1-127">Sorgu ifadelerinde yöntemlerin güvenli bir şekilde nasıl kullanılacağı hakkında daha fazla bilgi için sorgu [ifadelerinde özel durumları ele'ye](../../linq/handle-exceptions-in-query-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="529f1-127">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="529f1-128">Bileşik tuşlara göre gruplandırma</span><span class="sxs-lookup"><span data-stu-id="529f1-128">Grouping by composite keys</span></span>

<span data-ttu-id="529f1-129">Öğeleri birden fazla anahtara göre gruplandırmak istediğinizde bileşik anahtar kullanın.</span><span class="sxs-lookup"><span data-stu-id="529f1-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="529f1-130">Anahtar öğesini tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak bileşik bir anahtar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="529f1-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="529f1-131">Aşağıdaki örnekte, bir sınıfın `Person` adlandırılmış `surname` üyelerle `city`birlikte bildirildiğini varsayalım ve .</span><span class="sxs-lookup"><span data-stu-id="529f1-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="529f1-132">Yan `group` tümce, her bir ad ve aynı şehre sahip kişiler için ayrı bir grup oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="529f1-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="529f1-133">Sorgu değişkenini başka bir yönteme geçirmeniz gerekiyorsa, adlandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="529f1-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="529f1-134">Tuşlar için otomatik olarak uygulanan özellikleri kullanarak özel bir <xref:System.Object.Equals%2A> sınıf <xref:System.Object.GetHashCode%2A> oluşturun ve ardından bu ve yöntemleri geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="529f1-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="529f1-135">Ayrıca bir yapı kullanabilirsiniz, bu durumda kesinlikle bu yöntemleri geçersiz kılmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="529f1-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="529f1-136">Daha fazla bilgi için, [otomatik olarak uygulanan özelliklere sahip hafif bir sınıfın nasıl uygulanacağını](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [dizin ağacında yinelenen dosyaları nasıl sorgulayabilirsiniz'a](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="529f1-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="529f1-137">İkinci makalede, adlandırılmış bir türe sahip bileşik anahtarın nasıl kullanılacağını gösteren bir kod örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="529f1-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="529f1-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="529f1-138">Example</span></span>

<span data-ttu-id="529f1-139">Aşağıdaki örnek, gruplara ek sorgu mantığı uygulanmadığında kaynak verileri gruplara sıralamak için standart deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="529f1-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="529f1-140">Buna devamı olmayan bir gruplama denir.</span><span class="sxs-lookup"><span data-stu-id="529f1-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="529f1-141">Dizeleri bir dizi elemanları ilk harfe göre gruplanır.</span><span class="sxs-lookup"><span data-stu-id="529f1-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="529f1-142">Sorgunun sonucu, tür <xref:System.Linq.IGrouping%602> `Key` `char` ve gruplandırmadaki her öğeyi içeren bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyon içeren bir türdür.</span><span class="sxs-lookup"><span data-stu-id="529f1-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="529f1-143">Bir `group` yan tümcenin sonucu diziler dizisidir.</span><span class="sxs-lookup"><span data-stu-id="529f1-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="529f1-144">Bu nedenle, döndürülen her grup içindeki tek `foreach` tek öğelere erişmek için, aşağıdaki örnekte gösterildiği gibi, grup anahtarlarını yineleyen döngü içinde iç içe bir döngü kullanın.</span><span class="sxs-lookup"><span data-stu-id="529f1-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="529f1-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="529f1-145">Example</span></span>

<span data-ttu-id="529f1-146">Bu örnek, '' ile bir *devamı* kullanarak, bunları oluşturduktan `into`sonra gruplar üzerinde ek mantık gerçekleştirmek için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="529f1-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="529f1-147">Daha fazla bilgi için [bkz.](into.md)</span><span class="sxs-lookup"><span data-stu-id="529f1-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="529f1-148">Aşağıdaki örnek, yalnızca anahtar değeri sesli harf olan kişileri seçmek için her grubu sorgular.</span><span class="sxs-lookup"><span data-stu-id="529f1-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="529f1-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="529f1-149">Remarks</span></span>

<span data-ttu-id="529f1-150">Derleme zamanında, `group` yan tümceler <xref:System.Linq.Enumerable.GroupBy%2A> yönteme yapılan çağrılara çevrilir.</span><span class="sxs-lookup"><span data-stu-id="529f1-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="529f1-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="529f1-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="529f1-152">Sorgu Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="529f1-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="529f1-153">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="529f1-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="529f1-154">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="529f1-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="529f1-155">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="529f1-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="529f1-156">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="529f1-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
