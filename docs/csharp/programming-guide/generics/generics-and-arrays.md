---
title: Genel türler ve diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 50d649c4662114e76fdc0a6161ab0cbbeb04756d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237460"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genel Türler ve Diziler (C# Programlama Kılavuzu)
C# 2.0 ve sonraki sürümlerinde, otomatik olarak bir alt sınırı sıfır olan tek boyutlu diziler uygulamak <xref:System.Collections.Generic.IList%601>. Bu, aynı kodu, diziler ve diğer koleksiyon türlerine yineleme yapmak için kullanabileceğiniz genel yöntemler oluşturmanıza olanak sağlar. Bu teknik koleksiyonlarda verileri okumak için özellikle yararlıdır. <xref:System.Collections.Generic.IList%601> Arabirimi eklemek veya bir diziden öğeleri kaldırmak için kullanılamaz. Çağrılacak denerseniz bir özel durum bir <xref:System.Collections.Generic.IList%601> yöntemi gibi <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bu bağlamda bir dizi.  
  
 Aşağıdaki kod örneği, alan tek bir genel yöntem nasıl gösterir bir <xref:System.Collections.Generic.IList%601> giriş parametresi bir listesi ve bir dizi yinelenir bu tamsayı dizisi durumda.  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Collections.Generic>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
- [Diziler](../../../csharp/programming-guide/arrays/index.md)  
- [Genel Türler](~/docs/standard/generics/index.md)
