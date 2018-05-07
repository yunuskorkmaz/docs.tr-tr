---
title: 'Nasıl yapılır: bir özel durum kullanılarak try-catch (C# programlama Kılavuzu) işleme'
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: b67a3d7b6d2e10519363a273b7dd1d8b61317d1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Nasıl yapılır: try/catch Kullanarak Özel Durum İşleme (C# Programlama Kılavuzu)
Amacı bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) taşıdır yakalamak ve çalışma kod tarafından oluşturulan özel bir durumu işlemek için. Bazı özel durumlar işlenebilir bir `catch` bloğu ve sorun çözüldüğünde yeniden atılmış olan özel durum; ancak, daha sık yapabileceğiniz tek şey uygun özel durum atılır emin olun.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.IndexOutOfRangeException> en uygun özel durum değil: <xref:System.ArgumentOutOfRangeException> tarafından hataya neden olduğundan daha fazla yöntemi için mantıklı `index` bağımsız değişkeni geçirilen çağıran tarafından.  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Bir özel duruma neden olan kod sınırlanan `try` bloğu. A `catch` deyimi eklenir hemen sonra işlemek üzere `IndexOutOfRangeException`, meydana gelmesi durumunda. `catch` Engelleme tanıtıcıları `IndexOutOfRangeException` ve daha uygun oluşturur `ArgumentOutOfRangeException` özel durum yerine. Arayan mümkün olduğunca fazla bilgi sağlamak için özgün özel durum olarak belirtmeyi göz önünde bulundurun <xref:System.Exception.InnerException%2A> yeni özel durum. Çünkü <xref:System.Exception.InnerException%2A> özelliği [readonly](../../../csharp/language-reference/keywords/readonly.md), yeni özel durum oluşturucuda atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)  
 [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)
