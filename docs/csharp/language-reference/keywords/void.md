---
title: void - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: ce52e4d19335db0e21637b87bbd1589c86c06ae1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613134"
---
# <a name="void-c-reference"></a><span data-ttu-id="e4b72-102">void (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e4b72-102">void (C# Reference)</span></span>

<span data-ttu-id="e4b72-103">Bir yöntem için dönüş türü olarak kullanıldığında `void` yöntemi bir değer döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4b72-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="e4b72-104">`void` bir yöntemin parametre listesinde izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="e4b72-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="e4b72-105">Hiçbir parametre almayan ve hiçbir değer döndürmeyen bir yöntem şu şekilde bildirilir:</span><span class="sxs-lookup"><span data-stu-id="e4b72-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="e4b72-106">`void` Ayrıca güvenli olmayan bir bağlamda, bir işaretçi türü bilinmiyor bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4b72-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="e4b72-107">Daha fazla bilgi için [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="e4b72-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="e4b72-108">`void` .NET Framework için bir diğer addır <xref:System.Void?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="e4b72-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e4b72-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e4b72-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e4b72-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4b72-110">See also</span></span>

- [<span data-ttu-id="e4b72-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e4b72-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e4b72-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e4b72-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e4b72-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e4b72-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e4b72-114">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="e4b72-114">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="e4b72-115">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="e4b72-115">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="e4b72-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e4b72-116">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="e4b72-117">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="e4b72-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)