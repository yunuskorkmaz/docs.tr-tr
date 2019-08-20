---
title: 'Nasıl yapılır: Öznitelikleri (C#) kullanarakC++ C birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: fdadc9505b93f40c66001ac36345efada2edd270
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595365"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Nasıl yapılır: Öznitelikleri kullanarak C/C++ Union oluşturma (C#)
Öznitelikleri kullanarak yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz. Örneğin,C++ `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` özniteliklerini kullanarak C/içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz.  
  
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
  
 İki tamsayı alanı `i1` ve `i2`aynı bellek konumlarını `lg`ile paylaşır. Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler (C#)](./index.md)
- [Özel öznitelikler (C#) oluşturma](./creating-custom-attributes.md)
- [Yansıma (C#) kullanarak özniteliklere erişme](./accessing-attributes-by-using-reflection.md)
