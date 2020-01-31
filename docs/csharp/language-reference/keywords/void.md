---
title: void C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742765"
---
# <a name="void-c-reference"></a><span data-ttu-id="69125-102">void (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="69125-102">void (C# Reference)</span></span>

<span data-ttu-id="69125-103">Bir yöntem için dönüş türü olarak kullanıldığında, `void` metodun bir değer döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="69125-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="69125-104">metodun parametre listesinde `void` izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="69125-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="69125-105">Hiçbir parametre alan ve değer döndüren bir yöntem aşağıdaki şekilde bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="69125-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="69125-106">`void`, bilinmeyen bir tür için bir işaretçi bildirmek üzere güvenli olmayan bir bağlamda de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69125-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="69125-107">Daha fazla bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="69125-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="69125-108">`void`, .NET Framework <xref:System.Void?displayProperty=nameWithType> türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="69125-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="69125-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="69125-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="69125-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69125-110">See also</span></span>

- [<span data-ttu-id="69125-111">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="69125-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="69125-112">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="69125-112">C# keywords</span></span>](index.md)
- [<span data-ttu-id="69125-113">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="69125-113">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="69125-114">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="69125-114">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="69125-115">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="69125-115">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="69125-116">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="69125-116">Unsafe code and pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
