---
title: Ölçü Birimleri (F#)
description: Nasıl kayan nokta öğrenin ve F# imzalı tamsayı değerleri, genellikle uzunluğu, ses ve yığın belirtmek için kullanılan ölçü birimlerini ilişkili.
ms.date: 05/16/2016
ms.openlocfilehash: ad2193e25f3c0cee6e73cd529ab43d1e4b6b549b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45972523"
---
# <a name="units-of-measure"></a>Ölçü Birimleri

Kayan nokta ve imzalı tamsayı değerleri F# genellikle toplu vb. uzunluğu, birim belirtmek için kullanılan ölçü birimlerini ilişkili. Birimleri ile miktarlar kullanarak önlemeye yardımcı olur aritmetik ilişkileri doğru birimleri, yüklü olduğunu doğrulamak derleyiciyi etkinleştir programlama hatalarını.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Açıklamalar

Önceki söz dizimi *birim adı* ölçü birimi olarak. İsteğe bağlı bir parçası, önceden tanımlanmış birimleri yeni bir ölçü tanımlamak için kullanılır. Örneğin, aşağıdaki satırı ölçü tanımlar `cm` (santimetre).

```fsharp
[<Measure>] type cm
```

Aşağıdaki satırı ölçü tanımlar `ml` (milliliter) üçüncü dereceden santimetre olarak (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

Önceki sözdiziminde, *ölçü* birim içeren bir formül. Birim içeren formüllerde, tam sayı katlarını (pozitif ve negatif) desteklenir; birimleri arasında boşluk iki birimleri, bir ürünü belirtmek `*` de birimleri, bir ürün gösterir ve `/` birimlerinin bir bölümü gösterir. Karşılıklı bir birim için bir negatif tam sayı üssü ya da kullanabilirsiniz veya `/` payı ve bir birim formülün paydayı arasında bir ayrım gösterir. Payda içinde birden çok birimi parantez içine alınır. Sonraki boşluklar ayrılmış birim bir `/` payda, ancak izleyen tüm birimleri bir parçası olacak şekilde yorumlanır bir `*` pay parçası olacak şekilde yorumlanır.

1 birim ifadelerde ya da tek başına bir dimensionless miktar belirtmek için veya diğer birimleri, gibi pay birlikte kullanabilirsiniz. Örneğin, bir oran için birim olarak yazılacak `1/s`burada `s` saniye gösterir. Parantez birim formüllerde kullanılmaz. Birim formüllerde sayısal dönüştürme sabitleri belirtmeyin; Ancak, dönüşümü sabitleri birimleri ile ayrı olarak tanımlayın ve bunları birim işaretli hesaplamalar kullanın.

Aynı anlamda birim formülleri eşdeğer çeşitli şekillerde yazılabilir. Bu nedenle, derleyici negatif powers reciprocals, grupları birimleri için tek bir pay ve bir paydası dönüştürür ve birimleri pay ve paydası alfabetik olarak sıralar tutarlı bir form birim formülleri dönüştürür.

Örneğin, birim formülleri `kg m s^-2` ve `m /s s * kg` hem dönüştürülür `kg m/s^2`.

Kayan nokta ifadeleri ölçü kullanırsınız. Ölçü kayan noktalı sayıları ilişkili birimleri ile birlikte kullanarak başka bir tür güvenliği düzeyini ekler ve yardımcı formüllerde zayıf yazılmış kayan noktalı sayıları kullanırken oluşabilecek birim uyuşmazlığı hataları önleyebilirsiniz. Kayan yazarsanız birimleri kullanan noktası ifadesi ifade birimleriyle aynı olmalıdır.

Aşağıdaki örneklerde gösterildiği gibi bir birim formül köşeli parantez içinde sabit değerleri açıklama ekleyebilirsiniz.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Açılı ayraç arasındaki boşluk koymayın; Ancak, değişmez değer soneki gibi içerebilir `f`, aşağıdaki örnekte olduğu gibi.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Böyle bir ek açıklama değişmez değer türü kendi temel türünden değiştirir (gibi `float`) dimensioned bir türe gibi `float<cm>` veya bu durumda, `float<miles/hour>`. Bir birim ek açıklamanın `<1>` dimensionless miktarını ve türünü ilkel tür bir birim parametresi olmadan eşdeğer olduğunu gösterir.

Ölçü türü bir kayan nokta veya imzalı tamsayı türü köşeli ayraç içinde gösterilen birim ek açıklamanın birlikte. Bu nedenle, bir dönüştürme türü yazdığınızda `g` (gram) için `kg` (kilogram) aşağıdaki gibi türleri açıklanmaktadır.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Ölçü birimleri için derleme zamanı birimi denetimi kullanılır ancak çalışma zamanı ortamında kalıcı değildir. Bu nedenle, performans etkilemez.

Ölçü birimleri, yalnızca kayan nokta tür herhangi bir tür uygulanabilir; Ancak, yalnızca kayan nokta türleri, tam sayı türleri ve ondalık türleri dimensioned destek miktarlar imzalanmış. Bu nedenle, yalnızca temel eleman türleri ve bu ilkel türler içeren toplamaları ölçü kullanılacak mantıklıdır.

Aşağıdaki örnek, ölçü kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

Aşağıdaki kod örneği, dimensionless kayan noktası numarasından dimensioned kayan nokta değerine dönüştürmek gösterilmektedir. Yalnızca tarafından 1.0, 1.0 boyutları uygulama çarpın. Bu gibi bir işlev uygulamasına soyutlamak `degreesFahrenheit`.

Ayrıca, dimensioned değerlerini dimensionless kayan noktalı sayıları beklediğiniz bir işleve geçirdiğinizde, birimi iptal etmeli veya başvurusuna `float` kullanarak `float` işleci. Bu örnekte, bölen `1.0<degC>` bağımsız değişkenleri için `printf` çünkü `printf` dimensionless miktarlar bekliyor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Aşağıdaki örnekte oturum bu kodu girişleri ve çıkışları gösterir.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Genel birimler

İlişkili bir ölçü olan veriler üzerinde çalışan genel işlevler yazabilirsiniz. Bir tür parametresi bir türle birlikte genel bir birim belirterek aşağıdaki kod örneğinde gösterildiği gibi yaparsınız.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Toplama türlerini genel birimleri ile oluşturma

Aşağıdaki kod genel birimler sahip tek kayan nokta değerleri oluşan bir toplama türünü oluşturma işlemini gösterir. Bu, çeşitli birimleri ile birlikte çalışan oluşturulacak tek bir türü sağlar. Ayrıca, genel birimleri tür güvenliği birimleri bir dizi olan bir genel tür birimleri farklı bir dizi ile aynı genel tür farklı bir tür olduğundan emin olarak korur. Bu teknik temelini `Measure` özniteliği tür parametresi için uygulanabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Çalışma zamanında birimleri

Ölçü birimleri statik tür denetlemek için kullanılır. Kayan nokta değerleri derlendiğinde çalışma zamanında birimleri kayıp olacak şekilde ölçü, ortadan kalkar. Bu nedenle, her türlü girişim çalışma zamanında birim denetimini bağlıdır işlevselliği uygulamak için mümkün değildir. Örneğin, uygulama bir `ToString` işlevi birimi yazdırmak için mümkün değildir.

## <a name="conversions"></a>Dönüşümler

Birimleri olan bir türü dönüştürmek için (örneğin, `float<'u>`) birimleri sahip olmayan bir türe standart dönüştürme işlevini kullanabilirsiniz. Örneğin, kullanabileceğiniz `float` dönüştürmek için bir `float` birimleri, aşağıdaki kodda gösterildiği gibi yok değeri.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Unitless değeri birimleri olan bir değere dönüştürülecek uygun birimleri ile açıklanıyor 1 veya 1.0 değere göre çarpabilirsiniz. Ancak, birlikte çalışabilirlik katmanları yazmak için de bazı açık unitless değerleri birimleriyle değerlerine dönüştürmek için kullanabileceğiniz işlevi vardır. İçinde bunlar [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modülü. Örneğin, unitless dönüştürmek için `float` için bir `float<cm>`, kullanın [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)aşağıdaki kodda gösterildiği gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>F# çekirdek Kitaplığı'nda ölçü birimleri

Bir birim kitaplığı kullanılabilir `FSharp.Data.UnitSystems.SI` ad alanı. Bunların her iki simge biçiminde sı birimleri içerir (gibi `m` ölçüm için) içinde `UnitSymbols` alt ad alanı ve bunların tam adı (gibi `meter` ölçüm için) içinde `UnitNames` alt ad.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
