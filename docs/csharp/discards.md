---
title: İptali - C# Kılavuzu
description: Atanmamış olan atar, discardable değişkenleri ve iptali kullanılabilir yöntemleri için C# ' nin desteğini açıklar.
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.openlocfilehash: 761fb69d3bc774975caf63b8aa665f8c19c0430a
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50045658"
---
# <a name="discards---c-guide"></a>İptali - C# Kılavuzu

C# 7.0 ile başlayarak, C# destekler atar, uygulama kodunda kasıtlı olarak kullanılmayan geçici, işlevsiz değişkenleri olduğu. Atanmamış değişkenlere atar eşdeğerdir; bir değere sahip değil. Yalnızca bir tek atma değişken yoktur ve bu değişken depolama bile ayrılmış değil çünkü atar bellek ayırmaları azaltabilir. Temizle, kodun amacı yaptıkları için bakım ve okunabilirliği geliştirmek.

Alt çizgi atayarak bir değişken bir atma olduğunu göstermek (`_`) ad olarak. Örneğin, aşağıdaki yöntem çağrısını birinci ve ikinci değerler atar: 3-tanımlama grubu döndürür ve *alan* tarafından döndürülen üçüncü karşılık gelen bileşeninden ayarlamak için daha önce bildirilen bir değişken  *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

C# 7.0, iptali aşağıdaki bağlamlara atamalarını desteklenir:

- Dizi ve nesne [ayrıştırma](deconstruct.md).
- İle desen eşleştirme [olduğu](language-reference/keywords/is.md) ve [geçiş](language-reference/keywords/switch.md).
- İle yöntemlere yapılan çağrılar `out` parametreleri.
- Tek başına bir `_` hiçbir `_` kapsamdadır.

Zaman `_` olan değerini veya oluşturur, atama işleminde bir derleyici hatası CS0301, kullanım almaya çalışırken, geçerli bir atma "adı '\_' geçerli bağlamda yok". Bunun nedeni, `_` bir değer atanmadı ve hatta bir depolama konumu atanamaz. Gerçek bir değişken olsaydı, önceki örnekte olduğu gibi birden fazla değer AT değil.

## <a name="tuple-and-object-deconstruction"></a>Dizi ve nesne ayrıştırma

İptali özellikle uygulama kodunuzun bazı dizi öğeleri kullanır ancak diğerleri yoksayar tanımlama grupları ile çalışma yararlıdır. Örneğin, aşağıdaki `QueryCityDataForYears` yöntemi bir şehir, kendi alanı, bir yıl, bu yıl, ikinci yıl ve bu ikinci yıl için city'nin popülasyonu city'nin nüfusunu adı ile 6-tanımlama grubu döndürür. Bu örnek, popülasyondaki bu iki yıl arasında değişiklik gösterir. Veri tanımlama grubu bulunan, şehir alanıyla unconcerned duyuyoruz ve şehir adı ve tasarım zamanında iki tarih biliyoruz. Sonuç olarak, biz tanımlama grubunda depolanan iki popülasyon değerleri yalnızca ilginizi çeken ve kalan değerleri atar olarak işleyebilir.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Ayrıştırma diziler iptali ile ilgili daha fazla bilgi için [demetleri ve diğer türleri ayrıştırma](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct` Bir sınıf, yapı veya arabirim yöntemini de almak ve belirli bir nesne verilerden birtakım Ayrıştır olanak tanır. Yalnızca bir alt kümesini ayrıştırılmış değerleri ile çalışma ilgilendiğiniz atar kullanabilirsiniz. Aşağıdaki örnek deconstructs bir `Person` nesne dört dizelere (ilk ve son adları, şehir ve durumu), ancak son adı ve durum atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Kullanıcı tanımlı türler iptali ile ayrıştırma daha fazla bilgi için bkz: [demetleri ve diğer türleri ayrıştırma](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>İle desen eşleştirme `switch` ve `is`

*Atma deseni* deseni ile eşleşen kullanılabilir [olduğu](language-reference/keywords/is.md) ve [geçiş](language-reference/keywords/switch.md) anahtar sözcükleri. Her ifade her zaman atma deseni ile eşleşir.

Aşağıdaki örnekte tanımlayan bir `ProvidesFormatInfo` kullanan yöntemi [olduğu](language-reference/keywords/is.md) deyimleri bir nesne sağlayıp sağlamadığını belirlemek için bir <xref:System.IFormatProvider> uygulama ve testleri nesnedir `null`. Ayrıca herhangi bir tür null olmayan nesneleri işlemek için atma deseni kullanır.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Out parametreleri ile yöntemlere yapılan çağrılar

Çağrılırken `Deconstruct` AT değerlerini tek bir kullanıcı tanımlı tür (bir sınıf, yapı veya arabirim örneği), ayrıştırma yönteminin `out` bağımsız değişkenler. Ancak değerini de atabilirsiniz `out` out parametresi ile herhangi bir yöntemi çağrılırken bağımsız değişkenler.

Aşağıdaki örnek çağrıları [DateTime.TryParse (dize, DateTime kullanıma)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) bir tarih dize gösterimini geçerli kültürün geçerli olup olmadığını belirlemek için yöntemi. Örnek yalnızca tarih dizesi doğrulama ile değil, tarih, ayıklanacak ayrıştırma endişe çünkü `out` yöntemi için bağımsız bir atma değişkenidir.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Tek başına AT

Tek başına atma yok saymak için seçtiğiniz herhangi bir değişken belirtmek için kullanabilirsiniz. Aşağıdaki örnek bir tek başına atma gözardı eder <xref:System.Threading.Tasks.Task> zaman uyumsuz bir işlem tarafından döndürülen nesne. Bu işlemin tamamlanması yaklaşık olarak oluşturan bir özel durum gizleme etkisi vardır.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Unutmayın `_` da geçerli bir tanımlayıcıdır. Desteklenen bir bağlamı dışında kullanıldığında `_` bir atma olarak değil, ancak geçerli bir değişken olarak kabul edilir. Tanımlayıcı adlı `_` zaten kullanımını kapsam içinde olan `_` atma tek başına bir neden olabilir:

- Kapsamdaki değerinin yanlışlıkla değişiklik `_` hedeflenen atma değerini atayarak değişken. Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Tür güvenliği ihlal bir derleyici hatası. Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Derleyici Hatası CS0136, "yerel veya parametre adındaki '\_' adı, bir kapanış yerel kapsamında bir Yereli veya parametreyi tanımlamak için kullanılır çünkü bu kapsamda bildirilemez." Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Demetleri ve diğer türleri ayrıştırma](deconstruct.md)
- [`is` Anahtar sözcüğü](language-reference/keywords/is.md)
- [`switch` Anahtar sözcüğü](language-reference/keywords/switch.md)
