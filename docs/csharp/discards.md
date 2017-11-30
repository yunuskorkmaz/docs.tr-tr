---
title: "İptali - C# Kılavuzu"
description: "C# ' ın atanmamış iptali, discardable değişkenleri ve iptali kullanılabilir yöntemleri için destek açıklanır."
keywords: .NET, .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 800a27d2d186c738dceb6838aa669377a0c07b01
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2017
---
# <a name="discards---c-guide"></a>İptali - C# Kılavuzu

C# 7 ile başlayan, C# destekler atar, uygulama kodunda kasıtlı olarak kullanılmayan geçici, sahte değişkenleri olduğu. İptali atanmamış değişkenlere eşdeğer; bir değere sahip değil. Yalnızca bir tek atma değişken yoktur ve bu değişken depolama bile ayrılan değil çünkü iptali bellek ayırmaları azaltabilir. Kodunuzu Temizle amacı olun çünkü bunlar okunabilirlik ve bakımı geliştirin.

Alt çizgi atayarak bir değişken bir atma olduğunu gösteriyor (`_`) ad olarak. Örneğin, aşağıdaki yöntem çağrısı birinci ve ikinci değer iptali olacak 3-tanımlama grubu döndürür ve *alanı* tarafından döndürülen ilgili üçüncü bileşen olarak daha önce bildirilen değişkenidir  *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

C# 7'de, aşağıdaki bağlamlarında atamaları iptali desteklenir:

- Dizi ve nesne [deconstruction](deconstruct.md).
- İle desen eşleştirme [olan](language-reference/keywords/is.md) ve [geçiş](language-reference/keywords/switch.md).
- Yöntemleriyle çağrıları `out` parametreleri.
- Tek başına `_` durumlarda `_` kapsamında değil.

Zaman `_` olan değerini veya atama işleminde ürettiği derleyici hatası CS0301, kullanım almaya geçerli bir at "adı '\_' geçerli bağlamda mevcut değil". Bunun nedeni, `_` bir değer atanmadı ve bir depolama konumu bile atanmış olmamalıdır. Gerçek bir değişken olsaydı, önceki örnekte olduğu gibi birden fazla değer atmak değil.

## <a name="tuple-and-object-deconstruction"></a>Dizi ve nesne deconstruction

İptali uygulama kodunuz bazı başlığın öğeleri kullanır ancak başkalarının yoksayar içeren başlık çalışma özellikle yararlı olur. Örneğin, aşağıdaki `QueryCityDataForYears` yöntemi bir şehir, kendi alanı, bir yılın, o yıl, ikinci bir yıl ve bu ikinci yıl Şehir 's popülasyon Şehir 's popülasyon adıyla 6-tanımlama grubu döndürür. Örnek popülasyondaki bu iki yıl arasında değişiklik gösterir. Verileri tanımlama grubu bulunan, biz Şehir alanıyla unconcerned ve şehir adı ve tasarım zamanında iki tarih biliyoruz. Sonuç olarak, biz yalnızca düzeninde depolanan iki popülasyon değerleri ilgileniyor ve onun kalan değerler iptali olarak işleyebilir.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

İptali içeren başlık deconstructing daha fazla bilgi için bkz: [tanımlama grupları ve diğer türleri Deconstructing](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct` Sınıf, yapı veya arabirim yöntemini de alabilir ve verileri bir nesneden belirli bir dizi deconstruct olanak tanır. Yalnızca bir alt kümesini deconstructed değerleri ile çalışma ilgilendiğiniz zaman iptali kullanabilirsiniz. Aşağıdaki örnek deconstructs Ihe bir `Person` dört dizeleri (ilk ve son adları, şehir ve durumu) nesnesine ancak son adı ve durum atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Kullanıcı tanımlı türler iptali ile deconstructing daha fazla bilgi için bkz: [tanımlama grupları ve diğer türleri Deconstructing](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Deseni ile eşleşen `switch` ve`is`

*Düzeni atmak* deseni ile eşleşen kullanılabilir [olan](language-reference/keywords/is.md) ve [geçiş](language-reference/keywords/switch.md) anahtar sözcükler. Her ifadesi her zaman atma eşleştirir.

Aşağıdaki örnek tanımlayan bir `ProvidesFormatInfo` kullanan yöntemi [olan](language-reference/keywords/is.md) nesneyi sağlayıp sağlamadığını belirlemek için deyimleri bir <xref:System.IFormatProvider> uygulama ve testleri nesne olup `null`. Ayrıca herhangi bir tür null olmayan nesneleri işlemek için atma desen kullanır.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Out Parametreleri yöntemleriyle çağrıları

Çağrılırken `Deconstruct` atmak değerlerini tek tek bir kullanıcı tanımlı tür (örneği sınıf, yapı veya arabirim), deconstruct yöntemi `out` bağımsız değişkenler. Ancak değerini de atabilirsiniz `out` out parametresi ile herhangi bir yöntemini çağırmadan zaman bağımsız değişkenler. 

Aşağıdaki örnek çağrıları [DateTime.TryParse (dize, DateTime çıkışı)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) bir tarih dize gösterimini geçerli kültürün geçerli olup olmadığını belirlemek için yöntem. Örneğin yalnızca tarih dizesi doğrulama ile tarih ayıklamak için ayrıştırma değil kaygı çünkü `out` olmayan bir atma yöntemi için bağımsız değişken.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Tek başına atma

Tek başına atma yoksaymak için seçtiğiniz herhangi bir değişken belirtmek için kullanabilirsiniz. Aşağıdaki örnek bir tek başına atma gözardı eder <xref:System.Threading.Tasks.Task> zaman uyumsuz bir işlem tarafından döndürülen nesne. Bu, yaklaşık tamamlamak için olduğu gibi işlemi oluşturur özel durum gizleme etkisi vardır.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Unutmayın `_` da geçerli bir tanımlayıcı değil. Desteklenen bir bağlam dışında kullanıldığında `_` bir atma olarak değil, ancak geçerli bir değişken olarak kabul edilir. Tanımlayıcı adlı `_` kullanımını kapsamda zaten `_` atma tek başına olarak neden olabilir:

- Kapsam içinde değerini yanlışlıkla değiştirilmesini `_` hedeflenen atma değerini atayarak değişken. Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- Tür güvenliği ihlal eden bir derleyici hatası. Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- Derleyici Hatası CS0136, "Bu adı kapsayan bir yerel kapsamında bir yerel veya parametre tanımlamak için kullanılır çünkü bir yerel veya '_' adlı parametre bu kapsamda bildirilemez." Örneğin:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.
[Tanımlama grupları ve diğer türleri deconstructing](deconstruct.md)   
[`is`anahtar sözcüğü](language-reference/keywords/is.md)   
[`switch`anahtar sözcüğü](language-reference/keywords/switch.md)   
