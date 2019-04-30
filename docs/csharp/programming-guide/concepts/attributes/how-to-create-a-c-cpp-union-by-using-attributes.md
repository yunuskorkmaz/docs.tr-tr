---
title: 'Nasıl yapılır: Öznitelikleri kullanarak C / C++ birleşimi oluşturma (C#)'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: a8b902536cd09ac732bf2144536605a66b5bbc56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703068"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Nasıl yapılır: Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)
Öznitelikleri kullanarak yapı birimleri bellekte nasıl düzenlenmiştir özelleştirebilirsiniz. Örneğin, olarak C/C++'ta bir birleşim kullanarak Bilineni oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` öznitelikleri.  
  
## <a name="example"></a>Örnek  
 Bu kesimdeki kod, tüm alanları `TestUnion` bellekte aynı konuma başlangıç.  
  
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
 Başka bir örnek farklı alanları başlangıcında konumları açıkça ayarlandığı verilmiştir.  
  
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
  
 İki tamsayı alanları `i1` ve `i2`, aynı bellek konumları olarak paylaşma `lg`. Platform çağırma kullanırken, bu tür bir yapı yerleşimi üzerinde denetim yararlı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
- [Öznitelikler](../../../../../docs/standard/attributes/index.md)
- [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)
- [Öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)
- [Özel öznitelikler (C#) oluşturma](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
