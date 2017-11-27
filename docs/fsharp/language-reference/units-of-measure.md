---
title: "Ölçü Birimleri (F#)"
description: "Nasıl kayan nokta öğrenin ve F # imzalı tamsayı değerleri, genellikle uzunluğu, ses ve yığın belirtmek için kullanılan ölçü ilişkili."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: cb2eb658-df6c-422e-afad-97422609c773
ms.openlocfilehash: 2d0683e864c5684a78c02e177c296d3067295723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="units-of-measure"></a>Ölçü Birimleri

Kayan nokta ve imzalı tamsayı değerleri F # genellikle toplu vb. uzunluğu, birim, belirtmek için kullanılan ölçü ilişkili sahip. Birimleriyle miktarları kullanarak önlemeye yardımcı olan aritmetik ilişkileri doğru birimleri olduğunu doğrulamak derleyici etkinleştirmek programlama hatalarını.


## <a name="syntax"></a>Sözdizimi

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdizimi tanımlar *birim adı* bir ölçü olarak. İsteğe bağlı bölümü önceden tanımlanmış birimleri açısından yeni bir ölçü tanımlamak için kullanılır. Örneğin, aşağıdaki satırı ölçü tanımlar `cm` (santimetre).

```fsharp
[<Measure>] type cm
```

