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
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Öznitelikleri kullanarak C/C++ birleşimoluşturma (C#)

Öznitelikleri kullanarak, yapıların bellekte nasıl ortaya konuldurüldüni özelleştirebilirsiniz. Örneğin, C/C++'da birleşim olarak bilinen şeyi `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` özniteliklerini kullanarak oluşturabilirsiniz.

## <a name="example"></a>Örnek

Bu kod segmentinde, `TestUnion` tüm alanlar bellekte aynı konumda başlar.

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

Aşağıda, alanların farklı şekilde ayarlanmış konumlarda başladığı başka bir örnek verilmiştir.

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

İki tamsayı alanı `i1` ve `i2`, `lg`aynı bellek konumlarını paylaşır. Platform çağırma kullanırken yapı düzeni üzerinde bu tür bir denetim yararlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler (C#)](index.md)
- [Özel Öznitelikler oluşturma (C#)](creating-custom-attributes.md)
- [Yansıma (C#) kullanarak Özniteliklere Erişim](accessing-attributes-by-using-reflection.md)
