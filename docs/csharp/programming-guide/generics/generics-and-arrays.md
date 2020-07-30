---
title: Genel türler ve diziler-C# Programlama Kılavuzu
description: C# programlamada genel türler ve Diziler hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f3d9e9e0c84d954278780e7598545f80aea0e58c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299051"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genel Türler ve Diziler (C# Programlama Kılavuzu)
C# 2,0 ve üzeri sürümlerde, sıfır alt sınırı olan tek boyutlu diziler otomatik olarak uygulanır <xref:System.Collections.Generic.IList%601> . Bu, diziler ve diğer koleksiyon türleri arasında yinelemek için aynı kodu kullanan genel yöntemler oluşturmanızı sağlar. Bu teknik öncelikle koleksiyonlardaki verileri okumak için yararlıdır. <xref:System.Collections.Generic.IList%601>Arabirim bir diziye öğe eklemek veya kaldırmak için kullanılamaz. <xref:System.Collections.Generic.IList%601>Bu bağlamdaki bir dizide gibi bir yöntemi çağırmaya çalışırsanız bir özel durum oluşturulur <xref:System.Collections.Generic.IList%601.RemoveAt%2A> .  
  
 Aşağıdaki kod örneği, bir giriş parametresi alan tek bir genel yöntemin <xref:System.Collections.Generic.IList%601> , bu durumda bir tamsayılar dizisi olan bir liste ve dizi boyunca nasıl yineleyebileceğinizi göstermektedir.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Diziler](../arrays/index.md)
- [Genel Türler](../../../standard/generics/index.md)
