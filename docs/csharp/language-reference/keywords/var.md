---
title: var-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d944cde932b5c1f5ef1439ee46a1447e107e6ac9
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053081"
---
# <a name="var-c-reference"></a><span data-ttu-id="ed999-102">var (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ed999-102">var (C# Reference)</span></span>

<span data-ttu-id="ed999-103">Visual C# 3,0 ' den başlayarak, yöntem kapsamında belirtilen değişkenlerin örtük bir "tür" türü olabilir `var` .</span><span class="sxs-lookup"><span data-stu-id="ed999-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="ed999-104">Örtük olarak yazılmış bir yerel değişken, türü kendi kendinize bildirdiyseniz olduğu gibi kesin şekilde yazılır, ancak derleyici türü belirler.</span><span class="sxs-lookup"><span data-stu-id="ed999-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="ed999-105">Aşağıdaki iki bildirimi `i` işlevsel olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="ed999-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="ed999-106">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve tür ilişkileri.</span><span class="sxs-lookup"><span data-stu-id="ed999-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed999-107">`var`Null yapılabilir başvuru türleri etkinken kullanıldığında, ifade türü null yapılabilir olmasa bile her zaman null yapılabilir bir başvuru türü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ed999-107">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="ed999-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed999-108">Example</span></span>

<span data-ttu-id="ed999-109">Aşağıdaki örnek iki sorgu ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed999-109">The following example shows two query expressions.</span></span> <span data-ttu-id="ed999-110">İlk ifadede öğesinin kullanımına `var` izin verilir, ancak sorgu sonucunun türü açıkça bir olarak belirtilemediğinden gerekli değildir `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="ed999-110">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="ed999-111">Ancak, ikinci ifadede, `var` sonucun anonim türlerin bir koleksiyonu olmasına izin verir ve bu türün adı derleyicinin kendisi hariç erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="ed999-111">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="ed999-112">Kullanımı, `var` sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ed999-112">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="ed999-113">Örneğin #2, `foreach` yineleme değişkeninin `item` de örtük olarak yazılmış olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ed999-113">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="ed999-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed999-114">See also</span></span>

- [<span data-ttu-id="ed999-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ed999-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ed999-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ed999-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ed999-117">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ed999-117">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
