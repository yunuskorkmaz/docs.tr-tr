---
title: 'Nasıl yapılır: öznitelikleri kullanarak C-C + + birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: ebab0ad947f776932f9379af3969e369eeec1941
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400687"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Nasıl yapılır: öznitelikleri kullanarak C/C++ birleşimi oluşturma (Visual Basic)

Öznitelikleri kullanarak yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz. Örneğin, ve özniteliklerini kullanarak C/C++ içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` `FieldOffset` .

## <a name="example"></a>Örnek

Bu kod kesiminde, tüm alanları `TestUnion` bellekte aynı konumda başlar.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a>Örnek

Aşağıda, alanların farklı bir açık küme konumlarında başlayacağı başka bir örnek verilmiştir.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

İki tamsayı alanı `i1` ve `i2` aynı bellek konumlarını ile paylaşır `lg` . Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic Programlama Kılavuzu](../../index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (Visual Basic)](../reflection.md)
- [Öznitelikler (Visual Basic)](../../../language-reference/attributes.md)
- [Özel öznitelikler oluşturma (Visual Basic)](creating-custom-attributes.md)
- [Yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md)
