---
title: Öznitelikleri kullanarak C/C++ birleşimoluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141580"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="a3ac3-102">Öznitelikleri kullanarak C/C++ birleşimoluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="a3ac3-102">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="a3ac3-103">Öznitelikleri kullanarak, yapıların bellekte nasıl ortaya konuldurüldüni özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3ac3-103">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="a3ac3-104">Örneğin, C/C++'da birleşim olarak bilinen şeyi `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` özniteliklerini kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3ac3-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="a3ac3-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3ac3-105">Example</span></span>

<span data-ttu-id="a3ac3-106">Bu kod segmentinde, `TestUnion` tüm alanlar bellekte aynı konumda başlar.</span><span class="sxs-lookup"><span data-stu-id="a3ac3-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="a3ac3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3ac3-107">Example</span></span>

<span data-ttu-id="a3ac3-108">Aşağıda, alanların farklı şekilde ayarlanmış konumlarda başladığı başka bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a3ac3-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="a3ac3-109">İki tamsayı alanı `i1` ve `i2`, `lg`aynı bellek konumlarını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a3ac3-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="a3ac3-110">Platform çağırma kullanırken yapı düzeni üzerinde bu tür bir denetim yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a3ac3-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3ac3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3ac3-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="a3ac3-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a3ac3-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a3ac3-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3ac3-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="a3ac3-114">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="a3ac3-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="a3ac3-115">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="a3ac3-115">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="a3ac3-116">Özel Öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="a3ac3-116">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="a3ac3-117">Yansıma (C#) kullanarak Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="a3ac3-117">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
