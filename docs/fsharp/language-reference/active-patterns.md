---
title: Etkin Desenler
description: F# programlama dilinde giriş verilerini alt bölen adlandırılmış bölümleri tanımlamak için etkin desenleri nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187066"
---
# <a name="active-patterns"></a>Etkin Desenler

*Etkin desenler,* giriş verilerini alt bölen adlandırılmış bölümleri tanımlamanızı sağlar, böylece bu adları ayrımcı bir birliktelik için olduğu gibi eşleşen bir ifadede deseni kullanabilirsiniz. Verileri her bölüm için özelleştirilmiş bir şekilde ayrıştırmak için etkin desenler kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *tanımlayıcılar, bağımsız değişkenler*tarafından temsil edilen giriş verilerinin bölümlerinin veya başka bir deyişle, bağımsız değişkenlerin tüm değer kümelerinin alt kümelerinin adlarıdır. Etkin desen tanımında en fazla yedi bölüm olabilir. *İfade,* verileri ayrıştırmak için hangi formu açıklar. Adlandırılmış bölümlerden hangisinin bağımsız değişken olarak verilen değerlerin ait olduğunu belirlemek için kuralları tanımlamak için etkin bir desen tanımı kullanabilirsiniz. (| ve |) *sembolleri muz klipleri* olarak adlandırılır ve bu tür let bağlama tarafından oluşturulan işlev *etkin tanıyıcı*olarak adlandırılır.

Örnek olarak, bir bağımsız değişken ile aşağıdaki etkin desen düşünün.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aşağıdaki örnekte olduğu gibi, etkin deseni desen eşleştirme ifadesinde kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Bu programın çıktısı aşağıdaki gibidir:

```console
7 is odd
11 is odd
32 is even
```

Etkin desenlerin başka bir kullanımı, aynı temel verilerin çeşitli olası gösterimleri olması gibi veri türlerini birden çok şekilde ayrıştırmaktır. Örneğin, bir `Color` nesne RGB gösterimi veya HSB gösterimi olarak ayrıştırılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Yukarıdaki programın çıktısı aşağıdaki gibidir:

```console
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

Birlikte, etkin desenleri kullanmanın bu iki yolu, verileri yalnızca uygun biçimde bölmenize ve ayrıştırmanıza ve uygun veriler üzerinde uygun hesaplamaları hesaplama için en uygun biçimde gerçekleştirmenize olanak tanır.

Ortaya çıkan desen eşleştirme ifadeleri, verilerin çok okunabilir bir şekilde yazılmasını sağlayarak karmaşık olabilecek dallanma ve veri çözümleme kodunu büyük ölçüde basitleştirir.

## <a name="partial-active-patterns"></a>Kısmi Aktif Desenler

Bazen, giriş alanının yalnızca bir kısmını bölmeniz gerekir. Bu durumda, her biri bazı girişler eşleşen ancak diğer girişleri eşleşemeyen kısmi desenler kümesi yazın. Her zaman bir değer üretmeyen *etkin desenlere kısmi etkin desenler*denir; opsiyon türüolan bir iade değerine sahiptirler. Kısmi etkin bir desen tanımlamak için, muz\_kliplerinin içindeki desen listesinin sonunda bir joker karakter ( ) kullanırsınız. Aşağıdaki kod kısmi etkin bir desen kullanımını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Önceki örneğin çıktısı aşağıdaki gibidir:

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Kısmi etkin desenler kullanırken, bazen bireysel seçimler ayrık veya birbirini dışlayan olabilir, ancak gerek yoktur. Aşağıdaki örnekte, bazı sayılar 64 gibi kareler ve küpler olduğundan, desen Kare ve desen Küp ayrı değildir. Aşağıdaki program Kare ve Küp desenleri birleştirmek için AND deseni kullanır. Hem kareler hem de küpler olan 1000'e kadar olan tüm tamsaların yanı sıra yalnızca küp olan tüm tamsayıları yazdırır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
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

## <a name="parameterized-active-patterns"></a>Parametreli Etkin Desenler

Etkin desenler her zaman eşleşen öğe için en az bir bağımsız değişken alır, ancak ek bağımsız değişkenler de alabilir, bu durumda ad *parametreli etkin desen* geçerlidir. Ek bağımsız değişkenler genel bir desen özel leştirilmiş olmasını sağlar. Örneğin, dizeleri ayrıştırmak için normal ifadeler kullanan etkin desenler genellikle önceki kod örneğinde tanımlanan kısmi etkin desen `Integer` kullanan aşağıdaki kodda olduğu gibi, ek bir parametre olarak normal ifadeyi içerir. Bu örnekte, genel ParseRegex etkin deseni özelleştirmek için çeşitli tarih biçimleri için normal ifadeler kullanan dizeleri verilir. Karşıcı etkin desen, eşleşen dizeleri DateTime oluşturucusuna geçirilebilen bir aralığa dönüştürmek için kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Etkin desenler yalnızca desen eşleştirme ifadeleriyle sınırlı değildir, bunları izin bağlamalarında da kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dil Referansı](index.md)
- [Eşleşme İfadeleri](match-expressions.md)
