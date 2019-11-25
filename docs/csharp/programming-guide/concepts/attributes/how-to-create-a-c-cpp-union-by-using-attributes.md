---
title: Öznitelikleri kullanarak C/C++ Union oluşturma ()C#
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141580"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="be943-102">Öznitelikleri kullanarak C/C++ Union oluşturma ()C#</span><span class="sxs-lookup"><span data-stu-id="be943-102">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="be943-103">Öznitelikleri kullanarak, yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be943-103">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="be943-104">Örneğin, `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` özniteliklerini kullanarak C/C++ içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be943-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="be943-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="be943-105">Example</span></span>

<span data-ttu-id="be943-106">Bu kod kesiminde, tüm `TestUnion` alanları bellekte aynı konumda başlar.</span><span class="sxs-lookup"><span data-stu-id="be943-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="be943-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="be943-107">Example</span></span>

<span data-ttu-id="be943-108">Aşağıda, alanların farklı bir açık küme konumlarında başlayacağı başka bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="be943-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="be943-109">İki tamsayı alanı `i1` ve `i2`, `lg` ile aynı bellek konumlarını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="be943-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="be943-110">Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="be943-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="be943-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be943-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="be943-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="be943-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="be943-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be943-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="be943-114">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="be943-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="be943-115">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="be943-115">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="be943-116">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="be943-116">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="be943-117">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="be943-117">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