Aşağıdaki satırı ölçü tanımlar `ml` (milliliter) bir Santimetreküp olarak (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

Önceki sözdiziminde *ölçü* birimleri içerir formülüdür. Formüllerde birimleri içeren, tam sayı powers (pozitif ve negatif) desteklenir, birimleri arasında boşluk gösterir iki birimleri, bir ürün `*` de birimleri, bir ürün gösterir ve `/` birimlerin bir sayının gösterir. Karşılıklı bir birim için negatif tamsayı güç ya da kullanabilirsiniz veya `/` pay ve bir birim formülün payda arasında ayrım gösterir. Payda birden çok birim ayraç içinde kullanılması. Birimleri ayrılmış sonra boşluklarla bir `/` payda, ancak aşağıdaki birimleri parçası olacak şekilde yorumlanır bir `*` pay parçası olacak şekilde yorumlanır.

1 ya da tek başına dimensionless bir miktar belirtmek için birim ifadelerde veya diğer birimler, pay olduğu gibi birlikte kullanabilirsiniz. Örneğin, bir hızı birimi olarak yazılacak `1/s`, burada `s` saniye gösterir. Parantez birim formüller kullanılmaz. Birim formüllerde sayısal dönüşüm sabitleri belirtmeyin; Ancak, dönüştürme sabitleri birimleriyle ayrı olarak tanımlamak ve birim işaretli hesaplamalarında kullanın.

Aynı anlamda birim formüller eşdeğer çeşitli şekillerde yazılabilir. Bu nedenle, derleyici, negatif katlarını reciprocals, grupları birimleri için tek bir pay ve bir paydası dönüştürür ve pay ve payda birimlerinde alfabetik olarak sıralar tutarlı bir form birim formüller dönüştürür.

Örneğin, birim formüller `kg m s^-2` ve `m /s s * kg` her ikisi de dönüştürülür `kg m/s^2`.

Kayan nokta ifadelerinde ölçü kullanın. Ölçü kayan nokta sayıları ilişkili birimler birlikte kullanarak başka bir tür güvenliği düzeyi ekler ve yardımcı formüller zayıf yazılmış kayan noktalı sayının kullandığınızda oluşabilecek birim uyuşmazlığı hataları kaçının. Bir kayan yazarsanız, birimleri kullanan noktası ifade ifade birimlerinde eşleşmesi gerekir.

Aşağıdaki örneklerde gösterildiği gibi köşeli, birim formülde ile değişmez değerleri açıklama ekleyebilirsiniz.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Sayı ve açılı ayraç arasında bir boşluk koymayın; Ancak, değişmez değer soneki gibi içerebilir `f`, aşağıdaki örnekte olduğu gibi.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Böyle bir ek açıklama değişmez değeri türünü ilkel türünden değiştirir (gibi `float`) dimensioned türü gibi `float<cm>` veya bu durumda, `float<miles/hour>`. Bir birim bir ek açıklamanın `<1>` dimensionless bir miktar ve türünü ilkel tür bir birim parametresi olmadan eşdeğer olduğunu gösterir.

Bir ölçü türü bir kayan nokta veya köşeli gösterilen ek birim açıklamanın birlikte tam sayı türdür. Bu nedenle, ne zaman yazdığınız dönüştürme türü `g` (gram) için `kg` (kilogram), aşağıdaki gibi türleri açıklanmaktadır.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Ölçü için derleme zamanı birimi denetimi kullanılır ancak çalışma zamanı ortamında kalıcı değildir. Bu nedenle, performans etkilemez.

Ölçü birimleri yalnızca kayan nokta türleri, herhangi bir türüne uygulanabilir; Ancak, tek kayan nokta türleri, tam sayı türleri ve ondalık türleri dimensioned destek miktarları imzalanmış. Bu nedenle, yalnızca ilkel türler ve bu ilkel türler içeren toplamalar ölçü kullanılacak mantıklıdır.

Aşağıdaki örnek ölçü kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
Aşağıdaki kod örneğinde dimensionless kayan nokta sayısı dimensioned bir kayan noktalı değeri dönüştürme gösterilmektedir. Yalnızca tarafından 1.0, 1.0 boyutları uygulama çarpın. Bu gibi bir işlevine soyut `degreesFahrenheit`.

Ayrıca, dimensionless kayan noktalı sayının beklediğiniz işlevleri dimensioned değerlerini geçirdiğinizde, birimleri iptal etmeli veya için cast `float` kullanarak `float` işleci. Bu örnekte, bölün `1.0<degC>` bağımsız değişkenleri için `printf` çünkü `printf` dimensionless miktarları bekliyor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Aşağıdaki örnek oturumunda bu kodu girişleri ve çıkışları gelen gösterir.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Genel birimlerini kullanma
İlişkili bir ölçü olan veriler üzerinde çalışan genel işlevler yazabilirsiniz. Tür parametresi bir tür genel bir birim birlikte belirterek aşağıdaki kod örneğinde gösterildiği gibi bunu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a>Genel birimleriyle toplama türleri oluşturma
Aşağıdaki kod genel birimleri olan tek tek kayan nokta değerlerine oluşan bir toplama türü oluşturulacağını gösterir. Bu birimleri çeşitli çalışan oluşturulması tek bir türü sağlar. Ayrıca, bir grup birimlerinin genel bir tür aynı genel tür birimleri farklı bir dizi farklı bir tür olduğu sağlayarak tür güvenliği genel birimleri korur. Bu teknik temelini `Measure` özniteliği için tür parametre uygulanabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a>Çalışma zamanında birimleri
Ölçü birimleri statik türü denetlemek için kullanılır. Kayan nokta değerlerine derlendiğinde çalışma zamanında birimleri kayıp; bu nedenle ölçü, ortadan kalkar. Bu nedenle, çalışma zamanında birimleri denetimini bağlıdır işlevselliği uygulamak için her türlü girişim mümkün değildir. Örneğin, uygulama bir `ToString` birimleri yazdırmak için işlevi mümkün değildir.


## <a name="conversions"></a>Dönüşümler
Birimleri olan bir türü dönüştürmek için (örneğin, `float<'u>`) birimleri sahip olmayan bir türe standart dönüştürme işlevini kullanabilirsiniz. Örneğin, kullanabileceğiniz `float` dönüştürmek için bir `float` birimleri, aşağıdaki kodda gösterildiği gibi yok değeri.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Bir unitless değeri birimleri olan değerine dönüştürmek için uygun birimleriyle açıklama 1 veya 1.0 değeri tarafından çarpabilirsiniz. Ancak, birlikte çalışabilirlik Katmanlar yazmak için de bazı explicit unitless değerleri birimleriyle değerlerine dönüştürmek için kullanabileceğiniz işlev vardır. İçinde bunlar [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modülü. Örneğin, bir unitless dönüştürmek için `float` için bir `float<cm>`, kullanın [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)aşağıdaki kodda gösterildiği gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a>F # güç paketindeki ölçü birimleri
F # PowerPack'ten kullanılabilir bir birim kitaplıktır. Birim kitaplığı sı birimleri ve fiziksel sabitleri içerir.


## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)
