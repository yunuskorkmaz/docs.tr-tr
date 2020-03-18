---
title: Özel Durumlar ve Özel Durum Taşıma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: b883012cf8f72247ff4e0b47a46eee1854e2d534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76735652"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)

C# dilinin özel durum işleme özellikleri, bir program çalışırken meydana gelen beklenmeyen veya istisnai durumlarla başa çıkmanıza yardımcı olur. Özel durum `try`işleme, başarılı olamayan eylemleri denemek, bunu yapmak için makul olduğuna karar verdiyseniz hataları işlemek ve daha sonra kaynakları temizlemek için , ve `catch` `finally` anahtar kelimeler kullanır. Özel durumlar, ortak dil çalışma süresi (CLR), .NET Framework veya herhangi bir üçüncü taraf kitaplıkları veya uygulama kodu tarafından oluşturulabilir. Özel durumlar anahtar sözcük `throw` kullanılarak oluşturulur.

Çoğu durumda, bir özel durum, kodunuzu doğrudan çağırdığı bir yöntem tarafından değil, arama yığınının daha aşağısındabaşka bir yöntem tarafından atılabilir. Bu durumda, CLR belirli özel durum türü için bir `catch` blok ile bir yöntem arayarak yığını `catch` gevşetmek ve bulursa ilk tür blok yürütecek. Arama yığınının `catch` herhangi bir yerinde uygun bir engel bulamazsa, işlemi sonlandırır ve kullanıcıya bir ileti görüntüler.

Bu örnekte, bir yöntem sıfıra bölme için test ve hata yakalar. Özel durum işleme olmadan, bu program **bir DivideByZeroException ile sonlandırılmaz işlenmemiş** hata oldu.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Özel Durumlara Genel Bakış

Özel durumlar aşağıdaki özelliklere sahiptir:

- Özel durumlar, sonuçta tüm türlerden `System.Exception`türetilmiştir.
- Özel `try` durumlar atabilecek deyimlerin etrafında bir blok kullanın.
- `try` Blokta bir özel durum oluştuğunda, denetim akışı çağrı yığınının herhangi bir yerinde bulunan ilk ilişkili özel durum işleyicisine atlar. `catch` C#'da, anahtar kelime bir özel durum işleyicisi tanımlamak için kullanılır.
- Belirli bir özel durum için özel durum işleyicisi yoksa, program bir hata iletisi ile yürütmeyi durdurur.
- İşleyebilir ve uygulamayı bilinen bir durumda bırakmadığınız sürece bir özel durum yakalamayın. Yakalarsanız, `System.Exception` `catch` bloğun sonundaki anahtar `throw` kelimeyi kullanarak yeniden atayın.
- Bir `catch` blok bir özel durum değişkeni tanımlıyorsa, oluşan özel durum türü hakkında daha fazla bilgi edinmek için kullanabilirsiniz.
- Özel `throw` durumlar, anahtar kelime kullanılarak bir program tarafından açıkça oluşturulabilir.
- Özel durum nesneleri, arama yığınının durumu ve hatanın metin açıklaması gibi hata hakkında ayrıntılı bilgiler içerir.
- Bir özel `finally` durum atılsa bile bloktaki kod yürütülür. Örneğin, `finally` `try` blokta açılan akışları veya dosyaları kapatmak için kaynakları serbest bırakmak için bir blok kullanın.
- .NET Framework'de yönetilen özel durumlar Win32 yapılandırılmış özel durum işleme mekanizmasının üstüne uygulanır. Daha fazla bilgi için [Win32 Yapılandırılmış Özel Durum İşleme'nin Derinliklerinde](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm) [Yapılandırılmış Özel Durum İşleme (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) ve Bir Kilitlenme Kursu'na bakın.

## <a name="related-sections"></a>İlgili Bölümler

Özel durumlar ve özel durum işleme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Özel Durumları Kullanma](using-exceptions.md)
- [Özel Durum Taşıma](exception-handling.md)
- [Özel Durumlar Oluşturma ve Atma](creating-and-throwing-exceptions.md)
- [Derleyicinin Ürettiği Özel Durumlar](compiler-generated-exceptions.md)
- [Try/catch (C# Programlama Kılavuzu) kullanarak bir özel durum nasıl işleyebilir](how-to-handle-an-exception-using-try-catch.md)
- [Finally anahtar sözcüğünü kullanarak temizleme kodu yürütme](how-to-execute-cleanup-code-using-finally.md)
- [CLS dışı özel durumu yakalama](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Özel Durumlar'a](~/_csharplang/spec/exceptions.md) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- [C# Programlama Kılavuzu](../index.md)
- [C# Anahtar Kelimeler](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Özel durumlar](../../../standard/exceptions/index.md)
