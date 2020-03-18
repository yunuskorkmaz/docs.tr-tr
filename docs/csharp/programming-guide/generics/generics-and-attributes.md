---
title: Genel ler ve Öznitelikler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703032"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
Öznitelikler genel olmayan türler gibi genel türlere uygulanabilir. Öznitelikleri uygulama hakkında daha fazla bilgi için, [Bkz. Öznitelikler.](../concepts/attributes/index.md)  
  
 Özel özniteliklere yalnızca, tür bağımsız değişkenleri verilen genel türler olan açık genel türlere ve tüm tür parametreleri için bağımsız değişkensağlayan kapalı yapılı genel türlere başvurmaizni verilir.  
  
 Aşağıdaki örneklerde bu özel özniteliği kullanın:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Bir öznitelik açık genel bir türbaşvuru olabilir:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Uygun sayıda virgül kullanarak birden çok tür parametresini belirtin. Bu örnekte, `GenericClass2` iki tür parametre vardır:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Bir öznitelik kapalı oluşturulmuş genel türe başvurulabilir:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Genel bir tür parametresine başvuran bir öznitelik derleme zamanı hatasına neden olur:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Genel bir tür <xref:System.Attribute>devralamaz:  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Genel bir tür veya çalışma zamanında tür parametresi hakkında bilgi <xref:System.Reflection>edinmek için . Daha fazla bilgi için [Genel Bilgiler ve Yansıma](./generics-and-reflection.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Öznitelikler](../../../standard/attributes/index.md)
