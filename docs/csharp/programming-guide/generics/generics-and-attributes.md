---
title: Genel türler ve öznitelikler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703032"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
Öznitelikler Genel türlere genel olmayan türlerle aynı şekilde uygulanabilir. Öznitelikleri uygulama hakkında daha fazla bilgi için bkz. [öznitelikler](../concepts/attributes/index.md).  
  
 Özel özniteliklerin yalnızca tür bağımsız değişkenleri sağlanmayan genel türler ve tüm tür parametreleri için bağımsız değişkenler sağlayan kapalı oluşturulmuş genel türler olan açık Genel türlere başvurmasına izin verilir.  
  
 Aşağıdaki örnekler bu özel özniteliği kullanır:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Bir öznitelik, açık bir genel türe başvurabilir:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Uygun sayıda virgül kullanarak birden çok tür parametresi belirtin. Bu örnekte `GenericClass2` iki tür parametreye sahiptir:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Bir öznitelik, Kapalı oluşturulmuş genel bir türe başvurabilir:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Genel tür parametresine başvuran bir öznitelik, derleme zamanı hatasına neden olur:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Genel bir tür <xref:System.Attribute>devralınabilir:  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Çalışma zamanında genel bir tür veya tür parametresi hakkında bilgi almak için <xref:System.Reflection>yöntemlerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Genel türler ve yansıma](./generics-and-reflection.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Öznitelikler](../../../standard/attributes/index.md)
