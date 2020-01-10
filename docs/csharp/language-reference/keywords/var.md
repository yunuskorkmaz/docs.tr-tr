---
title: var- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712890"
---
# <a name="var-c-reference"></a><span data-ttu-id="f415c-102">var (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f415c-102">var (C# Reference)</span></span>

<span data-ttu-id="f415c-103">Visual C# 3,0 ' den başlayarak, yöntem kapsamında belirtilen değişkenlerin örtük bir "tür" `var`olabilir.</span><span class="sxs-lookup"><span data-stu-id="f415c-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="f415c-104">Örtük olarak yazılmış bir yerel değişken, türü kendi kendinize bildirdiyseniz olduğu gibi kesin şekilde yazılır, ancak derleyici türü belirler.</span><span class="sxs-lookup"><span data-stu-id="f415c-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="f415c-105">Aşağıdaki iki `i` bildirimi işlevsel olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="f415c-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="f415c-106">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve tür ilişkileri.</span><span class="sxs-lookup"><span data-stu-id="f415c-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="f415c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f415c-107">Example</span></span>

<span data-ttu-id="f415c-108">Aşağıdaki örnek iki sorgu ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f415c-108">The following example shows two query expressions.</span></span> <span data-ttu-id="f415c-109">İlk ifadede `var` kullanımı izin verilir ancak gerekli değildir, çünkü sorgu sonucunun türü açıkça bir `IEnumerable<string>`olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f415c-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="f415c-110">Ancak, ikinci ifadede `var`, sonucun anonim türlerin bir koleksiyonu olmasına izin verir ve bu türün adı derleyicinin kendisi hariç erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="f415c-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="f415c-111">`var` kullanımı, sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f415c-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="f415c-112">Örnek #2, `foreach` yineleme değişkeni `item` de örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f415c-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="f415c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f415c-113">See also</span></span>

- [<span data-ttu-id="f415c-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="f415c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f415c-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f415c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f415c-116">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f415c-116">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
