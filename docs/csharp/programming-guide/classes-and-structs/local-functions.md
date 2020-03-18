---
title: Yerel işlevler - C# Programlama Kılavuzu
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: b6924b8981af5115a474eeb6b2e5376dd1b17ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170241"
---
# <a name="local-functions-c-programming-guide"></a>Yerel işlevler (C# Programlama Kılavuzu)

C# 7.0 ile başlayarak, C# *yerel işlevleri*destekler. Yerel işlevler, başka bir üyede iç içe olan bir türdeki özel yöntemlerdir. Yalnızca kendi üyelerinden çağrılabilirler. Yerel işlevler bildirilebilir ve şu andan itibaren çağrılabilir:

- Yöntemler, özellikle reeratör yöntemleri ve async yöntemleri
- Oluşturucular
- Özellik erişime girenler
- Etkinlik erişime girenler
- Anonim yöntemler
- Lambda ifadeleri
- Sonlandırıcılar
- Diğer yerel işlevler

Ancak, yerel işlevler ifade gövdeli bir üye içinde bildirilemez.

> [!NOTE]
> Bazı durumlarda, yerel bir işlev tarafından da desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz. Karşılaştırma için, [Lambda ifadeleri ile karşılaştırıldığında Yerel işlevler](../../local-functions-vs-lambdas.md)bakın.

Yerel işlevler, kodunuzu açıkça ortaya kovar. Kodunuzu okuyan herkes, içeren yöntem dışında yöntemin çağrılabilir olmadığını görebilir. Takım projeleri için, başka bir geliştiricinin yöntemi yanlışlıkla sınıfın veya yapının başka bir yerinden yanlışlıkla aramasını da imkansız hale getirir.

## <a name="local-function-syntax"></a>Yerel işlev sözdizimi

Yerel bir işlev, iç içe bir üyenin içinde iç içe bir yöntem olarak tanımlanır. Tanımıaşağıdaki sözdizimine sahiptir:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Yerel işlevler [async](../../language-reference/keywords/async.md) ve [güvensiz](../../language-reference/keywords/unsafe.md) değiştiriciler kullanabilirsiniz.

Yöntem parametreleri de dahil olmak üzere, ilgili üyede tanımlanan tüm yerel değişkenlere yerel işlevde erişilebilir olduğunu unutmayın.

Yöntem tanımının aksine, yerel işlev tanımı üye erişim değiştiriciyi içeremez. `private` Anahtar kelime gibi bir erişim değiştirici de dahil olmak üzere tüm yerel işlevler özel olduğundan, cs0106 derleyici hatası oluşturur, "Değiştirici 'özel' bu öğe için geçerli değildir."

> [!NOTE]
> C# 8.0'dan önce yerel `static` işlevler değiştiriciyi içeremez. `static` Anahtar kelime de dahil olmak üzere derleyici hatası CS0106 oluşturur, "Değiştirici 'statik' bu öğe için geçerli değildir."

Ayrıca, öznitelikler yerel işleve veya parametrelerine ve tür parametrelerine uygulanamaz.

Aşağıdaki örnek, adlı bir `AppendPathSeparator` yönteme özel olan `GetText`yerel bir işlev tanımlar:

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeye çıkmasına izin verebilmeleridir. Yöntem yineleyicileri için, özel durumlar yalnızca döndürülen sıra numaralandırıldığında su yüzüne çıkar, yineleyici alındığında değil. Async yöntemleri için, döndürülen görev bekleniyor zaman bir async yöntemi atılan tüm özel durumlar gözlenir.

Aşağıdaki örnek, belirli `OddSequence` bir aralık arasında tek sayılar numaralandırmak bir yöntem tanımlar. Numaralandırma yöntemine 100'den `OddSequence` büyük bir sayı geçtiği için, yöntem <xref:System.ArgumentOutOfRangeException>bir . Örnekteki çıktının gösterdiği gibi, özel durum yalnızca sayıyı kaydettiğinizde değil, sayıları yinelediğinizde ortaya çıkar.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Bunun yerine, doğrulama gerçekleştirirken ve aşağıdaki örnekte görüldüğü gibi, yineleyiciyi yerel bir işlevden döndürerek yineleyiciyi almadan önce bir özel durum atabilirsiniz.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Yerel işlevler, asynchronous işleminin dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir. Normalde, async yönteminde atılan özel durumlar, bir <xref:System.AggregateException>. Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasını ve özel durumlarınızın hem atılmasına hem de eşzamanlı olarak gözlenmesine izin verir.

Aşağıdaki örnek, belirli bir saniye `GetMultipleAsync` sayısı için duraklatmak ve bu saniye sayısının rasgele bir katını döndürecek bir değer döndürmek için adlandırılmış bir eşzamanlı yöntem kullanır. Maksimum gecikme 5 saniyedir; değeri <xref:System.ArgumentOutOfRangeException> 5'ten büyükse sonuç verir. Aşağıdaki örnekte de görüldüğü gibi, `GetMultipleAsync` <xref:System.AggregateException> `GetMultipleAsync` yönteme 6 değeri geçirildiğinde atılan özel durum, yöntem yürütmeye başladıktan sonra bir şekilde sarılır.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Yöntem yineleyicide yaptığımız gibi, asynchronous yöntemini aramadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden değerlendirebiliriz. Aşağıdaki örnekteki çıktının gösterdiği <xref:System.ArgumentOutOfRangeException> gibi, bir <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yöntemler](methods.md)
