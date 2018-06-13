---
title: Etkin Desenler (F#)
description: 'Etkin desenler F # programlama dili giriş verisi ayırabilir adlandırılmış bölümleri tanımlamak için nasıl kullanılacağını öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: b8c3270b1efbeb3495ac69bf1217fddf8a5a73e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564452"
---
# <a name="active-patterns"></a>Etkin Desenler

*Etkin desenler* , bu adları için ayrılmış bir birleşim gibi ifadeyle eşleşen bir düzende kullanabilmesi için giriş verileri ayırabilir adlandırılmış bölümleri tanımlamayı sağlar. Etkin desenler her bölüm için özelleştirilmiş bir şekilde veri parçalayın için kullanabilirsiniz.


## <a name="syntax"></a>Sözdizimi

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde tarafından temsil edilen giriş verileri bölümlerini adlarını tanımlayıcılardır *bağımsız değişkenleri*, veya, diğer bir deyişle, değişkenlerin tüm değerleri kümesi kümelerine adları. Bir etkin desen tanımında en çok yedi bölüm olabilir. *İfade* olduğu veri parçalayın forma açıklar. Adlandırılmış bölüm hangisinin ait bağımsız değişkenler olarak verilen değerleri belirlemek için kurallar tanımlamak için bir etkin desen tanımı kullanabilirsiniz. (| Ve |) simgeleri denir *Muz klipleri* ve bu tür let bağlama tarafından oluşturulan işlev çağrılır bir *etkin tanıyıcı*.

Örnek olarak, bağımsız değişkeni aşağıdaki etkin desen göz önünde bulundurun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aşağıdaki örnekte olduğu gibi ifade ile eşleşen bir deseni etkin desen kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Bu programın çıkışı aşağıdaki gibidir:

```
7 is odd
11 is odd
32 is even
```

Başka bir Etkin desenler veri türleri aynı temel alınan verilerin çeşitli olası sunularını olduğunda gibi birden çok yolla parçalayın için kullanılır. Örneğin, bir `Color` nesne ayrılmış bir RGB temsili veya HSB gösterimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Yukarıdaki programın çıkışı aşağıdaki gibidir:

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

Birlikte, Etkin desenler kullanarak bu iki yolu bölüme etkinleştirin ve yalnızca uygun forma veri parçalayın ve hesaplama için en uygun biçimde uygun veri uygun hesaplamalar gerçekleştirin.

Sonuçta elde edilen desen eşleştirme ifadeleri çok okunabilir, büyük ölçüde basitleştirme potansiyel olarak karmaşık dallanma ve veri analizi kodu uygun şekilde yazılacak veriler etkinleştirin.


## <a name="partial-active-patterns"></a>Kısmi Etkin desenler
Bazı durumlarda, yalnızca giriş alanı parçası bölüm gerekir. Bu durumda, kısmi desenleri de, bazı girişler eşleşen ancak diğer girişleri eşleşecek şekilde başarısız yazma. Her zaman bir değer üretmez Etkin desenler çağrılır *kısmi Etkin desenler*; bir seçenek türü bir dönüş değerine sahip. Kısmi bir etkin düzeni tanımlamak için Muz klipleri içinde desenleri listesi sonunda joker karakteri (_) kullanın. Aşağıdaki kod, kısmi bir etkin desen kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Önceki örnekte çıktısı şu şekildedir:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Kısmi Etkin desenler kullanırken, bazen tek tek seçimler ayrık veya birbirini dışlayan olabilir, ancak bunlar olmaması. Kare ve küpleri 64 gibi bazı numaralarıdır aşağıdaki örnekte, düzeni kare ve küp düzeni ayrık, değildir. Aşağıdaki programı tüm tamsayılar kadar kareler ve küpleri 1000000 yazdırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Çıktı aşağıdaki gibidir:

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a>Parametreli Etkin desenler
Etkin desenler her zaman en az bir değişken eşleşen öğe için etkinleştirilir, ancak adı durumda ek bağımsız değişkenler de sürebilir *parametreli etkin desen* uygular. Ek bağımsız değişkenler özelleştirilmesi için genel bir desen sağlar. Örneğin, normal ifade de kısmi etkin desen kullanan aşağıdaki kod, olduğu gibi ek bir parametre olarak dizeler genellikle ayrıştırmak için normal ifadeleri kullanma Etkin desenler dahil `Integer` önceki kod örneğinde tanımlanan. Bu örnekte, genel ParseRegex etkin desen özelleştirmek için çeşitli tarih biçimleri için normal ifadeler kullanan dizeleri verilir. Tamsayı etkin desen DateTime oluşturucuya geçirilen tamsayılar eşleşen dizeleri dönüştürmek için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Önceki kod çıkışı aşağıdaki gibidir:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Etkin desenler yalnızca eşleşen ifadeleri desen sınırlı değildir, ayrıca bunları let bağlamaları üzerinde kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Önceki kod çıkışı aşağıdaki gibidir:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Eşleşme İfadeleri](match-expressions.md)

