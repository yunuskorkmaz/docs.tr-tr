---
title: Özel durumlar ve özel durum C# işleme-Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: c2b991a45a53ce4a8295d6181da11cb09fda6ddb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590201"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)
C# Dilin özel durum işleme özellikleri, bir program çalışırken oluşan beklenmedik veya olağanüstü durumlarla ilgilenmenize yardımcı olur. Özel durum işleme `try`, başarılı olmayan eylemleri `finally` denemek için, `catch`, ve anahtar kelimelerini kullanır, bunu yapmak için makul olduğuna karar verirken sorunları işleyebilir ve kaynakları daha sonra temizleyebiliriz. Özel durumlar ortak dil çalışma zamanı (CLR) tarafından, .NET Framework veya herhangi bir üçüncü taraf kitaplığı tarafından ya da uygulama kodu tarafından oluşturulabilir. Özel durumlar `throw` anahtar sözcüğü kullanılarak oluşturulur.  
  
 Çoğu durumda, kodunuzun doğrudan çağırdığı bir yöntem tarafından değil, çağrı yığınında daha sonra başka bir yöntem tarafından bir özel durum atılır. Bu durumda, clr, belirli bir özel durum türü için `catch` blok içeren bir yöntemi arayarak yığını geriye doğru yürütür ve bulursa bu `catch` blok üzerinde yürütülür. Çağrı yığınında herhangi bir yerde `catch` uygun bir blok bulmaz, işlemi sonlandırır ve kullanıcıya bir ileti görüntüler.  
  
 Bu örnekte, bir yöntem sıfıra bölme için test eder ve hatayı yakalar. Özel durum işleme olmadan, bu program bir **Dividebysıfırlaması özel durumu** ile sonlandırılır ve işlenmemiş bir hatadır.  
  
 [!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]  
  
## <a name="exceptions-overview"></a>Özel durumlara genel bakış  
 Özel durumlar aşağıdaki özelliklere sahiptir:  
  
- Özel durumlar, tüm sonunda türetilen `System.Exception`türlerdir.  
  
- Özel durumlar `try` oluşturabilecek deyimler etrafında bir blok kullanın.  
  
- `try` Blokta bir özel durum oluştuktan sonra Denetim akışı, çağrı yığınında herhangi bir yerde bulunan ilk ilişkili özel durum işleyicisine atlar. ' C#De, `catch` bir özel durum işleyicisini tanımlamak için anahtar sözcüğü kullanılır.  
  
- Belirli bir özel durum için özel durum işleyicisi yoksa, program yürütmeyi bir hata iletisiyle sonlandırır.  
  
- İşleyebilmediğiniz ve uygulamayı bilinen bir durumda bırakarak bir özel durumu yakalamayın. Yakalar `System.Exception` `throw` , bloğunun`catch` sonundaki anahtar sözcüğünü kullanarak yeniden oluşturun.  
  
- Bir `catch` blok bir özel durum değişkeni tanımlıyorsa, oluşan özel durum türü hakkında daha fazla bilgi edinmek için onu kullanabilirsiniz.  
  
- Özel durumlar, `throw` anahtar sözcüğü kullanılarak bir program tarafından açıkça oluşturulabilir.  
  
- Özel durum nesneleri, hata hakkında, çağrı yığınının durumu ve hatanın metin açıklaması gibi ayrıntılı bilgiler içerir.  
  
- Bir `finally` özel durum oluşsa bile bloktaki kod yürütülür. Kaynakları serbest `finally` bırakmak için bir blok kullanın, örneğin, `try` bloğunda açılan tüm akışları veya dosyaları kapatmak.  
  
- .NET Framework yönetilen özel durumlar, Win32 yapılandırılmış özel durum işleme mekanizmasının üzerine uygulanır. Daha fazla bilgi için, bkz. [yapılandırılmış özel durum işlemeC++(C/)](/cpp/cpp/structured-exception-handling-c-cpp) ve [Win32 yapılandırılmış özel durum işleme derinlikleri üzerinde çökme kursu](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Özel durumlar ve özel durum işleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Özel Durumları Kullanma](./using-exceptions.md)  
  
- [Özel Durum İşleme](./exception-handling.md)  
  
- [Özel Durumlar Oluşturma ve Atma](./creating-and-throwing-exceptions.md)  
  
- [Derleyicinin Ürettiği Özel Durumlar](./compiler-generated-exceptions.md)  
  
- [Nasıl yapılır: Try/catch kullanarak özel durum işleme (C# Programlama Kılavuzu)](./how-to-handle-an-exception-using-try-catch.md)  
  
- [Nasıl yapılır: Son kullanılan temizleme kodunu yürütme](./how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [özel durumlar](~/_csharplang/spec/exceptions.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- [C# Programlama Kılavuzu](../index.md)
- [C# Anahtar Sözcükleri](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Özel Durumlar](../../../standard/exceptions/index.md)
