---
description: var-C# başvurusu
title: var-C# başvurusu
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d04bea9bcf5be726d3e81a1a53abed31f59330a0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608718"
---
# <a name="var-c-reference"></a><span data-ttu-id="0d440-103">var (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0d440-103">var (C# reference)</span></span>

<span data-ttu-id="0d440-104">C# 3 ' ten başlayarak, yöntem kapsamında belirtilen değişkenlerin örtülü bir "tür" olması olabilir `var` .</span><span class="sxs-lookup"><span data-stu-id="0d440-104">Beginning with C# 3, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="0d440-105">Örtük olarak yazılmış bir yerel değişken, türü kendi kendinize bildirdiyseniz olduğu gibi kesin şekilde yazılır, ancak derleyici türü belirler.</span><span class="sxs-lookup"><span data-stu-id="0d440-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="0d440-106">Aşağıdaki iki bildirimi `i` işlevsel olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="0d440-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> <span data-ttu-id="0d440-107">`var` [Null yapılabilir başvuru türleri](../builtin-types/nullable-reference-types.md) etkinken kullanıldığında, ifade türü null yapılabilir olmasa bile her zaman null yapılabilir bir başvuru türü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0d440-107">When `var` is used with [nullable reference types](../builtin-types/nullable-reference-types.md) enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

<span data-ttu-id="0d440-108">`var`Anahtar sözcüğünün yaygın kullanımı, Oluşturucu çağırma ifadeleridir.</span><span class="sxs-lookup"><span data-stu-id="0d440-108">A common use of the `var` keyword is with constructor invocation expressions.</span></span> <span data-ttu-id="0d440-109">Kullanımı, `var` Aşağıdaki örnekte gösterildiği gibi değişken bildiriminde ve nesne örneklemede bir tür adı yinelemenize izin verir:</span><span class="sxs-lookup"><span data-stu-id="0d440-109">The use of `var` allows you to not repeat a type name in a variable declaration and object instantiation, as the following example shows:</span></span>

```csharp
var xs = new List<int>();
```

<span data-ttu-id="0d440-110">C# 9,0 ' den başlayarak, bir alternatif olarak, hedef türü belirtilmiş bir [ `new` ifade](../operators/new-operator.md) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d440-110">Beginning with C# 9.0, you can use a target-typed [`new` expression](../operators/new-operator.md) as an alternative:</span></span>

```csharp
List<int> xs = new();
List<int>? ys = new();
```

## <a name="example"></a><span data-ttu-id="0d440-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d440-111">Example</span></span>

<span data-ttu-id="0d440-112">Aşağıdaki örnek iki sorgu ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d440-112">The following example shows two query expressions.</span></span> <span data-ttu-id="0d440-113">İlk ifadede öğesinin kullanımına `var` izin verilir, ancak sorgu sonucunun türü açıkça bir olarak belirtilemediğinden gerekli değildir `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="0d440-113">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="0d440-114">Ancak, ikinci ifadede, `var` sonucun anonim türlerin bir koleksiyonu olmasına izin verir ve bu türün adı derleyicinin kendisi hariç erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="0d440-114">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="0d440-115">Kullanımı, `var` sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0d440-115">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="0d440-116">Örneğin #2, `foreach` yineleme değişkeninin `item` de örtük olarak yazılmış olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0d440-116">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="0d440-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d440-117">See also</span></span>

- [<span data-ttu-id="0d440-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0d440-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0d440-119">Örtük olarak yazılan yerel değişkenler</span><span class="sxs-lookup"><span data-stu-id="0d440-119">Implicitly typed local variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="0d440-120">LINQ sorgu işlemlerinde tür ilişkileri</span><span class="sxs-lookup"><span data-stu-id="0d440-120">Type relationships in LINQ query operations</span></span>](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
