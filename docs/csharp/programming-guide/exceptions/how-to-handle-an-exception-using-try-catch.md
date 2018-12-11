---
title: 'Nasıl Yapılır: Bir özel durum kullanarak try-catch - işleme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: db83eca52b204df1bb8273e94ae8664e61175aa7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244946"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Nasıl Yapılır: Bir özel durum try/catch kullanarak işleme (C# Programlama Kılavuzu)
Amacı, bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) bloğudur yakalayın ve çalışan kod tarafından oluşturulan bir özel durumu işle. Bazı özel durumlar olarak işlenebilen bir `catch` bloğu ve sorun çözüldüğünde yeniden oluşturulmuş olan özel durum; ancak, daha sık yapmak için gereken tek şey uygun özel durum emin emin olun.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.IndexOutOfRangeException> en uygun özel durum değil: <xref:System.ArgumentOutOfRangeException> tarafından hata oluştuğundan, yöntem için daha anlamlı olur `index` bağımsız değişken geçirildi çağıran tarafından.  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Bir özel durum neden olan kod içine `try` blok. A `catch` deyimi eklenir hemen sonra işlemeye `IndexOutOfRangeException`, meydana gelmesi durumunda. `catch` Block tanıtıcıları `IndexOutOfRangeException` ve daha uygun `ArgumentOutOfRangeException` özel durumu yerine. Çağıranın yazılımında mümkün olduğunca fazla bilgi için özgün özel durum olarak belirtmeyi düşünün <xref:System.Exception.InnerException%2A> yeni özel durum. Çünkü <xref:System.Exception.InnerException%2A> özelliği [salt okunur](../../../csharp/language-reference/keywords/readonly.md), yeni özel durumun oluşturucuda atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)  
- [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)
