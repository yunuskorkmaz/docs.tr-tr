---
title: Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3c4ff558f2b850e195138dcc8901d6d860365cfc
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/24/2018
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)
C# dil özel durum özellikleri Yardım işleme ile bir program çalışırken oluşan beklenmeyen veya olağanüstü durumlara ilgilenir. Özel durum işleme kullanan `try`, `catch`, ve `finally` başarılı olmayabilir Eylemler denemek için bunu yapmak için ve daha sonra kaynakları temizlemek için makul karar verirken hataları işlemek için anahtar sözcükler. Özel durumlar ortak dil çalışma zamanı tarafından (CLR), .NET Framework veya herhangi bir üçüncü taraf kitaplıklar veya uygulama kodu tarafından oluşturulabilir. Özel durumlar kullanarak oluşturulur `throw` anahtar sözcüğü.  
  
 Çoğu durumda, bir özel durum kodunuzu doğrudan çağrılan olmayan bir yöntemi tarafından oluşturulan, ancak başka bir yöntem kullanarak aşağı çağrı yığınında daha fazla. Bu gerçekleştiğinde, CLR yığını bir yöntemle arayan bırakma bir `catch` belirli özel durum türünü ve bu ilk yürütecek için engelleme gibi `catch` olması durumunda engelleme bulur. Hayır uygun bulursa `catch` herhangi bir yere çağrı yığınında engellemek, işlemi sonlandırmamız ve kullanıcıya bir ileti görüntüler.  
  
 Bu örnekte, bir yöntem sıfıra bölme için test ve hata yakalar. Özel durum işleme olmadan bu programı ile sonlandırmak bir **DivideByZeroException işlenmemiş** hata.  
  
 [!code-csharp[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>Özel durumlar genel bakış  
 Özel durumlar aşağıdaki özelliklere sahiptir:  
  
-   Özel durumları olan tüm sonuçta öğesinden türetilen türler `System.Exception`.  
  
-   Kullanım bir `try` özel durumlar oluşturma deyimleri geçici bloğu.  
  
-   Bir özel durum oluşması sonra `try` engellemek, akışını herhangi bir yere çağrı yığınında mevcut ilk ilişkili özel durum işleyici denetimi atlar. C# ' ta, `catch` anahtar sözcüğü bir özel durum işleyici tanımlamak için kullanılır.  
  
-   Belirli bir özel durum için hiçbir özel durum işleyicisi varsa, bir hata iletisi ile yürütme programı durdurur.  
  
-   Bunu işlemek ve uygulama bilinen bir durumda bırakır sürece bir özel durum catch değil. Catch `System.Exception`, kullanarak yeniden oluşturulması `throw` anahtar sözcüğü sonunda `catch` bloğu.  
  
-   Varsa bir `catch` blok tanımlayan bir özel durum değişkeni, oluşan özel durum türü hakkında daha fazla bilgi edinmek için kullanın.  
  
-   Özel durumlar açıkça oluşturulabilir bir program tarafından kullanarak `throw` anahtar sözcüğü.  
  
-   Özel durum nesneleri çağrı yığını ve metin açıklamasını hata durumu gibi hatayla ilgili ayrıntılı bilgiler içerir.  
  
-   Kod bir `finally` blok, bir özel durum olsa bile yürütüldüğünde. Kullanım bir `finally` herhangi bir akış veya açılmış dosyaları kapatmak örneğin kaynakları serbest bırakmak için blok `try` bloğu.  
  
-   .NET Framework yönetilen özel durumlar mekanizması yapılandırılmış Win32 özel durum işleme üzerinde uygulanır. Daha fazla bilgi için bkz: [yapılandırılmış özel durum işleme (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) ve [bir kilitlenme indirmelere derinliklerine, Win32 yapılandırılmış özel durum işleme üzerinde](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Özel durumlar ve özel durum işleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Özel Durumları Kullanma](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Özel Durumlar Oluşturma ve Atma](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Derleyicinin Ürettiği Özel Durumlar](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Nasıl yapılır: bir özel durum try/catch kullanarak (C# programlama Kılavuzu) işleme](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [Nasıl yapılır: Finally Kullanarak Temizleme Kodu Yürütme](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.SystemException>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [Özel Durumlar](../../../standard/exceptions/index.md)  
