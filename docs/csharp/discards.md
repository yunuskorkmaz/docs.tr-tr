---
title: Atar - C# Kılavuzu
description: Atanamayan, atılabilir değişkenler olan c#'ın atıliş desteğini ve atılların nasıl kullanılabileceğini açıklar.
ms.technology: csharp-fundamentals
ms.date: 07/21/2017
ms.openlocfilehash: a76e7fc13f92ec0de87153bb35eb3924bb317616
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73100633"
---
# <a name="discards---c-guide"></a>Atar - C# Kılavuzu

C# 7.0 ile başlayarak C#, uygulama kodunda kasıtlı olarak kullanılmayan geçici, sahte değişkenler olan atları destekler. Atıllar atanmamış değişkenlere eşdeğerdir; bir değeri yoktur. Yalnızca tek bir atma değişkeni olduğundan ve bu değişken depolama alanı bile tahsis edilemeyebileceğinden, atarlar bellek ayırmalarını azaltabilir. Kodunuzu açıkça belirttikleri için, kodun okunabilirliğini ve korunabilirliğini artırırlar.

Bir değişkenin, alt puanını (`_`) adı olarak atayarak bir attırMa olduğunu belirtirsiniz. Örneğin, aşağıdaki yöntem çağrısı, birinci ve ikinci değerlerin atıldığı ve *alanın* *GetCityInformation*tarafından döndürülen ilgili üçüncü bileşene ayarlanacak daha önce bildirilen bir değişken olduğu bir 3-tuple döndürür:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

C# 7.0'da, atamalar aşağıdaki bağlamlarda desteklenir:

- Tuple ve nesne [yapısızlaştırma.](deconstruct.md)
- Desen [ile](language-reference/keywords/is.md) eşleşen ve [anahtar](language-reference/keywords/switch.md).
- Parametreleri ile `out` yöntemleri çağırır.
- Kapsam da `_` hayır `_` olduğunda bağımsız bir.

Geçerli `_` bir atama olduğunda, değerini almaya veya bir atama işleminde kullanmaya çalışırken cs0301 derleyici\_hatası oluşturur, "Ad ' ' ' geçerli bağlamda yok". Bunun nedeni, `_` bir değer atanmamış olması ve hatta bir depolama konumu atanmamış olmasıdır. Gerçek bir değişken olsaydı, önceki örnekte olduğu gibi birden fazla değer atamadınız.

## <a name="tuple-and-object-deconstruction"></a>Tuple ve nesne yapısızlaştırma

Uygulama kodunuz bazı tuple öğeleri kullanır ken diğerlerini yok sayar, özellikle tuples ile çalışırken yararlıdır. Örneğin, aşağıdaki `QueryCityDataForYears` yöntem bir şehir, alanı, bir yıl, o yıl, ikinci yıl için şehrin nüfusu ve ikinci yıl için şehrin nüfusu adı ile 6-tuple döndürür. Örnek, bu iki yıl arasındaki nüfus değişimini göstermektedir. Tuple'dan elde edilen verilerden şehir alanıyla ilgilenmiyoruz ve şehir adını ve iki tarihi tasarım zamanında biliyoruz. Sonuç olarak, yalnızca tuple'da depolanan iki popülasyon değeriyle ilgileniyoruz ve kalan değerlerini atılarak işleyebiliriz.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Atlayışlarla tuples deconstructing hakkında daha fazla bilgi için, [deconstructing tuples ve diğer türleri](deconstruct.md#deconstructing-tuple-elements-with-discards)bakın.

Bir `Deconstruct` sınıfın, yapının veya arabirimin yöntemi, bir nesneden belirli bir veri kümesini almanızı ve dekonstrükte etmenizi de sağlar. Deconstructed değerlerin yalnızca bir alt kümesi ile çalışmak istediğinizde atar kullanabilirsiniz. Aşağıdaki örnek, bir `Person` nesneyi dört dize (ad ve soyad, şehir ve devlet) olarak belirtir, ancak soyadını ve durumu atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Atar ile kullanıcı tanımlı türleri deconstructing hakkında daha fazla bilgi için [bkz.](deconstruct.md#deconstructing-a-user-defined-type-with-discards)

## <a name="pattern-matching-with-switch-and-is"></a>Desen ile `switch` eşleşen ve`is`

*Atma deseni,* [is](language-reference/keywords/is.md) ve [anahtar](language-reference/keywords/switch.md) anahtar kelimeleri ile eşleşen desende kullanılabilir. Her ifade her zaman atma desenine eşleşir.

Aşağıdaki örnek, `ProvidesFormatInfo` bir nesnenin [is](language-reference/keywords/is.md) <xref:System.IFormatProvider> bir uygulama sağlayıp sağlamadığını belirlemek ve nesnenin `null`. Ayrıca, başka bir türdeki null olmayan nesneleri işlemek için atma deseni kullanır.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Parametreleri dışa doğru olan yöntemlere çağrı

Kullanıcı tanımlı bir türü (bir sınıf, yapı veya arabirim örneği) yapısızlaştırılması için `Deconstruct` `out` yöntemi çağırırken, bağımsız değişkenlerin değerlerini atabilirsiniz. Ancak, herhangi bir yöntemi `out` dış parametreyle ararken bağımsız değişkenlerin değerini de atabilirsiniz.

Aşağıdaki örnek, bir tarihin dize gösteriminin geçerli kültürde geçerli olup olmadığını belirlemek için [DateTime.TryParse (String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) yöntemini çağırır. Örnek yalnızca tarih dizesini doğrulamakla ilgili olduğundan ve tarihi ayıklamak için `out` ayrıştırma ile değil, yöntemin bağımsız değişkeni bir attır.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Tek başına atma

Yoksaymayı seçtiğiniz herhangi bir değişkeni belirtmek için tek başına bir atma kullanabilirsiniz. Aşağıdaki örnek, eşyoklama işlemi <xref:System.Threading.Tasks.Task> yle döndürülen nesneyi yok saymak için tek başına bir atma kullanır. Bu, işlemin tamamlanmak üzere olduğu gibi attığı özel durumu bastırma etkisine sahiptir.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Bunun `_` da geçerli bir tanımlayıcı olduğunu unutmayın. Desteklenen bir bağlam Dışında kullanıldığında, bir atma olarak değil, `_` geçerli bir değişken olarak kabul edilir. Adı verilen `_` bir tanımlayıcı zaten kapsamdaysa, `_` tek başına atma olarak kullanımı aşağıdakileri yapabilir:

- Amaçlanan atın değerini atayarak `_` kapsam içi değişkenin değerinin yanlışlıkla değiştirilmesi. Örnek:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Tür güvenliğini ihlal etmek için derleyici hatası. Örnek:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Derleyici hatası CS0136, "' '\_adlı yerel veya parametre bu kapsamda bildirilemez, çünkü bu ad yerel veya parametre tanımlamak için çevreleyen bir yerel kapsamda kullanılır." Örnek:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Demetleri ve diğer türleri ayrıştırma](deconstruct.md)
- [`is`Anahtar kelime](language-reference/keywords/is.md)
- [`switch`Anahtar kelime](language-reference/keywords/switch.md)
