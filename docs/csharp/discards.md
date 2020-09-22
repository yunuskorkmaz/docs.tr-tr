---
title: Atarsa-C# Kılavuzu
description: ", Atanmamış, discardable değişkenleri ve atma 'un kullanılabileceği yollarla ilgili olarak, C# ' nin atma desteğini açıklar."
ms.technology: csharp-fundamentals
ms.date: 09/22/2020
ms.openlocfilehash: 4de48aebaeb896b198b2e9f2431c6a38ba11469e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869329"
---
# <a name="discards---c-guide"></a>Atarsa-C# Kılavuzu

C# 7,0 ' den itibaren C#, uygulama kodunda kasıtlı olarak kullanılmamış olan geçici ve kukla değişkenler olan atma 'yı destekler. Atma, atanmamış değişkenlere eşdeğerdir; Bunlar bir değere sahip değildir. Yalnızca tek bir atma değişkeni olduğundan ve bu değişkene ayrılan depolama alanı bulunmayabilir, atma işlemi bellek ayırmalarını azaltabilir. Kodunuzun amacını açık hale yaptığından, okunabilirliği ve bakım yapamazı geliştirir.

Bir değişkenin, adı olarak alt çizgi () atayarak bir atma olduğunu belirtirsiniz `_` . Örneğin, aşağıdaki yöntem çağrısı, ilk ve ikinci değerlerin dıştığı 3 tanımlama grubu döndürür ve *alan* , daha önce bildirildiği bir değişken *Getcityınformation*tarafından döndürülen karşılık gelen üçüncü bileşene ayarlanır:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

C# 7,0 ve üzeri sürümlerde, atma aşağıdaki bağlamlarda atamalar içinde desteklenir:

- Kayıt düzeni ve nesne [oluşturma](deconstruct.md).
- Ve [anahtarı](language-reference/keywords/switch.md)ile [eşleşen](language-reference/keywords/is.md) model.
- Parametrelere sahip yöntemlere çağrılar `out` .
- Kapsamda olmayan tek başına `_` `_` .

C# 9,0 ' den başlayarak, bir lambda ifadesinin kullanılmayan giriş parametrelerini belirtmek için atarsa ' u kullanabilirsiniz. Daha fazla bilgi için [lambda ifadeleri](language-reference/operators/lambda-expressions.md) makalesinin [lambda ifadesinin giriş parametreleri](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) bölümüne bakın.

`_`Geçerli bir atma olduğunda, değerini alma veya atama işleminde kullanma girişimi, "' \_ ' adı geçerli bağlamda yok" hatasını üretir. Bunun nedeni `_` , bir değer atanmamıştır ve bir depolama konumu atanmayabilir. Gerçek bir değişkense, önceki örnekte olduğu gibi birden fazla değeri atlamadınız.

## <a name="tuple-and-object-deconstruction"></a>Demet ve nesne oluşturmayı kaldırma

Atma, uygulama kodunuz bazı demet öğeleri kullandığında ancak diğerlerini yoksaytığında tanımlama grupları ile çalışırken özellikle yararlıdır. Örneğin, aşağıdaki yöntem, `QueryCityDataForYears` şehir adı, alanı, yıl, bu yıl için şehir popülasyonu, ikinci yıl ve bu ikinci yıl için şehir popülasyonu olan 6 kayıt döndürür. Örnek, bu iki yıl arasındaki popülasyondaki değişikliği gösterir. Kayıt kümesinden kullanılabilen veriler, şehir alanıyla ilgilentik ve tasarım zamanında şehir adını ve iki tarihi biliyoruz. Sonuç olarak, yalnızca kayıt düzeninde depolanan iki popülasyon değeri ile ilgileniyoruz ve kalan değerlerini atma olarak işleyebilir.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Atma ile tanımlama gruplarını kaldırma hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct`Bir sınıf, yapı veya arabirim yöntemi Ayrıca bir nesneden belirli bir veri kümesini almanıza ve oluşturmanıza olanak sağlar. Yalnızca ayrıştırılmış değerlerin yalnızca bir alt kümesiyle çalışmayı düşünüyorsanız, atma ' yı kullanabilirsiniz. Aşağıdaki örnek, bir `Person` nesnesini dört dizeye (ilk ve son adlar, şehir ve eyalet) ayırır, ancak son adı ve durumu atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Kullanıcı tanımlı türleri atma ile kaldırma hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Ve ile eşleşen desenler `switch``is`

*Atma stili* [, ın](language-reference/keywords/is.md) ve [anahtar](language-reference/keywords/switch.md) anahtar sözcükleriyle birlikte eşleşen düzende kullanılabilir. Her ifade her zaman atma düzeniyle eşleşir.

Aşağıdaki örnek `ProvidesFormatInfo` , bir nesnenin bir uygulama verip içermediğini ve nesnenin olup olmadığını test etmek için [,,,,](language-reference/keywords/is.md) bir yöntemi tanımlar <xref:System.IFormatProvider> `null` . Ayrıca, başka bir türdeki null olmayan nesneleri işlemek için de atma modelini kullanır.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Out parametreleri ile yöntemlere çağrılar

`Deconstruct`Kullanıcı tanımlı bir türü (bir sınıf, yapı veya arabirim örneği) oluşturmak için yöntemini çağırırken bağımsız değişkenlerin değerlerini atabilirsiniz `out` . Ancak, `out` Out parametresiyle herhangi bir yöntemi çağırırken bağımsız değişkenlerin değerini de atabilirsiniz.

Aşağıdaki örnek, bir tarihin dize temsilinin geçerli kültür içinde geçerli olup olmadığını belirlemek için [DateTime. Trypari (dize, Out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) yöntemini çağırır. Örnek yalnızca tarih dizesini doğrulamaya ve tarihi ayıklamak için ayrıştırılmaya karşı düşünüldüğünde, `out` yöntemin bağımsız değişkeni bir atma işlemi olur.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Tek başına atma

Yok saymayı seçtiğiniz herhangi bir değişkeni belirtmek için tek başına atmayı kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Threading.Tasks.Task> zaman uyumsuz bir işlem tarafından döndürülen nesneyi yoksaymak için tek başına atmayı kullanır. Bu, işlemin tamamlanana kadar yaptığı özel durumu gizlemeyi etkiler.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

`_`Ayrıca geçerli bir tanımlayıcı olduğunu unutmayın. Desteklenen bir bağlam dışında kullanıldığında, `_` atma olarak kabul edilir, ancak geçerli bir değişken olarak değerlendirilir. Adlı bir tanımlayıcı `_` zaten kapsamda ise, `_` tek başına atma olarak kullanılması şu şekilde olabilir:

- İstenen atma değeri atanarak kapsam içi değişkenin değerini yanlışlıkla değiştirme `_` . Örnek:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Tür güvenliğini ihlal eden bir derleyici hatası. Örnek:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Derleyici hatası CS0136, " \_ Bu ad bir yerel veya parametre tanımlamak için kapsayan bir yerel kapsamda kullanıldığı için," ' ' adlı yerel veya parametre bu kapsamda bildirilemez. " Örnek:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Demetleri ve diğer türleri ayrıştırma](deconstruct.md)
- [`is` sözcükle](language-reference/keywords/is.md)
- [`switch` sözcükle](language-reference/keywords/switch.md)
