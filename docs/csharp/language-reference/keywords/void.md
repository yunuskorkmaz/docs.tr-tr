---
title: void C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 465aaeadca603f14432478a7e5496a9ef4589ebe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712864"
---
# <a name="void-c-reference"></a><span data-ttu-id="9d74a-102">void (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9d74a-102">void (C# Reference)</span></span>

<span data-ttu-id="9d74a-103">Bir yöntem için dönüş türü olarak kullanıldığında, `void` metodun bir değer döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d74a-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="9d74a-104">metodun parametre listesinde `void` izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9d74a-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="9d74a-105">Hiçbir parametre alan ve değer döndüren bir yöntem aşağıdaki şekilde bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9d74a-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="9d74a-106">`void`, bilinmeyen bir tür için bir işaretçi bildirmek üzere güvenli olmayan bir bağlamda de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d74a-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="9d74a-107">Daha fazla bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="9d74a-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="9d74a-108">`void`, .NET Framework <xref:System.Void?displayProperty=nameWithType> türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="9d74a-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9d74a-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9d74a-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9d74a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d74a-110">See also</span></span>

- [<span data-ttu-id="9d74a-111">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9d74a-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9d74a-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9d74a-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9d74a-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9d74a-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9d74a-114">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="9d74a-114">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="9d74a-115">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="9d74a-115">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="9d74a-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d74a-116">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="9d74a-117">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="9d74a-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
