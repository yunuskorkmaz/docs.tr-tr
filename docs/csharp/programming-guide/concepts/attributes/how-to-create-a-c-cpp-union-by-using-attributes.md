---
title: 'Nasıl yapılır: öznitelikleri (C#) kullanarak C C++ birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 30a8be9021495aa4cf61010508762999cdf91ff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315847"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Nasıl yapılır: öznitelikleri (C#) kullanarak C/C++ birleşimi oluşturma
Öznitelikleri kullanarak yapılar bellekte nasıl düzenlenmiştir özelleştirebilirsiniz. Örneğin, kullanarak C/c++ birleşimi olarak Bilineni oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` öznitelikleri.  
  
## <a name="example"></a>Örnek  
 Bu kesimdeki kod, tüm alanları `TestUnion` bellek aynı konumda başlatın.  
  
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
 Başka bir örnek farklı alanları başlangıcında açıkça konumları belirlendiği verilmiştir.  
  
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
  
 İki tamsayı alanlarının `i1` ve `i2`, aynı bellek konumları olarak paylaşma `lg`. Platform çağırma kullanırken bu tür bir yapı düzeni denetime yararlıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Öznitelikler](../../../../../docs/standard/attributes/index.md)  
 [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Özel öznitelikler (C#) oluşturma](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
