---
title: Genel türler ve diziler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703019"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genel Türler ve Diziler (C# Programlama Kılavuzu)
C# 2,0 ve üzeri sürümlerde, sıfır alt sınırı olan tek boyutlu diziler otomatik olarak <xref:System.Collections.Generic.IList%601>uygular. Bu, diziler ve diğer koleksiyon türleri arasında yinelemek için aynı kodu kullanan genel yöntemler oluşturmanızı sağlar. Bu teknik öncelikle koleksiyonlardaki verileri okumak için yararlıdır. <xref:System.Collections.Generic.IList%601> arabirimi bir diziye öğe eklemek veya kaldırmak için kullanılamaz. Bu bağlamdaki bir dizide <xref:System.Collections.Generic.IList%601.RemoveAt%2A> gibi bir <xref:System.Collections.Generic.IList%601> yöntemi çağırmayı denerseniz bir özel durum oluşturulur.  
  
 Aşağıdaki kod örneği, bir <xref:System.Collections.Generic.IList%601> giriş parametresi alan tek bir genel yöntemin, bu durumda bir tamsayılar dizisi olan bir liste ve dizi boyunca nasıl yineleyebileceğinizi göstermektedir.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Diziler](../arrays/index.md)
- [Genel Türler](../../../standard/generics/index.md)
