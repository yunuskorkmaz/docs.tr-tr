---
title: Ölçü Birimleri
description: 'F # içindeki kayan nokta ve işaretli tamsayı değerlerinin, genellikle uzunluğu, hacmi ve kütle belirtmek için kullanılan, ilişkili ölçü birimlerine sahip olabileceğini öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 0262f89e80697dd86161c93fe37381122972b56f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811580"
---
# <a name="units-of-measure"></a>Ölçü Birimleri

F # ' de kayan nokta ve işaretli tamsayı değerleri, genellikle uzunluğu, hacmi, kütle, vb. belirtmek için kullanılan ilişkili ölçü birimlerine sahip olabilir. Birimleri olan miktarları kullanarak, aritmetik ilişkilerin doğru birimlere sahip olduğunu doğrulamak için derleyicinin, programlama hatalarının önlenmesine yardımcı olan doğru birimlere sahip olduğunu doğrulaması için etkinleştirin.

## <a name="syntax"></a>Syntax

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdizimi *birim adını* ölçü birimi olarak tanımlar. İsteğe bağlı bölüm, önceden tanımlanmış birimler açısından yeni bir ölçü tanımlamak için kullanılır. Örneğin, aşağıdaki satır ölçüyü `cm` (santimeter) tanımlar.

```fsharp
[<Measure>] type cm
```

Aşağıdaki satır, ölçüyü `ml` (milliliter) santimetrede () olarak tanımlar `cm^3` .

```fsharp
[<Measure>] type ml = cm^3
```

Önceki sözdiziminde, *Ölçü* birimleri içeren bir formüldür. Birimleri içeren formüllerde, tam sayı güçleri desteklenir (pozitif ve negatif), birimler arasındaki boşluklar iki birimin bir ürününü belirtir, `*` Ayrıca bir birim ürünü gösterir ve `/` birim bölümünü gösterir. Ters bir birim için, bir `/` birim formülünün pay ve paydası arasındaki ayrımı belirten negatif bir tamsayı gücü veya bir kullanabilirsiniz. Paydadaki birden çok birim parantezle çevrelenmelidir. Bir `/` değeri paydaya bir parçası olarak yorumlandıktan sonra boşluklara göre ayrılmış birimler, ancak bir sonraki birimler, `*` payın bir parçası olarak yorumlanır.

Birim ifadelerinde 1 ' i, bir boyutsuz miktarı belirtmek için tek başına ya da pay içindeki gibi diğer birimlerle birlikte kullanabilirsiniz. Örneğin, bir hız için birimler olarak yazılır; `1/s` burada `s` saniyeler belirtilir. Parantezler, birim formüllerinde kullanılmaz. Birim formüllerinde sayısal dönüştürme sabitleri belirtmeyin; Ancak, birimlere ayrı olarak dönüştürme sabitleri tanımlayabilir ve bunları birim denetimli hesaplamalar halinde kullanabilirsiniz.

Aynı şeyi gösteren birim formülleri, çeşitli eşdeğer yollarla yazılabilir. Bu nedenle, derleyici birim formüllerini, negatif üsleri devrik bir biçimde, gruplar birimlerini tek bir pay ve paydaya dönüştürür ve pay ve paydadaki birimleri alfabetik hale getirir.

Örneğin, birim formülleri `kg m s^-2` ve `m /s s * kg` her ikisi de olarak dönüştürülür `kg m/s^2` .

Kayan nokta ifadelerinde ölçü birimleri kullanırsınız. İlişkili ölçü birimleriyle birlikte kayan noktalı sayıların kullanılması, başka bir tür güvenliği düzeyi ekler ve zayıf yazılmış kayan noktalı sayılar kullandığınızda formüllerde oluşabilecek birim uyumsuzluğu hatalarından kaçınmaya yardımcı olur. Birimleri kullanan bir kayan nokta ifadesi yazarsanız, ifadedeki birimlerin eşleşmesi gerekir.

Aşağıdaki örneklerde gösterildiği gibi, bir birim formülüyle, açılı ayraç içinde sabit değerlere açıklama ekleyebilirsiniz.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Sayı ve açılı ayraç arasına bir boşluk koymayın; Ancak, `f` Aşağıdaki örnekte olduğu gibi, gibi bir sabit sonek dahil edebilirsiniz.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Böyle bir ek açıklama, değişmez değer türünü (gibi) temel türünden `float` veya gibi bir boyut türüne (örneğin,) değiştirir `float<cm>` `float<miles/hour>` . Bir birim ek açıklaması `<1>` , bir boyutsuz miktarı gösterir ve türü bir birim parametresi olmadan temel tür ile eşdeğerdir.

