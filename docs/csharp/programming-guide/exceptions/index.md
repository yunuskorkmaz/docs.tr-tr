---
title: Özel durumlar ve özel durum işleme - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: dfbdcf29e0fc003f9478e6f691957b67574d5233
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680669"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)
C# dil özel durum özelliklerin help işleme ile bir program çalışırken oluşan beklenmeyen veya olağanüstü durumlara ilgilenir. Özel durum işleme kullanan `try`, `catch`, ve `finally` başarılı olmayabilir eylemleri denemek için bunu yapmak için ve daha sonra kaynakları temizlemek için makul karar verdiğinizde, hataları işlemek için anahtar sözcükler. Özel durumlar, .NET Framework veya herhangi bir üçüncü taraf kitaplıklar tarafından veya uygulama kodu tarafından ortak dil çalışma zamanı tarafından (CLR) oluşturulabilir. Özel durumlar kullanılarak oluşturulan `throw` anahtar sözcüğü.  
  
 Çoğu durumda, bir özel durum kodunuzu doğrudan çağıran olmayan bir yöntemi tarafından oluşturulan, ancak başka bir yöntemle aşağı çağrı yığınında daha fazla. Bu durumda, CLR yığını bir yöntemle aranıyor geriye doğru izleme bir `catch` belirli özel durum türü ve ilk yürütecek için engelleme gibi `catch` olması durumunda block bulur. En uygun bulursa `catch` herhangi bir çağrı yığınında engelleme, işlemi sonlandırmak ve kullanıcıya bir ileti görüntüler.  
  
 Bu örnekte, bir yöntem sıfıra bölme için test ve hata yakalar. Özel durum işleme olmadan, bu program ile sonlanırdı bir **DivideByZeroException işlenmemiş** hata.  
  
 [!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]  
  
## <a name="exceptions-overview"></a>Özel durumlar genel bakış  
 Özel durumlar aşağıdaki özelliklere sahiptir:  
  
- Özel durumları olan tüm sonuçta öğesinden türetilen türler `System.Exception`.  
  
- Kullanım bir `try` geçici özel durumlar deyimleri blok.  
  
- Özel durum oluşması sonra `try` herhangi bir çağrı yığınında mevcut olan ilk ilişkili bir özel durum işleyici denetimi atlar akışını engelleyin. C# ' ta, `catch` anahtar sözcüğü, bir özel durum işleyicisi tanımlamak için kullanılır.  
  
- Belirli bir özel durum için hiçbir özel durum işleyicisi varsa, yürütülürken bir hata iletisiyle programı durdurur.  
  
- Bunu işlemek ve uygulamanın bilinen bir durumda bırakır sürece bir özel durum yakalamayın. Yakalarsanız, `System.Exception`, kullanarak rethrow `throw` sonunda, anahtar sözcüğü `catch` blok.  
  
- Varsa bir `catch` blok bir özel durum değişken tanımlar, oluşan özel durumun türünü hakkında daha fazla bilgi edinmek için kullanabilirsiniz.  
  
- Özel durumlar açıkça oluşturulabilir bir program tarafından kullanarak `throw` anahtar sözcüğü.  
  
- Özel durum nesneleri, çağrı yığını ve metin açıklamasını hata durumu gibi hata hakkında ayrıntılı bilgi içerir.  
  
- Kod bir `finally` blokesi bile bir özel durum oluşturulur. Kullanım bir `finally` herhangi bir akış veya açılmış dosyaları kapatın. Örneğin, kaynakları serbest bırakmak için blok `try` blok.  
  
- Yönetilen özel durumlar .NET Framework'teki Win32 yapılandırılmış özel durum işleme mekanizmasını üzerine uygulanır. Daha fazla bilgi için [yapılandırılmış özel durum işleme (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) ve [derinliği, Win32 yapılandırılmış özel durum işleme ile ilgili bir kilitlenme dersi](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Özel durumlar ve özel durum işleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Özel Durumları Kullanma](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
- [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
- [Özel Durumlar Oluşturma ve Atma](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
- [Derleyicinin Ürettiği Özel Durumlar](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
- [Nasıl yapılır: Bir özel durum try/catch kullanarak işleme (C# Programlama Kılavuzu)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
- [Nasıl yapılır: Finally anahtar sözcüğünü kullanarak temizleme kodu yürütme](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [özel durumları](~/_csharplang/spec/exceptions.md) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [throw](../../../csharp/language-reference/keywords/throw.md)
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
- [Özel Durumlar](../../../standard/exceptions/index.md)
