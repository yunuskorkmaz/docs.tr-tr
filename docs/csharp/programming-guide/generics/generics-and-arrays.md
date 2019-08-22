---
title: Genel türler ve diziler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: fee66cf7bd0ab3c051ea67acc323efa02a21a017
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659799"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genel Türler ve Diziler (C# Programlama Kılavuzu)
2,0 C# ve üzeri sürümlerde, sıfır alt sınırı olan tek boyutlu diziler otomatik olarak uygulanır <xref:System.Collections.Generic.IList%601>. Bu, diziler ve diğer koleksiyon türleri arasında yinelemek için aynı kodu kullanan genel yöntemler oluşturmanızı sağlar. Bu teknik öncelikle koleksiyonlardaki verileri okumak için yararlıdır. <xref:System.Collections.Generic.IList%601> Arabirim bir diziye öğe eklemek veya kaldırmak için kullanılamaz. Bu bağlamdaki bir dizide gibi <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bir yöntemi çağırmaya çalışırsanız bir özel durum oluşturulur.  
  
 Aşağıdaki kod örneği, bir <xref:System.Collections.Generic.IList%601> giriş parametresi alan tek bir genel yöntemin, bu durumda bir tamsayılar dizisi olan bir liste ve dizi boyunca nasıl yineleyebileceğinizi göstermektedir.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Diziler](../arrays/index.md)
- [Genel Türler](../../../standard/generics/index.md)
