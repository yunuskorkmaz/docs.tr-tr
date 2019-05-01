---
title: 'Nasıl yapılır: (Visual Basic) öznitelikleri kullanarak C / C++ birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 0c3ebf248f5d2f20e2fff25fb8326a294b51d153
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789096"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Nasıl yapılır: Öznitelikler (Visual Basic) kullanarak bir C/C++ birleşimi oluşturma
Öznitelikleri kullanarak yapı birimleri bellekte nasıl düzenlenmiştir özelleştirebilirsiniz. Örneğin, olarak C/C++'ta bir birleşim kullanarak Bilineni oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` öznitelikleri.  
  
## <a name="example"></a>Örnek  
 Bu kesimdeki kod, tüm alanları `TestUnion` bellekte aynı konuma başlangıç.  
  
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
 Başka bir örnek farklı alanları başlangıcında konumları açıkça ayarlandığı verilmiştir.  
  
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
  
 İki tamsayı alanları `i1` ve `i2`, aynı bellek konumları olarak paylaşma `lg`. Platform çağırma kullanırken, bu tür bir yapı yerleşimi üzerinde denetim yararlı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Özel öznitelikler (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
