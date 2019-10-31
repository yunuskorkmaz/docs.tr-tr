---
title: Atma- C# kılavuz
description: Atanmamış C#, discardable değişkenleri ve atma 'un kullanılabileceği yollarla ilgili olarak, atma desteği açıklanmaktadır.
ms.technology: csharp-fundamentals
ms.date: 07/21/2017
ms.openlocfilehash: a76e7fc13f92ec0de87153bb35eb3924bb317616
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100633"
---
# <a name="discards---c-guide"></a>Atma- C# kılavuz

7,0 ile C# başlayarak, C# uygulama kodunda kasıtlı olarak kullanılmamış olan geçici ve kukla değişkenler olan atma 'yı destekler. Atma, atanmamış değişkenlere eşdeğerdir; Bunlar bir değere sahip değildir. Yalnızca tek bir atma değişkeni olduğundan ve bu değişkene ayrılan depolama alanı bulunmayabilir, atma işlemi bellek ayırmalarını azaltabilir. Kodunuzun amacını açık hale yaptığından, okunabilirliği ve bakım yapamazı geliştirir.

Bir değişkenin, adı olarak alt çizgi (`_`) atayarak bir atma olduğunu belirtirsiniz. Örneğin, aşağıdaki yöntem çağrısı, ilk ve ikinci değerlerin dıştığı 3 tanımlama grubu döndürür ve *alan* , daha önce bildirildiği bir değişken *Getcityınformation*tarafından döndürülen karşılık gelen üçüncü bileşene ayarlanır:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

7,0 C# ' de, atma aşağıdaki bağlamlarda atamalar içinde desteklenir:

- Kayıt düzeni ve nesne [oluşturma](deconstruct.md).
- Ve [anahtarı](language-reference/keywords/switch.md)ile [eşleşen](language-reference/keywords/is.md) model.
- `out` parametreli yöntemlere çağrılar.
- Kapsamda `_` olmadığında tek başına `_`.

`_` geçerli bir atıldığında, değerini alma veya atama işleminde kullanma girişimi, "\_' adı geçerli bağlamda yok" hatasını üretir. Bunun nedeni `_` bir değer atanmamıştır ve hatta bir depolama konumu atanmayabilir. Gerçek bir değişkense, önceki örnekte olduğu gibi birden fazla değeri atlamadınız.

## <a name="tuple-and-object-deconstruction"></a>Demet ve nesne oluşturmayı kaldırma

Atma, uygulama kodunuz bazı demet öğeleri kullandığında ancak diğerlerini yoksaytığında tanımlama grupları ile çalışırken özellikle yararlıdır. Örneğin, aşağıdaki `QueryCityDataForYears` yöntemi, şehir adı, alanı, yıl, bu yıl için şehir popülasyonu, ikinci yıl ve bu ikinci yıl için şehir popülasyonu olan 6 tanımlama grubu döndürür. Örnek, bu iki yıl arasındaki popülasyondaki değişikliği gösterir. Kayıt kümesinden kullanılabilen veriler, şehir alanıyla ilgilentik ve tasarım zamanında şehir adını ve iki tarihi biliyoruz. Sonuç olarak, yalnızca kayıt düzeninde depolanan iki popülasyon değeri ile ilgileniyoruz ve kalan değerlerini atma olarak işleyebilir.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Atma ile tanımlama gruplarını kaldırma hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](deconstruct.md#deconstructing-tuple-elements-with-discards).

Bir sınıf, yapı veya arabirimin `Deconstruct` yöntemi, bir nesneden belirli bir veri kümesini almanıza ve oluşturmanıza da olanak sağlar. Yalnızca ayrıştırılmış değerlerin yalnızca bir alt kümesiyle çalışmayı düşünüyorsanız, atma ' yı kullanabilirsiniz. Aşağıdaki örnek, bir `Person` nesnesini dört dizeye (ilk ve son adlar, şehir ve eyalet) ayırır, ancak son adı ve durumu atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Kullanıcı tanımlı türleri atma ile kaldırma hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>`switch` ve `is` ile eşleşen desenler

*Atma stili* [, ın](language-reference/keywords/is.md) ve [anahtar](language-reference/keywords/switch.md) anahtar sözcükleriyle birlikte eşleşen düzende kullanılabilir. Her ifade her zaman atma düzeniyle eşleşir.

Aşağıdaki örnek, bir nesnenin bir <xref:System.IFormatProvider> uygulama verip içermediğini ve nesnenin `null`olup olmadığını test etmek için [,,](language-reference/keywords/is.md) bir nesnesinin bir `ProvidesFormatInfo` yöntemini tanımlar. Ayrıca, başka bir türdeki null olmayan nesneleri işlemek için de atma modelini kullanır.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Out parametreleri ile yöntemlere çağrılar

Kullanıcı tanımlı bir türü (bir sınıf, yapı veya arabirim örneği) oluşturmak için `Deconstruct` yöntemi çağrılırken, bağımsız `out` bağımsız değişkenlerin değerlerini atabilirsiniz. Ancak, Out parametresiyle herhangi bir yöntemi çağırırken `out` bağımsız değişkenlerin değerini de atabilirsiniz.

Aşağıdaki örnek, bir tarihin dize temsilinin geçerli kültür içinde geçerli olup olmadığını belirlemek için [DateTime. Trypari (dize, Out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) yöntemini çağırır. Örnek yalnızca tarih dizesini doğrulamaya ve tarihi ayıklamak için ayrıştırılmaya karşı düşünüldüğünde, yönteme `out` bağımsız değişkeni atılır.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Tek başına atma

Yok saymayı seçtiğiniz herhangi bir değişkeni belirtmek için tek başına atmayı kullanabilirsiniz. Aşağıdaki örnek, zaman uyumsuz bir işlem tarafından döndürülen <xref:System.Threading.Tasks.Task> nesnesini yoksaymak için tek başına atmayı kullanır. Bu, işlemin tamamlanana kadar yaptığı özel durumu gizlemeyi etkiler.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

`_` de geçerli bir tanımlayıcı olduğunu unutmayın. Desteklenen bir bağlam dışında kullanıldığında `_`, atma olarak kabul edilir ancak geçerli bir değişken olarak değerlendirilir. `_` adlı bir tanımlayıcı zaten kapsamda ise, tek başına bir atma olarak `_` kullanılması şu şekilde olabilir:

- İstenen atma değeri atanarak, kapsam içi `_` değişkeninin değerini yanlışlıkla değiştirme. Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Tür güvenliğini ihlal eden bir derleyici hatası. Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Derleyici hatası CS0136, "Bu ad bir yerel veya parametre tanımlamak için kapsayan bir yerel kapsamda kullanıldığından,"\_' adlı bir yerel veya parametre bu kapsamda bildirilemez. " Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Demetleri ve diğer türleri ayrıştırma](deconstruct.md)
- [`is` anahtar sözcüğü](language-reference/keywords/is.md)
- [`switch` anahtar sözcüğü](language-reference/keywords/switch.md)