Bir ölçü biriminin türü, parantez içinde belirtilen ek birim ek açıklaması ile birlikte bir kayan nokta veya imzalı integral türüdür. Bu nedenle, (gram) ' den `g` (kilogram) dönüştürme türünü yazdığınızda `kg` , türleri aşağıdaki şekilde tanımlayabilirsiniz.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Ölçü birimleri derleme zamanı birim denetlemesi için kullanılır, ancak çalışma zamanı ortamında kalıcı değildir. Bu nedenle, performansı etkilemezler.

Ölçü birimleri yalnızca kayan nokta türleri değil herhangi bir türe uygulanabilir; Ancak, yalnızca kayan nokta türleri, işaretli integral türleri ve ondalık türler boyutlanır miktarları destekler. Bu nedenle, yalnızca temel türler ve bu ilkel türleri içeren toplamalarda ölçü birimleri kullanmak mantıklı olur.

Aşağıdaki örnek ölçü birimlerinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

Aşağıdaki kod örneği, bir boyutsuz kayan nokta numarasından bir boyutlandırma kayan nokta değerine nasıl dönüştürüleceğini gösterir. 1,0 ile çarpıp, boyutları 1,0 ' ye uygulayarak yapmanız yeterlidir. Bunu, gibi bir işlev içinde soyut hale getirebilirsiniz `degreesFahrenheit` .

Ayrıca, boyutlandırma değerlerini boyutsuz kayan noktalı sayılar bekleyen işlevlere geçirdiğinizde birimi iptal etmeniz veya `float` işlecini kullanarak atamalısınız `float` . Bu örnekte, için ' a `1.0<degC>` kadar olan bağımsız değişkenler, `printf` boyutsuz miktarlar gerektirdiğinden öğesine göre bölmektir `printf` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Aşağıdaki örnek oturum, bu koda ait çıkış ve giriş gösterir.

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Genel birimleri kullanma

İlişkili ölçü birimi olan veriler üzerinde çalışan genel işlevler yazabilirsiniz. Bunu, aşağıdaki kod örneğinde gösterildiği gibi, bir türü bir genel birimle birlikte bir tür parametresi olarak belirterek yapabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Genel birimlerle toplama türleri oluşturma

Aşağıdaki kod, genel birimlere sahip bağımsız kayan nokta değerlerinden oluşan bir toplam türün nasıl oluşturulacağını gösterir. Bu, çeşitli birimlerle birlikte çalışarak tek bir türün oluşturulmasını sağlar. Ayrıca, genel birimler, tek bir birim kümesine sahip genel bir türün farklı bir birim kümesiyle aynı genel türden farklı türde olmasını sağlayarak tür güvenliğini korur. Bu tekniğin temeli `Measure` özniteliğin tür parametresine uygulanabilirler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Çalışma zamanında birimler

Ölçü birimleri statik tür denetlemesi için kullanılır. Kayan nokta değerleri derlendiğinde, ölçü birimleri ortadan kaldırılır, bu nedenle birimler çalışma zamanında kaybedilir. Bu nedenle, çalışma zamanında birimleri denetlemeye bağlı olan işlevleri uygulama girişimi mümkün değildir. Örneğin, `ToString` birimleri yazdırmak için bir işlev uygulamak mümkün değildir.

## <a name="conversions"></a>Dönüşümler

Birimleri olan bir türü (örneğin, `float<'u>` ) birimi olmayan bir türe dönüştürmek için Standart dönüştürme işlevini kullanabilirsiniz. Örneğin, `float` `float` aşağıdaki kodda gösterildiği gibi, birimi olmayan bir değere dönüştürmek için kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Bir unitless değerini birimlere sahip bir değere dönüştürmek için, uygun birimlerle açıklanmış bir 1 veya 1,0 değeri ile çarpmanız gerekir. Bununla birlikte, birlikte çalışabilirlik katmanları yazmak için, birimsiz değerleri birimlere eşit değerlere dönüştürmek üzere kullanabileceğiniz bazı açık işlevler de vardır. Bunlar [FSharp. Core. LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) modülüdür. Örneğin, bir unitküçüktür öğesine dönüştürmek için `float` `float<cm>` aşağıdaki kodda gösterildiği gibi [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure)kullanın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>F # Çekirdek kitaplığındaki ölçü birimleri

Ad alanında bir birim kitaplığı mevcuttur `FSharp.Data.UnitSystems.SI` . Alt ad alanında hem sembol biçiminde (ölçüm gibi) hem de alt ad alanındaki `m` `UnitSymbols` tam adı ( `meter` ölçüm IÇIN) olan sı birimleri içerir `UnitNames` .

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
