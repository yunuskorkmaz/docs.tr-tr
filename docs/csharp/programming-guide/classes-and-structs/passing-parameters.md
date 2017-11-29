---
title: "Parametreleri Geçirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="8481f-102">Parametreleri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8481f-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="8481f-103">C# ' ta bağımsız değişken parametreleri değere veya başvuruya göre geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8481f-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="8481f-104">Başvuruya göre geçirme etkinleştirir işlevi üyeleri, yöntemler, özellikler, dizin oluşturucular, işleçler ve parametre değerini değiştirin ve bu değişikliği oluşturucular arama ortamda kalır.</span><span class="sxs-lookup"><span data-stu-id="8481f-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="8481f-105">Başvuruya göre bir parametre geçirmek için kullanmak `ref` veya `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8481f-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="8481f-106">Basitlik, yalnızca için `ref` anahtar sözcüğü, bu konudaki örnekler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="8481f-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="8481f-107">Arasındaki farklar hakkında daha fazla bilgi için `ref` ve `out`, bkz: [ref](../../../csharp/language-reference/keywords/ref.md), [çıkışı](../../../csharp/language-reference/keywords/out.md), ve [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="8481f-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="8481f-108">Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8481f-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="8481f-109">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="8481f-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="8481f-110">Değer türü parametrelerini geçirme</span><span class="sxs-lookup"><span data-stu-id="8481f-110">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="8481f-111">Başvuru türü parametreleri geçirme</span><span class="sxs-lookup"><span data-stu-id="8481f-111">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="8481f-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8481f-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8481f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8481f-113">See Also</span></span>  
 [<span data-ttu-id="8481f-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8481f-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8481f-115">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="8481f-115">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
