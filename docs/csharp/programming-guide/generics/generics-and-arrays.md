---
title: Genel türler ve diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 145203d259b943bea1f43a9e49db2c7889bf914a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680148"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genel Türler ve Diziler (C# Programlama Kılavuzu)
C# 2.0 ve sonraki sürümlerinde, otomatik olarak bir alt sınırı sıfır olan tek boyutlu diziler uygulamak <xref:System.Collections.Generic.IList%601>. Bu, aynı kodu, diziler ve diğer koleksiyon türlerine yineleme yapmak için kullanabileceğiniz genel yöntemler oluşturmanıza olanak sağlar. Bu teknik koleksiyonlarda verileri okumak için özellikle yararlıdır. <xref:System.Collections.Generic.IList%601> Arabirimi eklemek veya bir diziden öğeleri kaldırmak için kullanılamaz. Çağrılacak denerseniz bir özel durum bir <xref:System.Collections.Generic.IList%601> yöntemi gibi <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bu bağlamda bir dizi.  
  
 Aşağıdaki kod örneği, alan tek bir genel yöntem nasıl gösterir bir <xref:System.Collections.Generic.IList%601> giriş parametresi bir listesi ve bir dizi yinelenir bu tamsayı dizisi durumda.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)
- [Diziler](../../../csharp/programming-guide/arrays/index.md)
- [Genel Türler](~/docs/standard/generics/index.md)
