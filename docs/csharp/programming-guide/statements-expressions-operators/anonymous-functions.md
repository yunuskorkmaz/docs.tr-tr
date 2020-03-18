---
title: Anonim fonksiyonlar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: cfb0190ee263e65e8130a8925f76357a382eafa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712006"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="e35b2-102">Anonim işlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e35b2-102">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="e35b2-103">Anonim işlev, temsilci türünün beklendiği her yerde kullanılabilecek bir "satır çizgisi" ifadesi veya ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="e35b2-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="e35b2-104">Adlandırılmış bir temsilciyi başlatmak veya yöntem parametresi olarak adlandırılmış temsilci türü yerine geçmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e35b2-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="e35b2-105">Anonim bir işlev oluşturmak için [lambda ifadesini](lambda-expressions.md) veya anonim bir [yöntemi](../../language-reference/operators/delegate-operator.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e35b2-105">You can use a [lambda expression](lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="e35b2-106">Lambda ifadelerini satır içinde kod yazmak için daha kısa ve anlamlı bir şekilde kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e35b2-106">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="e35b2-107">Anonim yöntemlerin aksine, bazı lambda ifadeleri türlerinde ifade ağacı türlerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e35b2-107">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="e35b2-108">C'de Delegelerin Evrimi\#</span><span class="sxs-lookup"><span data-stu-id="e35b2-108">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="e35b2-109">C# 1.0'da, kodun başka bir yerinde tanımlanan bir yöntemle açıkça baş harfe başlayarak bir temsilci örneği oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="e35b2-109">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="e35b2-110">C# 2.0, bir temsilci çağırmasında yürütülebilecek adsız satır lı ifade blokları yazmanın bir yolu olarak anonim yöntemler kavramını tanıttı.</span><span class="sxs-lookup"><span data-stu-id="e35b2-110">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="e35b2-111">C# 3.0 anonim yöntemlere benzer ama daha anlamlı ve özlü lambda ifadeler tanıttı.</span><span class="sxs-lookup"><span data-stu-id="e35b2-111">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="e35b2-112">Bu iki özellik topluca *anonim işlevler*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="e35b2-112">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="e35b2-113">Genel olarak, .NET Framework sürüm 3.5 ve daha sonrasını hedefleyen uygulamalar da lambda ifadeleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e35b2-113">In general, applications that target version 3.5 and later of the .NET Framework should use lambda expressions.</span></span>  
  
 <span data-ttu-id="e35b2-114">Aşağıdaki örnek, delege oluşturmanın C# 1.0'dan C# 3.0'a evrimini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e35b2-114">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e35b2-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e35b2-115">C# language specification</span></span>

<span data-ttu-id="e35b2-116">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e35b2-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e35b2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e35b2-117">See also</span></span>

- [<span data-ttu-id="e35b2-118">İfadeler, İfadeler ve Operatörler</span><span class="sxs-lookup"><span data-stu-id="e35b2-118">Statements, Expressions, and Operators</span></span>](./index.md)
- [<span data-ttu-id="e35b2-119">Lambda İfadeler</span><span class="sxs-lookup"><span data-stu-id="e35b2-119">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="e35b2-120">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e35b2-120">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="e35b2-121">İfade Ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="e35b2-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
