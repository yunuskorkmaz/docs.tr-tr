---
title: Jenerik ler ve Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703019"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genel Türler ve Diziler (C# Programlama Kılavuzu)
C# 2.0 ve sonraki durumlarda, sıfır ın alt sınırı olan <xref:System.Collections.Generic.IList%601>tek boyutlu diziler otomatik olarak uygulanır. Bu, diziler ve diğer koleksiyon türleri arasında aynı kodu yinelemek için kullanabileceğiniz genel yöntemler oluşturmanıza olanak tanır. Bu teknik öncelikle koleksiyonlarda veri okumak için yararlıdır. Arabirim, <xref:System.Collections.Generic.IList%601> bir diziden öğe eklemek veya kaldırmak için kullanılamaz. Bu bağlamda bir dizi gibi <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bir yöntem çağırmaya çalışırsanız bir özel durum atılır.  
  
 Aşağıdaki kod örneği, giriş parametresi alan <xref:System.Collections.Generic.IList%601> tek bir genel yöntemin, bu durumda bir tamsayı dizisi olan bir liste ve dizi aracılığıyla nasıl yinelebildiğini gösterir.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Diziler](../arrays/index.md)
- [Genel Türler](../../../standard/generics/index.md)
