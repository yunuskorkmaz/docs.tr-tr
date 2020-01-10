---
title: Try-Catch- C# Programming kılavuzunu kullanarak özel durum işleme
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: adfc53cbe4fd603ac3a6de6b9a0162320d5a2e19
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712292"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Try/catch kullanarak özel durum işleme (C# Programlama Kılavuzu)
[Try-catch](../../language-reference/keywords/try-catch.md) bloğunun amacı, çalışma kodu tarafından oluşturulan bir özel durumu yakalamak ve işleymelidir. Bazı özel durumlar bir `catch` bloğunda işlenebilir ve sorun yeniden oluşturulan özel durum olmadan çözüldü; Ancak, çoğu zaman yapabileceğiniz tek şey, uygun özel durumun oluşturulmuş olduğundan emin olmanızı sağlamak.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.IndexOutOfRangeException> en uygun özel durum değildir: <xref:System.ArgumentOutOfRangeException>, hata, çağıran tarafından geçirilen `index` bağımsız değişkeninin nedeni nedeniyle Yöntem için daha anlamlı hale gelir.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Açıklamalar  
 Özel duruma neden olan kod `try` bloğuna alınmıştır. `catch` bir ifade, gerçekleşirse, `IndexOutOfRangeException`işleme hemen sonra eklenir. `catch` bloğu `IndexOutOfRangeException` işler ve bunun yerine daha uygun `ArgumentOutOfRangeException` özel durumunu oluşturur. Çağıranın mümkün olduğunca fazla bilgi sağlaması için, özgün özel durumu yeni özel durumun <xref:System.Exception.InnerException%2A> olarak belirtmeyi göz önünde bulundurun. <xref:System.Exception.InnerException%2A> özelliği [ReadOnly](../../language-reference/keywords/readonly.md)olduğundan, bunu yeni özel durumun oluşturucusunda atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [Özel Durum İşleme](./exception-handling.md)
