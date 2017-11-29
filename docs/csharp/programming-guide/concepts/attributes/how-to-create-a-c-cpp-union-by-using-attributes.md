---
title: "Nasıl yapılır: öznitelikleri (C#) kullanarak C C++ birleşimi oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 450fb922079ca6737b8db7754f25435b9c3b884b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Öznitelikleri](https://msdn.microsoft.com/library/5x6cd29c)  
 [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Özel öznitelikler (C#) oluşturma](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
