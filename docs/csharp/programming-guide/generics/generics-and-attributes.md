---
title: Genel türler ve öznitelikler-C# Programlama Kılavuzu
description: Genel türlere öznitelikler uygulama hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 94378e44782169141314890bf90f050fdb6b5b79
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184215"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)

Öznitelikler Genel türlere genel olmayan türlerle aynı şekilde uygulanabilir. Öznitelikleri uygulama hakkında daha fazla bilgi için bkz. [öznitelikler](../concepts/attributes/index.md).  
  
 Özel özniteliklerin yalnızca tür bağımsız değişkenleri sağlanmayan genel türler ve tüm tür parametreleri için bağımsız değişkenler sağlayan kapalı oluşturulmuş genel türler olan açık Genel türlere başvurmasına izin verilir.  
  
 Aşağıdaki örnekler bu özel özniteliği kullanır:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Bir öznitelik, açık bir genel türe başvurabilir:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Uygun sayıda virgül kullanarak birden çok tür parametresi belirtin. Bu örnekte, `GenericClass2` iki tür parametresi vardır:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Bir öznitelik, Kapalı oluşturulmuş genel bir türe başvurabilir:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Genel tür parametresine başvuran bir öznitelik, derleme zamanı hatasına neden olur:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Genel bir tür şuradan devralınabilir <xref:System.Attribute> :  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Çalışma zamanında genel bir tür veya tür parametresi hakkında bilgi edinmek için, yöntemlerini kullanabilirsiniz <xref:System.Reflection> . Daha fazla bilgi için bkz. [Genel türler ve yansıma](./generics-and-reflection.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Öznitelikler](../../../standard/attributes/index.md)
