---
title: Parametreler - geçirme C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 3e205ecba48df69c0e7f289ad8201765b35d5767
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238149"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="253d1-102">Parametreleri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="253d1-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="253d1-103">C# ' ta bağımsız değişkenler parametrelerini değere veya başvuruya göre geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="253d1-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="253d1-104">Çağıran ortama oluşturucular parametreleri değiştirin ve değişikliği kalıcı hale getirmek ve başvuruya göre geçirme işlev üyeleri, yöntemleri, özellikleri, Dizinleyicileri, işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="253d1-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="253d1-105">Değer değiştirme hedefi ile başvuruya göre bir parametre geçirmek için kullanmak `ref`, veya `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="253d1-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="253d1-106">Başvuru değiştirme değeri değil ancak kopyalama önleme amacıyla geçirmek için kullanmak `in` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="253d1-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="253d1-107">Kolaylık olması için yalnızca `ref` anahtar sözcüğü, bu konudaki örneklerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="253d1-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="253d1-108">Arasındaki fark hakkında daha fazla bilgi için `in`, `ref`, ve `out`, bkz: [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), ve [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="253d1-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="253d1-109">Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="253d1-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="253d1-110">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="253d1-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="253d1-111">Değer Türü Parametrelerini Geçirme</span><span class="sxs-lookup"><span data-stu-id="253d1-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="253d1-112">Başvuru Türü Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="253d1-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="253d1-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="253d1-113">C# Language Specification</span></span>  

<span data-ttu-id="253d1-114">Daha fazla bilgi için [bağımsız değişken listeleri](~/_csharplang/spec/expressions.md#argument-lists) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="253d1-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="253d1-115">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="253d1-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="253d1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="253d1-116">See Also</span></span>

- [<span data-ttu-id="253d1-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="253d1-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="253d1-118">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="253d1-118">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
