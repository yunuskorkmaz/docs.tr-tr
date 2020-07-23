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
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)

Öznitelikleri kullanarak, yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz. Örneğin, ve özniteliklerini kullanarak C/C++ içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` `FieldOffset` .

## <a name="example"></a>Örnek

Bu kod kesiminde, tüm alanları `TestUnion` bellekte aynı konumda başlar.

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

## <a name="example"></a>Örnek

Aşağıda, alanların farklı bir açık küme konumlarında başlayacağı başka bir örnek verilmiştir.

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

İki tamsayı alanı `i1` ve `i2` aynı bellek konumlarını ile paylaşır `lg` . Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler (C#)](index.md)
- [Özel öznitelikler oluşturma (C#)](creating-custom-attributes.md)
- [Yansıma kullanarak özniteliklere erişme (C#)](accessing-attributes-by-using-reflection.md)
