---
title: Try-catch kullanarak bir özel durum nasıl işleyebilir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: adfc53cbe4fd603ac3a6de6b9a0162320d5a2e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712292"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Try/catch (C# Programlama Kılavuzu) kullanarak bir özel durum nasıl işleyebilir
[Try-catch](../../language-reference/keywords/try-catch.md) bloğunun amacı, çalışma kodu tarafından oluşturulan bir özel durumu yakalamak ve işlemektir. Bazı özel durumlar bir `catch` blokta işlenebilir ve sorun, istisna sız yeniden atılmadan çözülebilir; ancak, daha sık yapabileceğiniz tek şey uygun özel durum atılır emin olmaktır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.IndexOutOfRangeException> en uygun özel <xref:System.ArgumentOutOfRangeException> durum değildir: hata arayan tarafından geçirilen `index` bağımsız değişken neden olduğu için yöntem için daha mantıklı.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Yorumlar  
 Özel durum neden olan kod `try` bloka eklenir. Bir `catch` deyim, oluşursa `IndexOutOfRangeException`işlemek için hemen sonra eklenir. Blok `catch` işler `IndexOutOfRangeException` ve bunun yerine daha `ArgumentOutOfRangeException` uygun özel durum atar. Arayanın mümkün olduğunca çok bilgi sağlaması için, özgün özel durumu <xref:System.Exception.InnerException%2A> yeni özel durum olarak belirtmeyi düşünün. <xref:System.Exception.InnerException%2A> Özellik yalnızca [okunduğu](../../language-reference/keywords/readonly.md)için, yeni özel durum oluşturucuya atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum Kullanımı](./index.md)
- [Özel Durum Taşıma](./exception-handling.md)
