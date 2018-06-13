---
title: Anonim İşlevler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 51a3c2e8399fdaae19ebe33f0d9ecc4bfd598799
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321853"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="381c9-102">Anonim İşlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="381c9-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="381c9-103">Adsız bir işlev bir "satır içi" deyimi veya bir temsilci türü bekleniyor her yerde kullanılabilir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="381c9-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="381c9-104">Adlandırılmış bir temsilci başlatmak veya bir yöntem parametresi olarak adlandırılan temsilci türü yerine geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="381c9-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="381c9-105">Aşağıdaki konular, ayrı ayrı ele alınan anonim işlevler iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="381c9-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="381c9-106">[Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="381c9-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="381c9-107">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="381c9-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="381c9-108">Lambda ifadeleri ifade ağaçları ve temsilciler bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="381c9-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="381c9-109">C# temsilciler evrimi</span><span class="sxs-lookup"><span data-stu-id="381c9-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="381c9-110">C# 1. 0'açıkça, başka bir yerde kodunda tanımlandığına bir yöntem ile başlatarak temsilcisi örneği oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="381c9-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="381c9-111">C# 2.0 kavramı anonim yöntemler, bir temsilci çağrısının yürütülebilecek Adlandırılmamış satır içi deyim blokları yazmak için bir yol olarak kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="381c9-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="381c9-112">C# 3.0 anonim yöntemler için kavram benzer, ancak daha açıklayıcı ve kısa lambda ifadeleri sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="381c9-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="381c9-113">Bu iki özellik topluca olarak bilinen *anonim işlevler*.</span><span class="sxs-lookup"><span data-stu-id="381c9-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="381c9-114">Genel olarak, uygulamalar, hedef sürüm 3.5 ve sonraki [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lambda ifadeleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="381c9-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="381c9-115">Aşağıdaki örnek, C# 1.0 temsilci oluşturulması C# 3.0 evrimi gösterir:</span><span class="sxs-lookup"><span data-stu-id="381c9-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="381c9-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="381c9-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="381c9-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="381c9-117">See Also</span></span>  
 [<span data-ttu-id="381c9-118">Deyimler, İfadeler ve İşleçler</span><span class="sxs-lookup"><span data-stu-id="381c9-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [<span data-ttu-id="381c9-119">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="381c9-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="381c9-120">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="381c9-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="381c9-121">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="381c9-121">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
