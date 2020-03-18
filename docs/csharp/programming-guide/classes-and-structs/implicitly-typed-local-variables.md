---
title: Örtülü olarak yazılan yerel değişkenler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399828"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="16909-102">Örtülü olarak yazılan yerel değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="16909-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="16909-103">Yerel değişkenler açık bir tür vermeden bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="16909-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="16909-104">Anahtar `var` kelime, derleyiciye, başlatma deyiminin sağ tarafındaki ifadeden değişkenin türünü çıkarmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="16909-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="16909-105">Çıkarılan tür yerleşik bir tür, anonim bir tür, kullanıcı tanımlı bir tür veya .NET Framework sınıf kitaplığında tanımlanan bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="16909-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="16909-106">Dizileri `var`nasıl başharfe çevireceklerine ilişkin daha fazla bilgi için [bkz.](../arrays/implicitly-typed-arrays.md)</span><span class="sxs-lookup"><span data-stu-id="16909-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="16909-107">Aşağıdaki örnekler, yerel değişkenlerin aşağıdakilerle `var`bildirilebileceği çeşitli yolları göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="16909-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="16909-108">Anahtar kelimenin `var` "varyant" anlamına gelmediğini ve değişkenin gevşek veya geç bağlı olduğunu göstermediğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="16909-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="16909-109">Bu sadece derleyici belirler ve en uygun türü atar anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="16909-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="16909-110">Anahtar `var` kelime aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="16909-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="16909-111">Önceki örnekte gösterildiği gibi yerel değişkenler (yöntem kapsamında bildirilen değişkenler) üzerinde.</span><span class="sxs-lookup"><span data-stu-id="16909-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="16909-112">Başlangıç bildirimi [için.](../../language-reference/keywords/for.md)</span><span class="sxs-lookup"><span data-stu-id="16909-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="16909-113">[Foreach](../../language-reference/keywords/foreach-in.md) başlatma deyiminde.</span><span class="sxs-lookup"><span data-stu-id="16909-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="16909-114">Bir [açıklama kullanarak.](../../language-reference/keywords/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="16909-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="16909-115">Daha fazla bilgi için, [sorgu ifadesinde örtülü olarak yazılan yerel değişkenleri ve dizileri nasıl kullanacağız'](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)a bakın.</span><span class="sxs-lookup"><span data-stu-id="16909-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="16909-116">var ve anonim türleri</span><span class="sxs-lookup"><span data-stu-id="16909-116">var and anonymous types</span></span>

<span data-ttu-id="16909-117">Birçok durumda kullanımı `var` isteğe bağlıdır ve sadece bir sözdizimsiz kolaylıktır.</span><span class="sxs-lookup"><span data-stu-id="16909-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="16909-118">Ancak, bir değişken anonim bir türle başharfe `var` atıldığında, değişkeni daha sonraki bir noktada nesnenin özelliklerine erişmeniz gerekiyormuş gibi bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16909-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="16909-119">Bu, LINQ sorgu ifadelerinde sık karşılaşılan bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="16909-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="16909-120">Daha fazla bilgi için [Bkz. Anonim Türler.](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="16909-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="16909-121">Kaynak kodunuz açısından, anonim bir türün adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="16909-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="16909-122">Bu nedenle, bir sorgu değişkeni `var`ile başharfe vurulmuşsa, nesnelerin döndürülen dizisindeki `var` özelliklere erişmenin tek yolu `foreach` deyimdeki yineleme değişkeninin türü olarak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="16909-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="16909-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16909-123">Remarks</span></span>

<span data-ttu-id="16909-124">Aşağıdaki kısıtlamalar örtülü olarak yazılan değişken bildirimleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="16909-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="16909-125">`var`yalnızca yerel bir değişken aynı ifadede beyan edilip başharfe geçtiğinde kullanılabilir; değişken null veya bir yöntem grubu veya anonim bir işlev için başharf olamaz.</span><span class="sxs-lookup"><span data-stu-id="16909-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="16909-126">`var`sınıf kapsamındaki alanlarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16909-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="16909-127">Initialization ifadesinde `var` kullanılarak bildirilen değişkenler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16909-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="16909-128">Başka bir deyişle, bu `int i = (i = 20);` ifade yasaldır: ancak bu ifade derleme zamanı hatası üretir:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="16909-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="16909-129">Aynı ifadede birden çok örtük olarak yazılan değişken ler baş harfe çevrilemez.</span><span class="sxs-lookup"><span data-stu-id="16909-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="16909-130">Adlandırılmış `var` bir tür kapsamdaysa, `var` anahtar kelime bu tür adına çözülür ve örtülü olarak yazılan yerel değişken bildiriminin bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="16909-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="16909-131">`var` Anahtar kelimeile örtülü yazma yalnızca yerel yöntem kapsamındaki değişkenlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="16909-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="16909-132">C# derleyicisi kodu işlediği için mantıksal bir paradoksla karşılaşacağı için sınıf alanları için örtük yazma kullanılamaz: derleyicinin alanın türünü bilmesi gerekir, ancak atama ifadesi çözümlenene kadar türünü belirleyemez ve ifade türünü bilmeden değerlendirilemez.</span><span class="sxs-lookup"><span data-stu-id="16909-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="16909-133">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="16909-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="16909-134">`bookTitles`türü `var`verilen bir sınıf alanıdır.</span><span class="sxs-lookup"><span data-stu-id="16909-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="16909-135">Alanın değerlendirilecek bir ifadesi olmadığından, derleyicinin ne tür `bookTitles` olması gerektiği hakkında bilgi alması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="16909-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="16909-136">Buna ek olarak, alana bir ifade eklemek (yerel bir değişken için yaptığınız gibi) da yetersizdir:</span><span class="sxs-lookup"><span data-stu-id="16909-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="16909-137">Derleyici kod derlemesi sırasında alanlarla karşılaştığında, onunla ilişkili ifadeleri işlemeden önce her alanın türünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="16909-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="16909-138">Derleyici ayrıştırmaya çalışırken aynı paradoksla karşılaşır `bookTitles`: alanın türünü bilmesi gerekir, ancak derleyici `var`normalde ifadeyi analiz ederek 'ın türünü belirler, bu da önceden türünü bilmeden mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="16909-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="16909-139">Sorgu değişkeninin tam olarak oluşturulmuş türünü belirlemenin zor olduğu sorgu ifadeleri ile de yararlı `var` olabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16909-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="16909-140">Bu gruplandırma ve sıralama işlemleri ile oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="16909-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="16909-141">Anahtar `var` kelime, değişkenin belirli türü klavyede yazmak için can sıkıcı olduğunda veya açık olduğunda veya kodun okunabilirliğine katkıda bulunmuyorsa da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="16909-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="16909-142">Bu şekilde `var` yararlı olduğu bir örnek, grup işlemleriile kullanılanlar gibi iç içe genel türleri ile.</span><span class="sxs-lookup"><span data-stu-id="16909-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="16909-143">Aşağıdaki sorguda, sorgu değişkeninin `IEnumerable<IGrouping<string, Student>>`türü .</span><span class="sxs-lookup"><span data-stu-id="16909-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="16909-144">Siz ve kodunuzu korumanız gereken diğer kişiler bunu anladığınız sürece, kolaylık ve kısalık için örtülü yazıyazmakta bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="16909-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="16909-145">Kullanımı, `var` kodunuzu basitleştirmeye yardımcı olur, ancak kullanımı gerekli olduğu durumlarda veya kodunuzu okunmasını kolaylaştırdığında kısıtlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16909-145">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="16909-146">Ne zaman düzgün kullanılacağı `var` hakkında daha fazla bilgi için, C# Kodlama Yönergeleri makalesinde [Örtük olarak yazılan yerel değişkenler](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16909-146">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="16909-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16909-147">See also</span></span>

- [<span data-ttu-id="16909-148">C# Referans</span><span class="sxs-lookup"><span data-stu-id="16909-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="16909-149">Örtük Olarak Yazılan Diziler</span><span class="sxs-lookup"><span data-stu-id="16909-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="16909-150">Sorgu ifadesinde örtülü olarak yazılan yerel değişkenler ve diziler nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="16909-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="16909-151">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="16909-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="16909-152">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="16909-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="16909-153">var</span><span class="sxs-lookup"><span data-stu-id="16909-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="16909-154">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="16909-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="16909-155">LINQ (Dil-Entegre Sorgu)</span><span class="sxs-lookup"><span data-stu-id="16909-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="16909-156">Için</span><span class="sxs-lookup"><span data-stu-id="16909-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="16909-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="16909-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="16909-158">Ekstresi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="16909-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
