---
title: Özel durumlar ve özel durum C# işleme-Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 3506406a441cb2028c00d5b8ed87b57cc6dff38b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423261"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)

C# Dilin özel durum işleme özellikleri, bir program çalışırken oluşan beklenmedik veya olağanüstü durumlarla ilgilenmenize yardımcı olur. Özel durum işleme, başarılı olmayan eylemleri denemek için `try`, `catch` ve `finally` anahtar sözcüklerini kullanır, bunu yapmak için makul olduğuna karar verirken sorunları idare edin ve daha sonra kaynakları temizleyebiliriz. Özel durumlar ortak dil çalışma zamanı (CLR) tarafından, .NET Framework veya herhangi bir üçüncü taraf kitaplığı tarafından ya da uygulama kodu tarafından oluşturulabilir. Özel durumlar `throw` anahtar sözcüğü kullanılarak oluşturulur.

Çoğu durumda, kodunuzun doğrudan çağırdığı bir yöntem tarafından değil, çağrı yığınında daha sonra başka bir yöntem tarafından bir özel durum atılır. Bu durumda, CLR, belirli bir özel durum türü için `catch` bloğuna sahip bir yöntemi arayarak yığını yeniden yürütür ve bulduğu ilk `catch` bloğunu yürütür. Çağrı yığınında herhangi bir yerde uygun `catch` bloğu bulursa, işlemi sonlandırır ve kullanıcıya bir ileti görüntüler.

Bu örnekte, bir yöntem sıfıra bölme için test eder ve hatayı yakalar. Özel durum işleme olmadan, bu program bir **Dividebysıfırlaması özel durumu** ile sonlandırılır ve işlenmemiş bir hatadır.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Özel durumlara genel bakış

Özel durumlar aşağıdaki özelliklere sahiptir:  

- Özel durumlar, sonuçta `System.Exception` ' dan türetilen türlerdir.
- Özel durum oluşturabilecek deyimler etrafında `try` bloğu kullanın.
- `try` bloğunda bir özel durum oluştuktan sonra Denetim akışı, çağrı yığınında herhangi bir yerde bulunan ilk ilişkili özel durum işleyicisine atlar. ' C#De, bir özel durum işleyicisini tanımlamak için `catch` anahtar sözcüğü kullanılır.
- Belirli bir özel durum için özel durum işleyicisi yoksa, program yürütmeyi bir hata iletisiyle sonlandırır.
- İşleyebilmediğiniz ve uygulamayı bilinen bir durumda bırakarak bir özel durumu yakalamayın. `System.Exception`yakalarsanız `catch` bloğunun sonundaki `throw` anahtar sözcüğünü kullanarak yeniden oluşturun.
- Bir `catch` bloğu bir özel durum değişkeni tanımlıyorsa, oluşan özel durum türü hakkında daha fazla bilgi edinmek için onu kullanabilirsiniz.
- Özel durumlar, `throw` anahtar sözcüğü kullanılarak açıkça bir program tarafından oluşturulabilir.
- Özel durum nesneleri, hata hakkında, çağrı yığınının durumu ve hatanın metin açıklaması gibi ayrıntılı bilgiler içerir.
- Bir özel durum oluşsa bile `finally` bloğundaki kod yürütülür. Kaynakları serbest bırakmak için `finally` bloğu kullanın, örneğin, `try` bloğunda açılan tüm akışları veya dosyaları kapatın.
- .NET Framework yönetilen özel durumlar, Win32 yapılandırılmış özel durum işleme mekanizmasının üzerine uygulanır. Daha fazla bilgi için, bkz. [yapılandırılmış özel durum işlemeC++(C/)](/cpp/cpp/structured-exception-handling-c-cpp) ve [Win32 yapılandırılmış özel durum işleme derinlikleri üzerinde çökme kursu](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>İlgili Bölümler

Özel durumlar ve özel durum işleme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Özel Durumları Kullanma](using-exceptions.md)
- [Özel Durum İşleme](exception-handling.md)
- [Özel Durumlar Oluşturma ve Atma](creating-and-throwing-exceptions.md)
- [Derleyicinin Ürettiği Özel Durumlar](compiler-generated-exceptions.md)
- [Nasıl yapılır: try/catch kullanarak özel durum Işleme (C# Programlama Kılavuzu)](how-to-handle-an-exception-using-try-catch.md)
- [Nasıl yapılır: Finally Kullanarak Temizleme Kodu Yürütme](how-to-execute-cleanup-code-using-finally.md)
- [Nasıl yapılır: CLS Olmayan Özel Durum Yakalama](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [özel durumlar](~/_csharplang/spec/exceptions.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- [C# Programlama Kılavuzu](../index.md)
- [C# Anahtar Sözcükleri](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Özel Durumlar](../../../standard/exceptions/index.md)
