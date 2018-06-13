---
title: Genel Türler ve Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 2e7ab9ff0dc4a73500c1a452df16af17c720d528
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320670"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genel Türler ve Diziler (C# Programlama Kılavuzu)
C# 2.0 ve daha sonra otomatik olarak sıfır alt sınır olan tek boyutlu diziler uygulamak <xref:System.Collections.Generic.IList%601>. Bu, aynı kod diziler ve diğer koleksiyon türleri yinelemek için kullanabileceğiniz genel yöntemler oluşturmanıza olanak sağlar. Koleksiyonlarda verileri okumak için öncelikle bu teknik yararlıdır. <xref:System.Collections.Generic.IList%601> Arabirimi eklemek veya dizisinden öğeleri kaldırmak için kullanılamaz. Çağrı çalışırsanız, bir özel durum bir <xref:System.Collections.Generic.IList%601> yöntemi gibi <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bu bağlamda bir dizi.  
  
 Aşağıdaki kod örneğinde alan tek bir genel yöntem nasıl gösterilmektedir bir <xref:System.Collections.Generic.IList%601> giriş parametresi bir listesi ve bir dizi yineleyebilirsiniz bu dizisi durumda.  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Genel Türler](~/docs/standard/generics/index.md)
