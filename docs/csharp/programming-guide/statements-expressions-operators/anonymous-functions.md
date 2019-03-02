---
title: Anonim işlevler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: f7ab471514cd437b7b1816d7e0bde30459f281a9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203330"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="560e9-102">Anonim İşlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="560e9-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="560e9-103">Bir anonim işlev bir "satır içi" deyimi veya bir temsilci türünün beklendiği her yerde kullanılabilir ifade ' dir.</span><span class="sxs-lookup"><span data-stu-id="560e9-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="560e9-104">Adlandırılmış bir temsilci başlatmak veya bir yöntem parametresi olarak bir adlandırılmış bir temsilci türü yerine geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="560e9-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="560e9-105">Aşağıdaki konular, ayrı ayrı ele alınmıştır anonim İşlevler, iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="560e9-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="560e9-106">[Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="560e9-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="560e9-107">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="560e9-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="560e9-108">Lambda ifadeleri ifade ağaçları ve temsilciler bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="560e9-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="560e9-109">C'de temsilciler evrimi\#</span><span class="sxs-lookup"><span data-stu-id="560e9-109">The Evolution of Delegates in C\#</span></span>
 <span data-ttu-id="560e9-110">C# 1. 0'bir temsilci örneğini açıkça, kod içinde başka bir yerde tanımlanmış bir yöntemle başlatarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="560e9-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="560e9-111">C# 2.0 içinde bir temsilci çağrısı yürütülebilecek Adlandırılmamış satır içi deyim blokları yazmak için bir yol olarak anonim yöntemler kavramını sundu.</span><span class="sxs-lookup"><span data-stu-id="560e9-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="560e9-112">Anonim yöntemler için kavram benzer, ancak daha ifadesel ve kısa olan lambda ifadeleri, C# 3.0 sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="560e9-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="560e9-113">Bu iki özellik topluca olarak bilinen *anonim işlevler*.</span><span class="sxs-lookup"><span data-stu-id="560e9-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="560e9-114">Genel olarak, hedefleyen uygulamalar sürüm 3.5 ve sonraki sürümlerinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lambda ifadeleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="560e9-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="560e9-115">Aşağıdaki örnek, C# 3.0 için C# 1.0 temsilci oluşturma gelişimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="560e9-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="560e9-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="560e9-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="560e9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="560e9-117">See also</span></span>

- [<span data-ttu-id="560e9-118">Deyimler, İfadeler ve İşleçler</span><span class="sxs-lookup"><span data-stu-id="560e9-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [<span data-ttu-id="560e9-119">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="560e9-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="560e9-120">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="560e9-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="560e9-121">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="560e9-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
