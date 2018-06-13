---
title: Parametreleri Geçirme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323111"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="5e92f-102">Parametreleri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5e92f-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="5e92f-103">C# ' ta bağımsız değişken parametreleri değere veya başvuruya göre geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e92f-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="5e92f-104">Başvuruya göre geçirme etkinleştirir işlevi üyeleri, yöntemler, özellikler, dizin oluşturucular, işleçler ve parametre değerini değiştirin ve bu değişikliği oluşturucular arama ortamda kalır.</span><span class="sxs-lookup"><span data-stu-id="5e92f-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="5e92f-105">Bir parametre değeri değiştirmenin amacıyla başvuruya geçirmek için kullanmak `ref`, veya `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5e92f-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="5e92f-106">Kopyalama ancak değerini değiştirmeyi değil önleme amacıyla başvuruya geçirmek için kullanmak `in` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5e92f-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="5e92f-107">Basitlik, yalnızca için `ref` anahtar sözcüğü, bu konudaki örnekler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="5e92f-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="5e92f-108">Arasındaki farklar hakkında daha fazla bilgi için `in`, `ref`, ve `out`, bkz: [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md), ve [ Dizileri kullanma ref ve out geçirme](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="5e92f-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="5e92f-109">Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e92f-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="5e92f-110">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="5e92f-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5e92f-111">Değer Türü Parametrelerini Geçirme</span><span class="sxs-lookup"><span data-stu-id="5e92f-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="5e92f-112">Başvuru Türü Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="5e92f-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5e92f-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5e92f-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e92f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e92f-114">See Also</span></span>  
 [<span data-ttu-id="5e92f-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5e92f-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5e92f-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5e92f-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
