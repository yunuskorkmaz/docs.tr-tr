---
title: Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)
description: Yapı birimlerinin C# dilinde bellekte nasıl düzenlendiğini özelleştirmek için öznitelikleri nasıl kullanacağınızı öğrenin. Bu örnek, C/C++ ' dan bir birleşimin eşdeğerini uygular.
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925078"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="84fab-104">Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="84fab-104">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="84fab-105">Öznitelikleri kullanarak, yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84fab-105">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="84fab-106">Örneğin, ve özniteliklerini kullanarak C/C++ içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` `FieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="84fab-106">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="84fab-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="84fab-107">Example</span></span>

<span data-ttu-id="84fab-108">Bu kod kesiminde, tüm alanları `TestUnion` bellekte aynı konumda başlar.</span><span class="sxs-lookup"><span data-stu-id="84fab-108">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a><span data-ttu-id="84fab-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="84fab-109">Example</span></span>

<span data-ttu-id="84fab-110">Aşağıda, alanların farklı bir açık küme konumlarında başlayacağı başka bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="84fab-110">The following is another example where fields start at different explicitly set locations.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

<span data-ttu-id="84fab-111">İki tamsayı alanı `i1` ve `i2` aynı bellek konumlarını ile paylaşır `lg` .</span><span class="sxs-lookup"><span data-stu-id="84fab-111">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="84fab-112">Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="84fab-112">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="84fab-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84fab-113">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="84fab-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="84fab-114">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="84fab-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="84fab-115">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="84fab-116">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="84fab-116">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="84fab-117">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="84fab-117">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="84fab-118">Özel öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="84fab-118">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="84fab-119">Yansıma kullanarak özniteliklere erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="84fab-119">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
