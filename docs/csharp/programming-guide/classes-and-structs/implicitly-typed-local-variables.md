---
title: Örtük olarak yazılan yerel değişkenler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 9c6f7ae5d7a579abead2a62f8fdc7c63e5c53328
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646377"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="c2154-102">Örtük olarak yazılan yerel değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2154-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="c2154-103">Yerel değişkenler, açık bir tür vermeden bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2154-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="c2154-104">`var` Başlatma ifadesinin sağ tarafındaki ifade değişkenin türünü çıkarsamak için derleyicinin anahtar sözcüğü bildirir.</span><span class="sxs-lookup"><span data-stu-id="c2154-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="c2154-105">Çıkarsanan tür, yerleşik bir tür, anonim bir tür, kullanıcı tanımlı bir tür veya .NET Framework Sınıf Kitaplığı'nda tanımlı bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2154-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="c2154-106">Dizilerle başlatma hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="c2154-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="c2154-107">Aşağıdaki örnekler, yerel değişkenleri bildirilebilir ile çeşitli şekillerde `var`:</span><span class="sxs-lookup"><span data-stu-id="c2154-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="c2154-108">Kavramak önemlidir `var` anahtar sözcüğü, "değişken" anlamına gelmez ve değişken gevşek olduğunu göstermez yazılabilir veya geç bağlama.</span><span class="sxs-lookup"><span data-stu-id="c2154-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="c2154-109">Yalnızca derleyici belirler ve en uygun türde atar anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c2154-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="c2154-110">`var` Anahtar sözcüğü aşağıdaki bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c2154-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="c2154-111">Yerel değişkenlere (yöntemi kapsamında bildirilen değişkenler) önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c2154-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="c2154-112">İçinde bir [için](../../language-reference/keywords/for.md) başlatma ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c2154-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for(var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="c2154-113">İçinde bir [foreach](../../language-reference/keywords/foreach-in.md) başlatma ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c2154-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach(var item in list){...}
    ```

- <span data-ttu-id="c2154-114">İçinde bir [kullanarak](../../language-reference/keywords/using-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="c2154-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="c2154-115">Daha fazla bilgi için [nasıl yapılır: Kullanım türü örtük olarak belirlenmiş yerel değişkenleri ve dizileri sorgu ifadesinde](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="c2154-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="c2154-116">var ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="c2154-116">var and anonymous types</span></span>

<span data-ttu-id="c2154-117">Çoğu durumda kullanımını `var` isteğe bağlıdır ve yalnızca söz dizimsel kolaylık.</span><span class="sxs-lookup"><span data-stu-id="c2154-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="c2154-118">Ancak, bir değişken içeren bir anonim tür başlatıldığında olarak değişkeni bildirilmelidir `var` daha sonraki bir noktada nesnenin özelliklerini erişmeniz gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="c2154-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="c2154-119">Bu ortak senaryoda olan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="c2154-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="c2154-120">Daha fazla bilgi için [anonim türler](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="c2154-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="c2154-121">Kaynak kodunuzu açısından bakıldığında, anonim bir tür adı yok.</span><span class="sxs-lookup"><span data-stu-id="c2154-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="c2154-122">Bu nedenle, bir sorgu değişkeni ile başlatılmışsa `var`, döndürülen dizi nesnelerin özelliklerine erişmek için tek yolu kullanmaktır sonra `var` yineleme değişkeni türü olarak `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c2154-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="c2154-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2154-123">Remarks</span></span>

<span data-ttu-id="c2154-124">Türü örtük olarak belirlenmiş değişken bildirimleri için aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="c2154-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="c2154-125">`var` yerel bir değişken bildirildi ve aynı deyimde başlatıldı, yalnızca kullanılabilir; değişkeni, null ya da bir yöntem grubu ya da anonim bir işlevdir başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="c2154-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="c2154-126">`var` sınıf kapsamı alanları kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c2154-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="c2154-127">Kullanılarak bildirilen değişkenler `var` başlatma ifadesinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c2154-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="c2154-128">Diğer bir deyişle, bu ifade yasal`: int i = (i = 20);` ancak bu ifade bir derleme zamanı hatası oluşturur: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="c2154-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="c2154-129">Aynı deyimde birden fazla örtük olarak yazılan değişkenler başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="c2154-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="c2154-130">Adlı bir tür ise `var` kapsam içinde olan sonra `var` anahtar sözcüğü bu tür adı için çözümler ve bir örtük olarak belirlenmiş yerel değişken bildirimi bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="c2154-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="c2154-131">İlginizi çekebilecek `var` da yararlı sorgu ifadeleri tam olarak yapılandırılmış sorgu değişkeni türünü olduğu saptamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2154-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="c2154-132">Bu gruplandırma ve sıralama işlemleri ile ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="c2154-132">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="c2154-133">`var` Anahtar sözcüğü de yararlı olabilir değişkeni türünü yorucu bir süreç klavyede yazın veya açıktır veya kodun okunabilirliğini eklemez.</span><span class="sxs-lookup"><span data-stu-id="c2154-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="c2154-134">Bir örnek burada `var` bu yararlıdır şekilde olan grubu işlemleri ile Kullanılanlar gibi iç içe geçmiş genel türler.</span><span class="sxs-lookup"><span data-stu-id="c2154-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="c2154-135">Aşağıdaki sorguda, sorgu değişkeninin türü olduğu `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="c2154-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="c2154-136">Siz ve kodunuzu korumalıdır başkalarının bunu anlamak sürece örtülü yazma convenience ve kısaltma için kullanma konusunda sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="c2154-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="c2154-137">Ancak, kullanımını `var` kodunuzu anlamak için diğer geliştiriciler daha zor hale getirmek için olası en az yok.</span><span class="sxs-lookup"><span data-stu-id="c2154-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="c2154-138">Bu nedenle, genellikle C# belgeleri kullanan `var` yalnızca gerekli olduğunda.</span><span class="sxs-lookup"><span data-stu-id="c2154-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2154-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2154-139">See also</span></span>

- [<span data-ttu-id="c2154-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c2154-140">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="c2154-141">Örtük Olarak Yazılan Diziler</span><span class="sxs-lookup"><span data-stu-id="c2154-141">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="c2154-142">Nasıl yapılır: Kullanım yerel değişkenleri ve dizileri sorgu ifadesinde örtük</span><span class="sxs-lookup"><span data-stu-id="c2154-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="c2154-143">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="c2154-143">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="c2154-144">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="c2154-144">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="c2154-145">var</span><span class="sxs-lookup"><span data-stu-id="c2154-145">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="c2154-146">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c2154-146">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
- [<span data-ttu-id="c2154-147">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="c2154-147">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="c2154-148">for</span><span class="sxs-lookup"><span data-stu-id="c2154-148">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="c2154-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="c2154-149">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="c2154-150">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="c2154-150">using Statement</span></span>](../../language-reference/keywords/using-statement.md)