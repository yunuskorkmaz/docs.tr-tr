---
title: Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 3bfb4028fb5efce693abd83b40636b0149962e3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
Öznitelikler genel türleri için genel olmayan türleri aynı şekilde uygulanabilir. Öznitelikleri uygulama ile ilgili daha fazla bilgi için bkz: [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md).  
  
 Özel öznitelikler yalnızca hiçbir tür bağımsız değişkenleri sağlanan genel türler ve tüm tür parametreleri için bağımsız değişkenleri eklemek kapalı oluşturulan genel türleri, açık genel türler başvurmak için izin verilir.  
  
 Aşağıdaki örnekler, bu özel öznitelik kullanın:  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 Açık genel tür bir öznitelik başvurusu yapabilir:  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Uygun sayıda virgül kullanarak birden çok tür parametreleri belirtin. Bu örnekte, `GenericClass2` iki tür parametreye sahiptir:  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Bir öznitelik kapalı oluşturulan genel bir tür başvurabilir:  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Genel tür parametresi başvuruda bulunan bir öznitelik, bir derleme zamanı hatası neden olur:  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Genel bir tür devralınmalıdır olamaz <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Çalışma zamanında bir genel tür veya tür parametresi hakkında bilgi almak için yöntemleri kullanabilirsiniz <xref:System.Reflection>. Daha fazla bilgi için bkz: [genel türler ve yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
 [Öznitelikler](../../../../docs/standard/attributes/index.md)
