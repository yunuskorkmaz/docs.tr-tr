---
title: 'Nasıl yapılır: Finally Anahtar Sözcüğünü Kullanarak Temizleme Kodu Yürütme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 948281af45d04714ed6fc308b60341e87abeb830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331714"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Nasıl yapılır: Finally Anahtar Sözcüğünü Kullanarak Temizleme Kodu Yürütme (C# Programlama Kılavuzu)
Amacı bir `finally` açıklamadır bir özel durum olsa bile nesneleri, dış kaynaklara bulunduran genellikle gerekli temizlenmesi hemen gerçekleşmesini sağlamak için. Bu tür temizleme bir örneği çağırma <xref:System.IO.Stream.Close%2A> üzerinde bir <xref:System.IO.FileStream> nesnesi gibi ortak dil çalışma zamanı tarafından toplanacak beklemek yerine hemen kullandıktan sonra:  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a>Örnek  
 Önceki koda açmak için bir `try-catch-finally` deyimi, kodu temizleme ayrılmış çalışma koddan gibi.  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Özel bir durum içinde herhangi bir zamanda olabileceği için `try` önce engelle `OpenWrite()` çağrısı, veya `OpenWrite()` çağrı kendisini başarısız, biz kapatmak denediğinizde dosyanın açık olduğunu garanti edilmez. `finally` Bloğu ekler emin olmak için bir onay <xref:System.IO.FileStream> nesnesi değil `null` çağırmadan önce <xref:System.IO.Stream.Close%2A> yöntemi. Olmadan `null` denetleyin, `finally` blok throw kendi <xref:System.NullReferenceException>, ancak özel durumları atma `finally` mümkünse blokları kaçınılmalıdır.  
  
 Bir veritabanı bağlantısı başka bir iyi kapalı için adaydır bir `finally` bloğu. Bir veritabanı sunucusu için izin verilen bağlantı sayısının bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olan en kısa sürede kapatmanız gerekir. Bağlantınızı kapatmadan önce bir özel durum, bu başka bir örneği ise kullanarak burada `finally` blok atık toplama için bekleyen daha iyi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)  
 [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [using Deyimi](../../../csharp/language-reference/keywords/using-statement.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
