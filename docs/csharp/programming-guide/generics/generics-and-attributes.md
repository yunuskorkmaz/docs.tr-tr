---
title: Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 0fe2d61001584aa7c175500bfa754b2ae2244660
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560431"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
Genel türler için öznitelikleri genel olmayan türleri aynı şekilde uygulanabilir. Öznitelikleri uygulama ile ilgili daha fazla bilgi için bkz: [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md).  
  
 Özel öznitelikler için hiçbir tür bağımsız değişkenleri sağlanan genel türler ve tüm tür parametreleri için bağımsız değişkenleri kapalı oluşturulan genel türler, açık genel türler başvurmak için yalnızca izin verilir.  
  
 Aşağıdaki örnekler, bu özel öznitelik kullanın:  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 Öznitelik, bir açık genel tür başvurabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Uygun sayıda virgül kullanarak birden çok tür parametreleri belirtin. Bu örnekte, `GenericClass2` iki tür parametreleri vardır:  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Öznitelik, kapalı bir oluşturulmuş genel tür başvurabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Genel tür parametresine başvuran bir öznitelik, bir derleme zamanı hatasına neden olur:  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Genel tür devralamaz <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Çalışma zamanında bir genel tür veya tür parametresi ile ilgili bilgi edinme yöntemlerini kullanabilirsiniz <xref:System.Reflection>. Daha fazla bilgi için [genel türler ve yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
- [Öznitelikler](../../../../docs/standard/attributes/index.md)
