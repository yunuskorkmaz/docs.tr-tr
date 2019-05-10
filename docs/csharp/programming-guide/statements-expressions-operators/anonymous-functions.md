---
title: Anonim işlevler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: c949bf5af441728b311391ecb42623951d0145ab
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608141"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="01386-102">Anonim İşlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="01386-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="01386-103">Bir anonim işlev bir "satır içi" deyimi veya bir temsilci türünün beklendiği her yerde kullanılabilir ifade ' dir.</span><span class="sxs-lookup"><span data-stu-id="01386-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="01386-104">Adlandırılmış bir temsilci başlatmak veya bir yöntem parametresi olarak bir adlandırılmış bir temsilci türü yerine geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01386-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="01386-105">Aşağıdaki konular, ayrı ayrı ele alınmıştır anonim İşlevler, iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="01386-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
- <span data-ttu-id="01386-106">[Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="01386-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
- [<span data-ttu-id="01386-107">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="01386-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="01386-108">Lambda ifadeleri ifade ağaçları ve temsilciler bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="01386-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="01386-109">C'de temsilciler evrimi\#</span><span class="sxs-lookup"><span data-stu-id="01386-109">The Evolution of Delegates in C\#</span></span>
 <span data-ttu-id="01386-110">C# 1. 0'bir temsilci örneğini açıkça, kod içinde başka bir yerde tanımlanmış bir yöntemle başlatarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="01386-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="01386-111">C# 2.0 içinde bir temsilci çağrısı yürütülebilecek Adlandırılmamış satır içi deyim blokları yazmak için bir yol olarak anonim yöntemler kavramını sundu.</span><span class="sxs-lookup"><span data-stu-id="01386-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="01386-112">Anonim yöntemler için kavram benzer, ancak daha ifadesel ve kısa olan lambda ifadeleri, C# 3.0 sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="01386-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="01386-113">Bu iki özellik topluca olarak bilinen *anonim işlevler*.</span><span class="sxs-lookup"><span data-stu-id="01386-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="01386-114">Genel olarak, hedefleyen uygulamalar sürüm 3.5 ve sonraki sürümlerinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lambda ifadeleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01386-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="01386-115">Aşağıdaki örnek, C# 3.0 için C# 1.0 temsilci oluşturma gelişimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="01386-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="01386-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="01386-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01386-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01386-117">See also</span></span>

- [<span data-ttu-id="01386-118">Deyimler, İfadeler ve İşleçler</span><span class="sxs-lookup"><span data-stu-id="01386-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [<span data-ttu-id="01386-119">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="01386-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="01386-120">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="01386-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="01386-121">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="01386-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
