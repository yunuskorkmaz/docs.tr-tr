---
title: Örtük olarak yazılan yerel değişkenler-C# Programlama Kılavuzu
description: C# ' deki var anahtar sözcüğü, derleyicinin başlangıç deyiminin sağ tarafındaki ifadeden değişkenin türünü çıkarmasını söyler.
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 6badb8588dedda80227ab38bee027cf2890c8672
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864221"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="30cc7-103">Örtük olarak yazılan yerel değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="30cc7-103">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="30cc7-104">Yerel değişkenler açık bir tür vermeden bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="30cc7-104">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="30cc7-105">`var`Anahtar sözcüğü, derleyiciye, başlatma deyiminin sağ tarafındaki ifadeden değişkenin türünü çıkarmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="30cc7-105">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="30cc7-106">Çıkarsanan tür yerleşik bir tür, anonim tür, Kullanıcı tanımlı tür veya .NET sınıf kitaplığı 'nda tanımlanmış bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-106">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET class library.</span></span> <span data-ttu-id="30cc7-107">İle dizileri başlatma hakkında daha fazla bilgi için `var` bkz. [örtülü olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="30cc7-107">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="30cc7-108">Aşağıdaki örneklerde, yerel değişkenlerin ile bildirilebilecek çeşitli yollar gösterilmektedir `var` :</span><span class="sxs-lookup"><span data-stu-id="30cc7-108">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="30cc7-109">`var`Anahtar sözcüğünün "varyant" anlamına gelmeyeceğini ve değişkenin gevşek olarak yazılmış olduğunu veya geç bağlandığını belirtmeyeceğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-109">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="30cc7-110">Yalnızca derleyicinin en uygun türü belirlediği ve atayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-110">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="30cc7-111">`var`Anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="30cc7-111">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="30cc7-112">Yerel değişkenlerde (Yöntem kapsamında belirtilen değişkenler) önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="30cc7-112">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="30cc7-113">[For](../../language-reference/keywords/for.md) Initialization ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="30cc7-113">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="30cc7-114">Bir [foreach](../../language-reference/keywords/foreach-in.md) başlatma bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="30cc7-114">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="30cc7-115">Bir [using](../../language-reference/keywords/using-statement.md) ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="30cc7-115">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="30cc7-116">Daha fazla bilgi için bkz. [bir sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="30cc7-116">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="30cc7-117">var ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="30cc7-117">var and anonymous types</span></span>

<span data-ttu-id="30cc7-118">Çoğu durumda, kullanımı `var` isteğe bağlıdır ve yalnızca sözdizimsel bir kolaylık vardır.</span><span class="sxs-lookup"><span data-stu-id="30cc7-118">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="30cc7-119">Ancak, bir değişken anonim bir türle başlatıldığında, `var` nesnenin özelliklerine sonraki bir noktada erişmeniz gerekiyorsa değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-119">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="30cc7-120">Bu, LINQ sorgu ifadelerinde yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="30cc7-120">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="30cc7-121">Daha fazla bilgi için bkz. [anonim türler](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="30cc7-121">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="30cc7-122">Kaynak kodunuzun perspektifinden adsız bir türün adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="30cc7-122">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="30cc7-123">Bu nedenle, bir sorgu değişkeni ile başlatılmış ise `var` , nesne dizisinde döndürülen özelliklere erişmenin tek yolu, `var` deyimindeki yineleme değişkeninin türü olarak kullanmaktır `foreach` .</span><span class="sxs-lookup"><span data-stu-id="30cc7-123">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="30cc7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30cc7-124">Remarks</span></span>

<span data-ttu-id="30cc7-125">Aşağıdaki kısıtlamalar, örtük olarak belirlenmiş değişken bildirimleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="30cc7-125">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="30cc7-126">`var`yalnızca yerel bir değişken aynı deyimde bildirildiği ve başlatıldığı zaman kullanılabilir; değişken null veya bir yöntem grubuna veya anonim işleve başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="30cc7-126">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="30cc7-127">`var`sınıf kapsamındaki alanlarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30cc7-127">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="30cc7-128">Kullanılarak belirtilen değişkenler `var` başlatma ifadesinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30cc7-128">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="30cc7-129">Diğer bir deyişle, bu ifade geçerlidir: `int i = (i = 20);` ancak bu ifade derleme zamanı hatası oluşturur:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="30cc7-129">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="30cc7-130">Birden çok örtük olarak yazılmış değişkenler aynı ifadede başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="30cc7-130">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="30cc7-131">Adlandırılmış bir tür `var` kapsamdadır, `var` anahtar sözcüğü bu tür adına çözümlenir ve örtük olarak yazılmış bir yerel değişken bildiriminin parçası olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="30cc7-131">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="30cc7-132">Anahtar sözcükle örtük yazma `var` yalnızca yerel Yöntem kapsamındaki değişkenlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-132">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="30cc7-133">C# derleyicisi kod işlendiği için bir mantıksal Paradox ile karşılaşacağından, sınıf alanları için örtük yazma kullanılamaz: derleyicinin alanın türünü bilmesi gerekir, ancak atama ifadesi çözümlenene kadar türü belirleyemez ve ifade türü bilmeden değerlendirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="30cc7-133">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="30cc7-134">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="30cc7-134">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="30cc7-135">`bookTitles`, türü verilen bir sınıf alanıdır `var` .</span><span class="sxs-lookup"><span data-stu-id="30cc7-135">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="30cc7-136">Alanın değerlendirilecek bir ifadesi olmadığından, derleyicinin ne tür olması gerektiğini çıkarması olanaksızdır `bookTitles` .</span><span class="sxs-lookup"><span data-stu-id="30cc7-136">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="30cc7-137">Ayrıca, alana bir ifade eklemek (yerel bir değişken gibi) de yeterli değildir:</span><span class="sxs-lookup"><span data-stu-id="30cc7-137">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="30cc7-138">Derleyici kod derleme sırasında alanlarla karşılaştığında, onunla ilişkili herhangi bir ifadeyi işlemeden önce her alanın türünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="30cc7-138">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="30cc7-139">Derleyici ayrıştırmaya çalışan aynı Paradox ile karşılaştığında `bookTitles` : alanın türünü bilmesi gerekir, ancak derleyici, bu türü `var` önceden bilmeden ifadeyi analiz ederek normalde türünü tespit edecektir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-139">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="30cc7-140">`var`Sorgu değişkeninin tam olarak oluşturulan türünün belirlenmesi zor olduğu sorgu ifadeleri ile de yararlı olabileceğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30cc7-140">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="30cc7-141">Gruplandırma ve sıralama işlemlerinde bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-141">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="30cc7-142">`var`Anahtar sözcüğü, değişkenin belirli türü klavyede yazmak sıkıcı veya belirgin olduğunda ya da kodun okunabilirliğini eklememe olduğunda da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-142">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="30cc7-143">`var`Bu şekilde yararlı olduğu bir örnek, Grup işlemleriyle kullanılanlar gibi iç içe geçmiş genel türlerdir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-143">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="30cc7-144">Aşağıdaki sorguda, sorgu değişkeninin türü `IEnumerable<IGrouping<string, Student>>` .</span><span class="sxs-lookup"><span data-stu-id="30cc7-144">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="30cc7-145">Siz ve kodunuzun bakımını yapmak zorunda olan başkaları bunu anlamış olduğu sürece, kolaylık ve kısaltma için örtük yazma kullanmayla ilgili bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="30cc7-145">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="30cc7-146">Kullanımı, `var` kodunuzun basitleştirilmesine yardımcı olur, ancak kullanımı gereken durumlarda veya kodunuzun daha kolay okunması durumunda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="30cc7-146">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="30cc7-147">Düzgün olarak ne zaman kullanılacağı hakkında daha fazla bilgi için `var` C# kodlama yönergeleri makalesindeki [örtülü olarak yazılan yerel değişkenler](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="30cc7-147">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="30cc7-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30cc7-148">See also</span></span>

- [<span data-ttu-id="30cc7-149">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="30cc7-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="30cc7-150">Türü Örtük Olarak Belirlenmiş Diziler</span><span class="sxs-lookup"><span data-stu-id="30cc7-150">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="30cc7-151">Sorgu ifadesinde türü örtük olarak belirlenmiş yerel değişkenleri ve dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="30cc7-151">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="30cc7-152">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="30cc7-152">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="30cc7-153">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="30cc7-153">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="30cc7-154">var</span><span class="sxs-lookup"><span data-stu-id="30cc7-154">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="30cc7-155">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="30cc7-155">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="30cc7-156">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="30cc7-156">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="30cc7-157">:</span><span class="sxs-lookup"><span data-stu-id="30cc7-157">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="30cc7-158">foreach, in</span><span class="sxs-lookup"><span data-stu-id="30cc7-158">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="30cc7-159">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="30cc7-159">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
