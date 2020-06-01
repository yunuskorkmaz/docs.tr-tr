---
title: Anonim işlevler-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: c99aaf4f35d2d294a9f07de54129bb3b4fbfbfde
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241909"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="a1eac-102">Anonim işlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a1eac-102">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="a1eac-103">Anonim bir işlev, bir temsilci türünün beklendiği her yerde kullanılabilecek bir "satır içi" deyim veya ifadedir.</span><span class="sxs-lookup"><span data-stu-id="a1eac-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="a1eac-104">Adlandırılmış bir temsilciyi başlatmak veya bir yöntem parametresi olarak adlandırılmış bir temsilci türü yerine bunu geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1eac-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="a1eac-105">Anonim bir işlev oluşturmak için bir [lambda ifadesi](lambda-expressions.md) veya [anonim yöntem](../../language-reference/operators/delegate-operator.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1eac-105">You can use a [lambda expression](lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="a1eac-106">Satır içi kod yazmak için daha kısa ve açıklayıcı bir yol sağlayan lambda ifadeleri kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="a1eac-106">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="a1eac-107">Anonim yöntemlerin aksine, bazı lambda ifadesi türleri ifade ağacı türlerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="a1eac-107">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="a1eac-108">C 'deki temsilcilerin evrimi\#</span><span class="sxs-lookup"><span data-stu-id="a1eac-108">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="a1eac-109">C# 1,0 ' de, bir temsilcinin örneğini kodun başka bir yerinde tanımlanmış bir yöntemle açıkça başlatarak oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="a1eac-109">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="a1eac-110">C# 2,0, anonim yöntemler kavramını bir temsilci çağrısında yürütülebilecek adlandırılmamış satır içi deyimler yazmak için bir yol olarak getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1eac-110">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="a1eac-111">C# 3,0, anonim metotlar kavramı, ancak daha açıklayıcı ve kısa bir kavram gibi lambda ifadeleri getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1eac-111">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="a1eac-112">Bu iki özellik topluca *Anonim işlevler*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="a1eac-112">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="a1eac-113">Genel olarak, .NET Framework 3,5 veya sonraki bir sürümü hedefleyen uygulamalar Lambda ifadelerini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1eac-113">In general, applications that target .NET Framework 3.5 or later should use lambda expressions.</span></span>  
  
 <span data-ttu-id="a1eac-114">Aşağıdaki örnek, c# 1,0 ' den c# 3,0 ' e temsilci oluşturma gelişini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a1eac-114">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a1eac-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a1eac-115">C# language specification</span></span>

<span data-ttu-id="a1eac-116">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a1eac-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a1eac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1eac-117">See also</span></span>

- [<span data-ttu-id="a1eac-118">Deyimler, Ifadeler ve Işleçler</span><span class="sxs-lookup"><span data-stu-id="a1eac-118">Statements, Expressions, and Operators</span></span>](./index.md)
- [<span data-ttu-id="a1eac-119">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a1eac-119">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="a1eac-120">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a1eac-120">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="a1eac-121">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="a1eac-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
