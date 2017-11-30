---
title: "Örtülü Olarak Yazılan Yerel Değişkenler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26a4460acf70ff3748f12d74442f0ca568a587b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="1b69c-102">Örtülü Olarak Yazılan Yerel Değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1b69c-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="1b69c-103">Yerel değişkenler bir açık tür vermeden bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1b69c-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="1b69c-104">`var` Anahtar sözcüğü başlatma ifadesinin sağ tarafında ifadesinden değişkeninin türü gerçekleştirip derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b69c-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="1b69c-105">Çıkarılan türü, yerleşik bir tür, anonim bir tür, kullanıcı tanımlı bir tür veya .NET Framework Sınıf Kitaplığı'nda tanımlanan bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b69c-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="1b69c-106">Dizilerle başlatma hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1b69c-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="1b69c-107">Aşağıdaki örnekler, yerel değişkenleri bildirilebilir ile çeşitli şekillerde `var`:</span><span class="sxs-lookup"><span data-stu-id="1b69c-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="1b69c-108">Anlamak önemlidir `var` anahtar sözcüğü "değişken" gelmez ve değişken geniş olduğunu göstermez yazılan veya geç bağlama.</span><span class="sxs-lookup"><span data-stu-id="1b69c-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="1b69c-109">Yalnızca derleyici belirler ve en uygun türe atar anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1b69c-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="1b69c-110">`var` Anahtar sözcüğünü aşağıdaki bağlamlarında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="1b69c-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="1b69c-111">Yerel değişkenler (yöntemi kapsamda bildirilen değişkenlerin) üzerinde önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1b69c-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="1b69c-112">İçinde bir [için](../../../csharp/language-reference/keywords/for.md) başlatma deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b69c-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="1b69c-113">İçinde bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) başlatma deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b69c-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="1b69c-114">İçinde bir [kullanarak](../../../csharp/language-reference/keywords/using-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b69c-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="1b69c-115">Daha fazla bilgi için bkz: [nasıl yapılır: kullanım örtük olarak yazılan yerel değişkenler ve bir sorgu ifadesinde dizileri](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="1b69c-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="1b69c-116">var ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="1b69c-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="1b69c-117">Çoğunda kullanımını durumlarda `var` isteğe bağlıdır ve yalnızca söz dizimi kolaylık sağlamak.</span><span class="sxs-lookup"><span data-stu-id="1b69c-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="1b69c-118">Ancak, bir değişkene sahip anonim bir tür başlatıldığında değişkeni olarak bildirilmelidir `var` sonraki bir zamanda nesnenin özelliklerini erişmeniz gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="1b69c-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="1b69c-119">Yaygın bir senaryo budur [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="1b69c-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="1b69c-120">Daha fazla bilgi için bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="1b69c-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="1b69c-121">Kaynak kodunuz perspektifinden anonim bir tür adı yok.</span><span class="sxs-lookup"><span data-stu-id="1b69c-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="1b69c-122">Bu nedenle, bir sorgu değişkeni ile başlatılmışsa `var`, döndürülen sırada nesnelerin özelliklerine erişmek için tek yolu kullanmaktır sonra `var` yineleme değişkeni türü olarak `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b69c-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="1b69c-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b69c-123">Remarks</span></span>  
 <span data-ttu-id="1b69c-124">Değişken bildirimleri örtük olarak yazılan aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="1b69c-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="1b69c-125">`var`yerel bir değişken bildirilen ve aynı deyiminde başlatılmış yalnızca kullanılabilir; Değişken null ya da bir yöntem Grup ya da adsız bir işlev başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b69c-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="1b69c-126">`var`sınıf kapsamı alanlarını kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b69c-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="1b69c-127">Kullanarak bildirilen değişkenlerin `var` başlatma ifadede kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b69c-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="1b69c-128">Bu ifade başka bir deyişle, yasal`: int i = (i = 20);` ancak bu ifade bir derleme zamanı hatası oluşturur:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="1b69c-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="1b69c-129">Birden çok örtük olarak yazılan değişkenler aynı deyiminde başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b69c-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="1b69c-130">Bir tür adlandırırsanız `var` kapsam içinde sonra `var` anahtar sözcüğü bu tür adı çözülür ve bir örtük olarak yazılan yerel değişken bildirimi bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="1b69c-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="1b69c-131">Bulabilirsiniz `var` sorgu değişkeni tam oluşturulan türünü olduğu belirlemek zor sorgu ifadelerle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b69c-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="1b69c-132">Bu işlemleri sıralama ve Gruplama ile ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="1b69c-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="1b69c-133">`var` Anahtar sözcüğü da yararlı olabilir değişkeni belirli türünü klavyede yazmak sıkıcı veya açık olduğunda veya kod okunabilirliğini eklemez.</span><span class="sxs-lookup"><span data-stu-id="1b69c-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="1b69c-134">Bir örneği burada `var` bu yararlıdır şekilde olan Grup işlemleriyle Kullanılanlar gibi iç içe geçmiş genel türler.</span><span class="sxs-lookup"><span data-stu-id="1b69c-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="1b69c-135">Aşağıdaki sorguda, sorgu değişkeni türüdür `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="1b69c-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="1b69c-136">Sizin ve kodunuzu korumalıdır başkalarının bu anlamak sürece, kolaylık sağlamak ve kısaltma için örtük yazarak kullanarak herhangi bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="1b69c-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="1b69c-137">Ancak, kullanımını `var` kodunuzu diğer geliştiriciler için anlaşılması daha zor hale getirmek için olası en az yok.</span><span class="sxs-lookup"><span data-stu-id="1b69c-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="1b69c-138">Bu nedenle, genellikle C# belgeleri kullanan `var` yalnızca gerekli olduğu zaman.</span><span class="sxs-lookup"><span data-stu-id="1b69c-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b69c-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b69c-139">See Also</span></span>  
 [<span data-ttu-id="1b69c-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1b69c-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1b69c-141">Örtük olarak yazılan diziler</span><span class="sxs-lookup"><span data-stu-id="1b69c-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="1b69c-142">Nasıl yapılır: Kullanım türü örtük olarak belirlenmiş yerel değişkenleri ve dizileri sorgu ifadesinde</span><span class="sxs-lookup"><span data-stu-id="1b69c-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="1b69c-143">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="1b69c-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="1b69c-144">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="1b69c-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="1b69c-145">var</span><span class="sxs-lookup"><span data-stu-id="1b69c-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="1b69c-146">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1b69c-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="1b69c-147">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="1b69c-147">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="1b69c-148">için</span><span class="sxs-lookup"><span data-stu-id="1b69c-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="1b69c-149">foreach,</span><span class="sxs-lookup"><span data-stu-id="1b69c-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="1b69c-150">using deyimi</span><span class="sxs-lookup"><span data-stu-id="1b69c-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
