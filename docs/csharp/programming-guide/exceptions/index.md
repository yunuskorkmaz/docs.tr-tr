---
title: Özel durumlar ve özel durum C# işleme-Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 1442daf646a29c3822d06d0b649f462b37523fe2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002118"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel durumlar ve özel durumC# işleme (Programlama Kılavuzu)

C# Dilin özel durum işleme özellikleri, bir program çalışırken oluşan beklenmedik veya olağanüstü durumlarla ilgilenmenize yardımcı olur. Özel durum işleme, başarılı olmayan eylemleri denemek için `try`, `catch` ve `finally` anahtar sözcüklerini kullanır, bunu yapmak için makul olduğuna karar verirken sorunları idare edin ve daha sonra kaynakları temizleyebiliriz. Özel durumlar ortak dil çalışma zamanı (CLR) tarafından, .NET Framework veya herhangi bir üçüncü taraf kitaplığı tarafından ya da uygulama kodu tarafından oluşturulabilir. Özel durumlar `throw` anahtar sözcüğü kullanılarak oluşturulur.

Çoğu durumda, kodunuzun doğrudan çağırdığı bir yöntem tarafından değil, çağrı yığınında daha sonra başka bir yöntem tarafından bir özel durum atılır. Bu durumda, CLR, belirli bir özel durum türü için `catch` bloğuna sahip bir yöntemi arayarak yığını yeniden yürütür ve bulduğu ilk `catch` bloğunu yürütür. Çağrı yığınında herhangi bir yerde uygun `catch` bloğu bulursa, işlemi sonlandırır ve kullanıcıya bir ileti görüntüler.

Bu örnekte, bir yöntem sıfıra bölme için test eder ve hatayı yakalar. Özel durum işleme olmadan, bu program bir **Dividebysıfırlaması özel durumu** ile sonlandırılır ve işlenmemiş bir hatadır.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Özel durumlara genel bakış

Özel durumlar aşağıdaki özelliklere sahiptir:  

- Özel durumlar, sonuçta `System.Exception` ' dan türetilen türlerdir.
- Özel durum oluşturabilecek deyimler etrafında `try` bloğu kullanın.
- @No__t-0 bloğunda bir özel durum oluştuktan sonra Denetim akışı, çağrı yığınında herhangi bir yerde bulunan ilk ilişkili özel durum işleyicisine atlar. ' C#De, bir özel durum işleyicisini tanımlamak için `catch` anahtar sözcüğü kullanılır.
- Belirli bir özel durum için özel durum işleyicisi yoksa, program yürütmeyi bir hata iletisiyle sonlandırır.
- İşleyebilmediğiniz ve uygulamayı bilinen bir durumda bırakarak bir özel durumu yakalamayın. @No__t-0 ' ı yakalarsanız, `catch` bloğunun sonundaki `throw` anahtar sözcüğünü kullanarak yeniden oluşturun.
- Bir `catch` bloğu bir özel durum değişkeni tanımlıyorsa, oluşan özel durum türü hakkında daha fazla bilgi edinmek için onu kullanabilirsiniz.
- Özel durumlar, `throw` anahtar sözcüğü kullanılarak açıkça bir program tarafından oluşturulabilir.
- Özel durum nesneleri, hata hakkında, çağrı yığınının durumu ve hatanın metin açıklaması gibi ayrıntılı bilgiler içerir.
- Bir özel durum oluşsa bile `finally` bloğundaki kod yürütülür. Kaynakları serbest bırakmak için `finally` bloğu kullanın, örneğin, `try` bloğunda açılan tüm akışları veya dosyaları kapatın.
- .NET Framework yönetilen özel durumlar, Win32 yapılandırılmış özel durum işleme mekanizmasının üzerine uygulanır. Daha fazla bilgi için, bkz. [yapılandırılmış özel durum işlemeC++(C/)](/cpp/cpp/structured-exception-handling-c-cpp) ve [Win32 yapılandırılmış özel durum işleme derinlikleri üzerinde çökme kursu](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>İlgili bölümler

Özel durumlar ve özel durum işleme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Özel durumları kullanma](using-exceptions.md)
- [Özel durum Işleme](exception-handling.md)
- [Özel durumlar oluşturma ve atma](creating-and-throwing-exceptions.md)
- [Derleyicinin ürettiği özel durumlar](compiler-generated-exceptions.md)
- [Nasıl yapılır: try/catch kullanarak özel durum Işleme (C# Programlama Kılavuzu)](how-to-handle-an-exception-using-try-catch.md)
- [Nasıl yapılır: son kullanarak temizlik kodu yürütme](how-to-execute-cleanup-code-using-finally.md)
- [Nasıl yapılır: CLS olmayan özel durum yakalama](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>C#Dil belirtimi

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [özel durumlar](~/_csharplang/spec/exceptions.md) . Dil belirtimi, sözdizimi ve kullanım için C# tanımlayıcı kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- [C#Programlama Kılavuzu](../index.md)
- [C#Lerimi](../../language-reference/keywords/index.md)
- [yaratır](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Özel Durumlar](../../../standard/exceptions/index.md)
