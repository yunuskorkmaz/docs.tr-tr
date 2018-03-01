---
title: "void (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a71cac30132417abce60cdde54322b5f2067d39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="void-c-reference"></a><span data-ttu-id="eb1e0-102">void (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eb1e0-102">void (C# Reference)</span></span>
<span data-ttu-id="eb1e0-103">Bir yöntemi, dönüş türü olarak kullanıldığında `void` yöntemi bir değer döndürmüyor belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb1e0-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="eb1e0-104">`void`bir yöntemin parametre listesinde izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="eb1e0-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="eb1e0-105">Hiçbir parametre alan ve herhangi bir değer döndüren bir yöntem aşağıdaki gibi bildirilmiş:</span><span class="sxs-lookup"><span data-stu-id="eb1e0-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="eb1e0-106">`void`Ayrıca güvensiz bir bağlamda bilinmeyen bir tür için bir işaretçi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb1e0-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="eb1e0-107">Daha fazla bilgi için bkz: [işaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="eb1e0-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="eb1e0-108">`void`.NET Framework için bir diğer ad olduğu <xref:System.Void?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="eb1e0-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eb1e0-109">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="eb1e0-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eb1e0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb1e0-110">See also</span></span>
 [<span data-ttu-id="eb1e0-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="eb1e0-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="eb1e0-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb1e0-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eb1e0-113">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="eb1e0-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="eb1e0-114">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="eb1e0-114">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="eb1e0-115">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="eb1e0-115">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="eb1e0-116">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="eb1e0-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="eb1e0-117">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="eb1e0-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
