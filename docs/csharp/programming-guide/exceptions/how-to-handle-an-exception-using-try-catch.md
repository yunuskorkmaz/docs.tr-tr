---
title: "Nasıl yapılır: bir özel durum kullanılarak try-catch (C# programlama Kılavuzu) işleme"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9098bbcf5cefb85211f9d3bb9cac15943ba02172
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Nasıl yapılır: try/catch Kullanarak Özel Durum İşleme (C# Programlama Kılavuzu)
Amacı bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) taşıdır yakalamak ve çalışma kod tarafından oluşturulan özel bir durumu işlemek için. Bazı özel durumlar işlenebilir bir `catch` bloğu ve sorun çözüldüğünde yeniden atılmış olan özel durum; ancak, daha sık yapabileceğiniz tek şey uygun özel durum atılır emin olun.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.IndexOutOfRangeException> en uygun özel durum değil: <xref:System.ArgumentOutOfRangeException> tarafından hataya neden olduğundan daha fazla yöntemi için mantıklı `index` bağımsız değişkeni geçirilen çağıran tarafından.  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Bir özel duruma neden olan kod sınırlanan `try` bloğu. A `catch` deyimi eklenir hemen sonra işlemek üzere `IndexOutOfRangeException`, meydana gelmesi durumunda. `catch` Engelleme tanıtıcıları `IndexOutOfRangeException` ve daha uygun oluşturur `ArgumentOutOfRangeException` özel durum yerine. Arayan mümkün olduğunca fazla bilgi sağlamak için özgün özel durum olarak belirtmeyi göz önünde bulundurun <xref:System.Exception.InnerException%2A> yeni özel durum. Çünkü <xref:System.Exception.InnerException%2A> özelliği [readonly](../../../csharp/language-reference/keywords/readonly.md), yeni özel durum oluşturucuda atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md)  
 [Özel durum işleme](../../../csharp/programming-guide/exceptions/exception-handling.md)
