---
title: Etkin Desenler
description: Etkin desenler girdi verileri alt bölümlere adlandırılmış bölümler tanımlamak için kullanmayı öğrenin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: 0f1f57de425836738201d2d8f84ab67a0df142ee
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412090"
---
# <a name="active-patterns"></a>Etkin Desenler

*Etkin desenler* , bir desen eşleme ifadesinde için ayrılmış bir birleşim olduğu gibi bu adlar kullanabilirsiniz, böylece giriş verileri alt bölümlere adlandırılmış bölümler tanımlamanıza olanak sağlar. Etkin desenler, her bölüm için özelleştirilmiş bir şekilde veri ayırmak için kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, bölümler tarafından temsil edilen giriş verileri için adları tanımlayıcılardır *bağımsız değişkenleri*, veya başka bir deyişle, bağımsız değişkenlerin tüm değerleri kümesi kümelerine adları. Bir etkin düzeni tanımında en fazla yedi bölüm olabilir. *İfade* , verileri ayırmak forma açıklar. Etkin desen tanımı, adlandırılmış bölüm ait bağımsız değişkenler olarak verilen değerlerden belirleyen kuralları tanımlamak için kullanabilirsiniz. (| Ve |) sembolleri denir *Muz klipleri* ve bu tür bir let bağlama tarafından oluşturulan işlev çağrılırsa bir *etkin tanıyıcı*.

Örneğin, bir bağımsız değişken ile aşağıdaki etkin düzeni göz önünde bulundurun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Etkin desen bir desen eşleme ifadesinde, aşağıdaki örnekte olduğu gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Bu program çıktısı aşağıdaki gibidir:

```
7 is odd
11 is odd
32 is even
```

Başka bir Etkin desenler veri türleri aynı temel alınan verilerin çeşitli olası gösterimleri olduğunda gibi birden çok yolla ayırmak için kullanılır. Örneğin, bir `Color` nesne ayrılmış bir RGB temsili ya da bir HSB temsili.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Yukarıdaki program çıktısı aşağıdaki gibidir:

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

Birlikte, Etkin desenler kullanarak bu iki yolu bölüme etkinleştirin ve yalnızca uygun biçime verileri parçalayın ve hesaplama için en uygun biçimde uygun veri uygun hesaplamalar gerçekleştirin.

Sonuçta elde edilen desen eşleştirme ifadeleri çok okunabilir, büyük ölçüde basitleştirme bulunabilecek karmaşık dallanma ve veri analizi kodu uygun şekilde yazılacak veriler etkinleştirin.

## <a name="partial-active-patterns"></a>Kısmi Etkin desenler

Bazen, giriş alanı yalnızca bir kısmını bölümlemek gerekir. Bu durumda, kısmi desenleri, bazı girişler eşleşen ancak diğer girişler eşleştirilecek başarısız yazın. Her zaman bir değer üretmez Etkin desenler çağrılır *kısmi Etkin desenler*; bunlar seçeneği türünde bir dönüş değerine sahip. Kısmi bir etkin düzeni tanımlamak için bir joker karakter kullanın. (\_) Muz klipleri içinde Desen listesinin sonunda. Aşağıdaki kodu kısmi bir etkin desen kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Önceki örnek çıktısı aşağıdaki gibidir:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Kısmi Etkin desenler kullanırken bazen tek tek seçimler ayrık veya birbirini dışlayan olabilir, ancak bunlar olmaması. Bazı sayılar kareler hem 64 gibi küpler olduğundan aşağıdaki örnekte, deseni kare ve küp deseni ayrık, değildir. Aşağıdaki program, kare ve küp desenleri birleştirmek ve deseni kullanır. Yazdırabilirsiniz hem kareler ve küpleri, hem de hangi yalnızca küpleri olan 1000'e kadar tüm tamsayıları. 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>Parametreli Etkin desenler

Etkin desenler, eşleştirilen öğesi için en az bir bağımsız değişkeni her zaman alır ancak adı bu durumda da, ek bağımsız değişken alabilir *parametreli etkin desen* uygular. Ek bağımsız değişkenler özelleştirilmesi için genel bir desen sağlar. Örneğin, normal ifade ayrıca kısmi etkin deseni kullanan aşağıdaki kod, olduğu gibi ek bir parametre olarak dizeler genellikle ayrıştırmak için normal ifadeleri kullanma Etkin desenler dahil `Integer` önceki kod örneğinde tanımlanan. Bu örnekte, çeşitli tarih biçimleri için normal ifadeleri kullanma dizeleri genel ParseRegex etkin düzeni özelleştirildiği verilir. Tamsayı etkin deseni, eşleşen dizeleri DateTime oluşturucuya geçirilen tamsayı dönüştürmek için kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Etkin desenler yalnızca eşleşen bir ifade deseni için sınırlı değildir, ayrıca bunları let bağlamaları üzerinde kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Eşleşme İfadeleri](match-expressions.md)
