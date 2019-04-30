---
title: Genel türler ve öznitelikler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 000ce5a72cede9d1f23b0efb7ccf8638090a9032
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680369"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
Genel türler için öznitelikleri genel olmayan türleri aynı şekilde uygulanabilir. Öznitelikleri uygulama ile ilgili daha fazla bilgi için bkz: [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md).  
  
 Özel öznitelikler için hiçbir tür bağımsız değişkenleri sağlanan genel türler ve tüm tür parametreleri için bağımsız değişkenleri kapalı oluşturulan genel türler, açık genel türler başvurmak için yalnızca izin verilir.  
  
 Aşağıdaki örnekler, bu özel öznitelik kullanın:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Öznitelik, bir açık genel tür başvurabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Uygun sayıda virgül kullanarak birden çok tür parametreleri belirtin. Bu örnekte, `GenericClass2` iki tür parametreleri vardır:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Öznitelik, kapalı bir oluşturulmuş genel tür başvurabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Genel tür parametresine başvuran bir öznitelik, bir derleme zamanı hatasına neden olur:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Genel tür devralamaz <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Çalışma zamanında bir genel tür veya tür parametresi ile ilgili bilgi edinme yöntemlerini kullanabilirsiniz <xref:System.Reflection>. Daha fazla bilgi için [genel türler ve yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)
- [Öznitelikler](../../../../docs/standard/attributes/index.md)
