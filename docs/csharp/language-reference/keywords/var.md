---
title: "var (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords: var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2be56243f9c4ddafb3903d14fa6d6f9cb0e2f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="var-c-reference"></a><span data-ttu-id="7360c-102">var (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7360c-102">var (C# Reference)</span></span>
<span data-ttu-id="7360c-103">Visual C# 3. 0'den itibaren yöntemi kapsamda bildirilen değişkenler örtük bir "tür" olabilir `var`.</span><span class="sxs-lookup"><span data-stu-id="7360c-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="7360c-104">Türü örtük olarak belirlenmiş yerel değişken yalnızca kendiniz türü bildirilmedi, ancak türü derleyici belirler gibi kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="7360c-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="7360c-105">Aşağıdaki iki bildirimlerini `i` işlevsel olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="7360c-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="7360c-106">Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [LINQ Sorgu işlemlerinde tür ilişkileri](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7360c-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7360c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="7360c-107">Example</span></span>  
 <span data-ttu-id="7360c-108">Aşağıdaki örnekte, iki sorgu ifadeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="7360c-108">The following example shows two query expressions.</span></span> <span data-ttu-id="7360c-109">Kullanımını ilk ifadesinde `var` izin verilir, ancak sorgu sonuç türü olarak açıkça belirtilebilir gerekli olmadığı bir `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="7360c-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="7360c-110">Ancak, ikinci ifade içinde `var` anonim tür koleksiyonu sonucu olduğundan ve bu tür adı derleyiciye dışında erişilemez kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7360c-110">However, in the second expression, `var` must be used because the result is a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="7360c-111">Örnek # 2'de unutmayın `foreach` yineleme değişkeni `item` da örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7360c-111">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7360c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7360c-112">See Also</span></span>  
 [<span data-ttu-id="7360c-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7360c-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7360c-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7360c-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7360c-115">Örtük olarak yazılan yerel değişkenler</span><span class="sxs-lookup"><span data-stu-id="7360c-115">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
