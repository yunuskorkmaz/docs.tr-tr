---
description: var-C# başvurusu
title: var-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141718"
---
# <a name="var-c-reference"></a><span data-ttu-id="da13e-103">var (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="da13e-103">var (C# Reference)</span></span>

<span data-ttu-id="da13e-104">Visual C# 3,0 ' den başlayarak, yöntem kapsamında belirtilen değişkenlerin örtük bir "tür" türü olabilir `var` .</span><span class="sxs-lookup"><span data-stu-id="da13e-104">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="da13e-105">Örtük olarak yazılmış bir yerel değişken, türü kendi kendinize bildirdiyseniz olduğu gibi kesin şekilde yazılır, ancak derleyici türü belirler.</span><span class="sxs-lookup"><span data-stu-id="da13e-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="da13e-106">Aşağıdaki iki bildirimi `i` işlevsel olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="da13e-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="da13e-107">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve tür ilişkileri.</span><span class="sxs-lookup"><span data-stu-id="da13e-107">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="da13e-108">`var`Null yapılabilir başvuru türleri etkinken kullanıldığında, ifade türü null yapılabilir olmasa bile her zaman null yapılabilir bir başvuru türü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="da13e-108">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="da13e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="da13e-109">Example</span></span>

<span data-ttu-id="da13e-110">Aşağıdaki örnek iki sorgu ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="da13e-110">The following example shows two query expressions.</span></span> <span data-ttu-id="da13e-111">İlk ifadede öğesinin kullanımına `var` izin verilir, ancak sorgu sonucunun türü açıkça bir olarak belirtilemediğinden gerekli değildir `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="da13e-111">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="da13e-112">Ancak, ikinci ifadede, `var` sonucun anonim türlerin bir koleksiyonu olmasına izin verir ve bu türün adı derleyicinin kendisi hariç erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="da13e-112">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="da13e-113">Kullanımı, `var` sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="da13e-113">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="da13e-114">Örneğin #2, `foreach` yineleme değişkeninin `item` de örtük olarak yazılmış olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="da13e-114">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="da13e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da13e-115">See also</span></span>

- [<span data-ttu-id="da13e-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="da13e-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="da13e-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="da13e-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="da13e-118">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="da13e-118">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
