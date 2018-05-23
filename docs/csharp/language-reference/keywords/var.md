---
title: var (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: c311993ebcc5b5072959b2e79242bcdabd6de913
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="var-c-reference"></a><span data-ttu-id="62042-102">var (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="62042-102">var (C# Reference)</span></span>
<span data-ttu-id="62042-103">Visual C# 3. 0'den itibaren yöntemi kapsamda bildirilen değişkenler örtük bir "tür" olabilir `var`.</span><span class="sxs-lookup"><span data-stu-id="62042-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="62042-104">Türü örtük olarak belirlenmiş yerel değişken yalnızca kendiniz türü bildirilmedi, ancak türü derleyici belirler gibi kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="62042-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="62042-105">Aşağıdaki iki bildirimlerini `i` işlevsel olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="62042-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```csharp  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="62042-106">Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [LINQ Sorgu işlemlerinde tür ilişkileri](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="62042-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62042-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="62042-107">Example</span></span>  
 <span data-ttu-id="62042-108">Aşağıdaki örnekte, iki sorgu ifadeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="62042-108">The following example shows two query expressions.</span></span> <span data-ttu-id="62042-109">Kullanımını ilk ifadesinde `var` izin verilir, ancak sorgu sonuç türü olarak açıkça belirtilebilir gerekli olmadığı bir `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="62042-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="62042-110">Ancak, ikinci ifade içinde `var` anonim türler koleksiyonu bulunmasını sağlar ve bu tür adı derleyiciye dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="62042-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="62042-111">Kullanımı `var` sonucu için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="62042-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="62042-112">Örnek # 2'de unutmayın `foreach` yineleme değişkeni `item` da örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62042-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="62042-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62042-113">See Also</span></span>  
 [<span data-ttu-id="62042-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="62042-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="62042-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="62042-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="62042-116">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="62042-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
