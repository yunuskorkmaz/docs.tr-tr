---
title: var - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: a523e575f14c88ea385bf115f0b07f54190499a5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633196"
---
# <a name="var-c-reference"></a><span data-ttu-id="9594c-102">var (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9594c-102">var (C# Reference)</span></span>

<span data-ttu-id="9594c-103">Visual C# 3.0 içinde başlayarak, yöntem kapsamda bildirilen değişkenler örtük bir "type" olabilir `var`.</span><span class="sxs-lookup"><span data-stu-id="9594c-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="9594c-104">Bir türü örtük olarak belirlenmiş yerel değişken alacağı yalnızca kendiniz türü bildirilen, ancak derleyicinin türü belirler kesin.</span><span class="sxs-lookup"><span data-stu-id="9594c-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="9594c-105">Aşağıdaki iki bildirimlerini `i` işlevsel olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="9594c-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="9594c-106">Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [LINQ Sorgu işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9594c-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="9594c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9594c-107">Example</span></span>

<span data-ttu-id="9594c-108">Aşağıdaki örnek, iki sorgu ifadeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="9594c-108">The following example shows two query expressions.</span></span> <span data-ttu-id="9594c-109">İlk ifadede, kullanımını `var` izin verilir, ancak sorgu sonuç türü olarak açıkça belirtilebilir gerekli olmadığından bir `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="9594c-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="9594c-110">Ancak, ikinci ifadede, `var` anonim türlerin koleksiyonunu olacak şekilde sonuç verir ve bu tür adı derleyici için dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="9594c-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="9594c-111">Kullanım `var` sonucu için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9594c-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="9594c-112">Örnek # 2'de unutmayın `foreach` yineleme değişkeni `item` de dolaylı olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9594c-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="9594c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9594c-113">See also</span></span>

- [<span data-ttu-id="9594c-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9594c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9594c-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9594c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9594c-116">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9594c-116">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
