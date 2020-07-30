---
title: Özel durumlar ve özel durum Işleme-C# Programlama Kılavuzu
description: Özel durumlar ve özel durum işleme hakkında bilgi edinin. Bu C# özellikleri, bir program çalışırken gerçekleşen beklenmedik veya olağanüstü durumlarla başa çıkmanıza yardımcı olur.
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 4be327be4e183d60e440358254aeb9c68fcf25ca
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303393"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)

C# dilinin özel durum işleme özellikleri, bir program çalışırken oluşan beklenmedik veya olağanüstü durumlarla ilgilenmenize yardımcı olur. Özel durum işleme `try` , `catch` başarılı olmayan eylemleri denemek için,, ve anahtar kelimelerini kullanır, bunu yapmak için `finally` makul olduğuna karar verirken sorunları işleyebilir ve kaynakları daha sonra temizleyebiliriz. Özel durumlar ortak dil çalışma zamanı (CLR), .NET veya üçüncü taraf kitaplıkları tarafından veya uygulama kodu tarafından oluşturulabilir. Özel durumlar anahtar sözcüğü kullanılarak oluşturulur `throw` .

Çoğu durumda, kodunuzun doğrudan çağırdığı bir yöntem tarafından değil, çağrı yığınında daha sonra başka bir yöntem tarafından bir özel durum atılır. Bu durumda, CLR, belirli bir özel durum türü için blok içeren bir yöntemi arayarak yığını geriye doğru `catch` yürütür ve `catch` bulursa bu blok üzerinde yürütülür. `catch`Çağrı yığınında herhangi bir yerde uygun bir blok bulmaz, işlemi sonlandırır ve kullanıcıya bir ileti görüntüler.

Bu örnekte, bir yöntem sıfıra bölme için test eder ve hatayı yakalar. Özel durum işleme olmadan, bu program bir **Dividebysıfırlaması özel durumu** ile sonlandırılır ve işlenmemiş bir hatadır.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Özel durumlara genel bakış

Özel durumlar aşağıdaki özelliklere sahiptir:

- Özel durumlar, tüm sonunda türetilen türlerdir `System.Exception` .
- `try`Özel durumlar oluşturabilecek deyimler etrafında bir blok kullanın.
- Blokta bir özel durum oluştuktan sonra `try` Denetim akışı, çağrı yığınında herhangi bir yerde bulunan ilk ilişkili özel durum işleyicisine atlar. C# ' de, `catch` bir özel durum işleyicisini tanımlamak için anahtar sözcüğü kullanılır.
- Belirli bir özel durum için özel durum işleyicisi yoksa, program yürütmeyi bir hata iletisiyle sonlandırır.
- İşleyebilmediğiniz ve uygulamayı bilinen bir durumda bırakarak bir özel durumu yakalamayın. Yakalar `System.Exception` , `throw` bloğunun sonundaki anahtar sözcüğünü kullanarak yeniden oluşturun `catch` .
- Bir `catch` blok bir özel durum değişkeni tanımlıyorsa, oluşan özel durum türü hakkında daha fazla bilgi edinmek için onu kullanabilirsiniz.
- Özel durumlar, anahtar sözcüğü kullanılarak bir program tarafından açıkça oluşturulabilir `throw` .
- Özel durum nesneleri, hata hakkında, çağrı yığınının durumu ve hatanın metin açıklaması gibi ayrıntılı bilgiler içerir.
- Bir `finally` özel durum oluşsa bile bloktaki kod yürütülür. Kaynakları serbest bırakmak için bir `finally` blok kullanın, örneğin, bloğunda açılan tüm akışları veya dosyaları kapatmak `try` .
- .NET 'teki yönetilen özel durumlar, Win32 yapılandırılmış özel durum işleme mekanizmasının üzerine uygulanır. Daha fazla bilgi için, bkz. [yapılandırılmış özel durum işleme (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) ve [Win32 yapılandırılmış özel durum işleme derinlikleri üzerinde çökme kursu](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>İlgili Bölümler

Özel durumlar ve özel durum işleme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Özel Durumlar Kullanma](using-exceptions.md)
- [Özel Durum İşleme](exception-handling.md)
- [Özel Durumlar Oluşturma ve Atma](creating-and-throwing-exceptions.md)
- [Derleyicinin Ürettiği Özel Durumlar](compiler-generated-exceptions.md)
- [Try/catch kullanarak özel durum işleme (C# Programlama Kılavuzu)](how-to-handle-an-exception-using-try-catch.md)
- [Finally anahtar sözcüğünü kullanarak temizleme kodu yürütme](how-to-execute-cleanup-code-using-finally.md)
- [CLS dışı özel durumu yakalama](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [özel durumlar](~/_csharplang/spec/exceptions.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- [C# Programlama Kılavuzu](../index.md)
- [C# anahtar sözcükleri](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Özel durumlar](../../../standard/exceptions/index.md)
