---
title: Örtük olarak yazılan yerel değişkenler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 692a0f8ad933f3ba4bef50681cb3487fa0a7eea9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714832"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="eb1b3-102">Örtük olarak yazılan yerel değişkenlerC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="eb1b3-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="eb1b3-103">Yerel değişkenler açık bir tür vermeden bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="eb1b3-104">`var` anahtar sözcüğü, derleyiciye, başlatma deyiminin sağ tarafındaki ifadeden değişkenin türünü çıkarmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="eb1b3-105">Çıkarsanan tür bir yerleşik tür, anonim tür, Kullanıcı tanımlı tür veya .NET Framework sınıf kitaplığında tanımlanmış bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="eb1b3-106">Dizileri `var`ile başlatma hakkında daha fazla bilgi için, bkz. [örtülü olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="eb1b3-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="eb1b3-107">Aşağıdaki örneklerde, yerel değişkenlerin `var`ile bildirilebilecek çeşitli yolları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="eb1b3-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="eb1b3-108">`var` anahtar sözcüğünün "değişken" anlamına gelmeyeceğini ve değişkenin gevşek olarak yazılmış olduğunu veya geç bağlandığını belirtmeyeceğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="eb1b3-109">Yalnızca derleyicinin en uygun türü belirlediği ve atayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="eb1b3-110">`var` anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="eb1b3-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="eb1b3-111">Yerel değişkenlerde (Yöntem kapsamında belirtilen değişkenler) önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="eb1b3-112">[For](../../language-reference/keywords/for.md) Initialization ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="eb1b3-113">Bir [foreach](../../language-reference/keywords/foreach-in.md) başlatma bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="eb1b3-114">Bir [using](../../language-reference/keywords/using-statement.md) ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="eb1b3-115">Daha fazla bilgi için bkz. [bir sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="eb1b3-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="eb1b3-116">var ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="eb1b3-116">var and anonymous types</span></span>

<span data-ttu-id="eb1b3-117">Çoğu durumda `var` kullanımı isteğe bağlıdır ve yalnızca sözdizimsel bir kolaylık vardır.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="eb1b3-118">Ancak, bir değişken anonim bir türle başlatıldığında, nesnenin özelliklerine sonraki bir noktada erişmeniz gerekiyorsa değişkeni `var` olarak bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="eb1b3-119">Bu, LINQ sorgu ifadelerinde yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="eb1b3-120">Daha fazla bilgi için bkz. [anonim türler](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="eb1b3-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="eb1b3-121">Kaynak kodunuzun perspektifinden adsız bir türün adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="eb1b3-122">Bu nedenle, bir sorgu değişkeni `var`ile başlatılmışsa, nesne dizisinde döndürülen özelliklere erişmenin tek yolu, `foreach` deyimindeki yineleme değişkeninin türü olarak `var` kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="eb1b3-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb1b3-123">Remarks</span></span>

<span data-ttu-id="eb1b3-124">Aşağıdaki kısıtlamalar, örtük olarak belirlenmiş değişken bildirimleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="eb1b3-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="eb1b3-125">`var`, yalnızca yerel bir değişken aynı deyimde bildirildiği ve başlatıldığı zaman kullanılabilir; değişken null veya bir yöntem grubuna veya anonim işleve başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="eb1b3-126">`var` sınıf kapsamındaki alanlarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="eb1b3-127">`var` kullanılarak belirtilen değişkenler başlatma ifadesinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="eb1b3-128">Diğer bir deyişle, bu ifade geçerli: `int i = (i = 20);` ancak bu ifade derleme zamanı hatası veriyor: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="eb1b3-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="eb1b3-129">Birden çok örtük olarak yazılmış değişkenler aynı ifadede başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="eb1b3-130">`var` adlı bir tür kapsamdadır, `var` anahtar sözcüğü bu tür adına çözümlenir ve örtük olarak yazılmış bir yerel değişken bildiriminin parçası olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="eb1b3-131">`var` anahtar sözcüğüyle örtük yazma, yalnızca yerel Yöntem kapsamındaki değişkenlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="eb1b3-132">C# Derleyici, kodu işlediği bir mantıksal Paradox ile karşılaşacağından, sınıf alanları için örtülü yazma kullanılamaz: derleyicinin alanın türünü bilmesi gerekir, ancak atama ifadesi çözümlenene kadar türü belirleyemez ve ifade türü bilmeden değerlendirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="eb1b3-133">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="eb1b3-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="eb1b3-134">`bookTitles`, `var`türü verilen bir sınıf alanıdır.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="eb1b3-135">Alan değerlendirilecek bir ifadeye sahip olmadığı için derleyicinin ne tür `bookTitles` olması gerektiğini çıkarması olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="eb1b3-136">Ayrıca, alana bir ifade eklemek (yerel bir değişken gibi) de yeterli değildir:</span><span class="sxs-lookup"><span data-stu-id="eb1b3-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="eb1b3-137">Derleyici kod derleme sırasında alanlarla karşılaştığında, onunla ilişkili herhangi bir ifadeyi işlemeden önce her alanın türünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="eb1b3-138">Derleyici, `bookTitles`ayrıştırmaya çalışan aynı Paradox ile karşılaştığında: alanın türünü bilmesi gerekir, ancak derleyici, daha önce türü bilmeden mümkün olmayan ifadeyi analiz ederek normalde `var`türünü saptayabilir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="eb1b3-139">`var`, sorgu değişkeninin tam olarak oluşturulan türünün belirlenmesi zor olduğu sorgu ifadeleri ile de yararlı olabileceğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="eb1b3-140">Gruplandırma ve sıralama işlemlerinde bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="eb1b3-141">`var` anahtar sözcüğü, değişkenin belirli türü klavyede yazmak sıkıcı veya belirgin olduğunda ya da kodun okunabilirliğini eklememe olduğunda da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="eb1b3-142">Bu şekilde `var` yararlı olduğu bir örnek, Grup işlemleriyle kullanılanlar gibi iç içe geçmiş genel türlerdir.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="eb1b3-143">Aşağıdaki sorguda, sorgu değişkeninin türü `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="eb1b3-144">Siz ve kodunuzun bakımını yapmak zorunda olan başkaları bunu anlamış olduğu sürece, kolaylık ve kısaltma için örtük yazma kullanmayla ilgili bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="eb1b3-145">Ancak `var` kullanımı, kodunuzun diğer geliştiriciler için anlaşılması daha zor hale getirmek için en az olasılığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-145">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="eb1b3-146">Bu nedenle, C# belgeler yalnızca gerekli olduğunda `var` kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-146">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb1b3-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb1b3-147">See also</span></span>

- [<span data-ttu-id="eb1b3-148">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="eb1b3-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="eb1b3-149">Örtük Olarak Yazılan Diziler</span><span class="sxs-lookup"><span data-stu-id="eb1b3-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="eb1b3-150">Sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="eb1b3-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="eb1b3-151">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="eb1b3-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="eb1b3-152">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="eb1b3-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="eb1b3-153">var</span><span class="sxs-lookup"><span data-stu-id="eb1b3-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="eb1b3-154">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="eb1b3-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="eb1b3-155">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="eb1b3-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="eb1b3-156">for</span><span class="sxs-lookup"><span data-stu-id="eb1b3-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="eb1b3-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="eb1b3-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="eb1b3-158">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="eb1b3-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
