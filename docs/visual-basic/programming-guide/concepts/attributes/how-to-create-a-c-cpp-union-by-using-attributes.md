---
title: 'Nasıl yapılır: öznitelikleri kullanarak CC++ birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: acb8dc781e2872ae46e5aa058a98b3dd98f3e064
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349493"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Nasıl yapılır: öznitelikleri kullanarak C/C++ Union oluşturma (Visual Basic)

Öznitelikleri kullanarak yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz. Örneğin, `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` özniteliklerini kullanarak C/C++ içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz.

## <a name="example"></a>Örnek

Bu kod kesiminde, tüm `TestUnion` alanları bellekte aynı konumda başlar.

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

İki tamsayı alanı `i1` ve `i2`, `lg`ile aynı bellek konumlarını paylaşır. Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Özel öznitelikler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Yansıma kullanarak özniteliklere erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
