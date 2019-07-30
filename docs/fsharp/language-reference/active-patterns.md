---
title: Etkin Desenler
description: F# Programlama dilinde giriş verilerini bölümlendirilen adlandırılmış bölümleri tanımlamak için etkin desenleri nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 12f423abe05e649e0b527ed04124b991feb5d592
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629954"
---
# <a name="active-patterns"></a>Etkin Desenler

*Etkin desenler* , bu adları ayrılmış bir birleşim için yaptığınız gibi bir desen eşleştirme ifadesinde kullanabilmeniz için, giriş verilerini bölümlendirilen adlandırılmış bölümler tanımlamanızı sağlar. Her bölüm için özelleştirilmiş bir şekilde verileri ayırmak için etkin desenleri kullanabilirsiniz.

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

Önceki sözdiziminde, tanımlayıcılar *bağımsız değişkenlerle*temsil edilen giriş verilerinin bölümlerinin adlarıdır veya diğer bir deyişle, bağımsız değişkenlerin tüm değerleri kümesinin alt kümelerine yönelik adlar. Etkin bir model tanımında en fazla yedi bölüm olabilir. *İfade* , verilerin parçalara çıkarılması için kullanılacak formu açıklar. Adlandırılmış bölümlerin bağımsız değişken olarak verilen değerlerin hangisinin dahil olduğunu belirlemek için kuralları tanımlamak üzere etkin bir model tanımı kullanabilirsiniz. (| Ve |) sembolleri, *muz klip* olarak adlandırılır ve bu tür Let bağlamasıyla oluşturulan işleve *etkin bir tanıyıcı*denir.

Örnek olarak, aşağıdaki etkin düzene bir bağımsız değişkenle göz önünde bulundurun.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aşağıdaki örnekte olduğu gibi, bir model eşleştirme ifadesinde etkin bir model kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Bu programın çıktısı aşağıdaki gibidir:

```
7 is odd
11 is odd
32 is even
```

Farklı bir etkin model kullanımı, veri türlerini birden çok şekilde oluşturmak, örneğin aynı temeldeki verilerin çeşitli olası temsiller olması olabilir. Örneğin, bir `Color` nesne bir rgb gösterimine veya bir HSB gösterimine parçalanamadı.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Yukarıdaki programın çıktısı aşağıdaki gibidir:

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

Bunun yanında, etkin desenleri kullanmanın bu iki yolu, verileri yalnızca uygun biçimde bölümleyip oluştururın ve uygun hesaplamaları hesaplama için en kullanışlı biçimde gerçekleştirmenizi sağlar.

Sonuç olarak eşleşen desenler, verilerin çok okunaklı, büyük olasılıkla karmaşık dallara ve veri analizi koduna büyük ölçüde basitleşerek kolay bir şekilde yazılmasına olanak tanır.

## <a name="partial-active-patterns"></a>Kısmi etkin desenler

Bazen, giriş alanının yalnızca bir kısmını bölümleyebilirsiniz. Bu durumda, her biri bazı girdilerle eşleşen, ancak diğer girişlerle eşleşmeyecek bir kısmi desenler kümesi yazarsınız. Her zaman bir değer üretmeyen etkin desenler *kısmen etkin desenler*olarak adlandırılır; Bunlar bir seçenek türü olan bir dönüş değerine sahiptir. Kısmi bir etkin düzen tanımlamak için, muz kliplerin içindeki desenler listesinin\_sonunda bir joker karakteri () kullanın. Aşağıdaki kod, kısmen etkin bir düzenin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Önceki örneğin çıktısı aşağıdaki gibidir:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Kısmi etkin desenler kullanılırken, bazen bağımsız seçimler ayrık veya birbirini dışlamalı olabilir, ancak bunların olmaması gerekir. Aşağıdaki örnekte, model karesi ve model küpü ayrık değildir, çünkü bazı sayılar hem kareler hem de küplerdir (örneğin, 64). Aşağıdaki program kare ve küp desenlerini birleştirmek için ve desenini kullanır. Hem kareler hem de küpler olan ve yalnızca küplerden oluşan tüm tamsayıları 1000 'e kadar yazdırır. 

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

## <a name="parameterized-active-patterns"></a>Parametreli etkin desenler

Etkin desenler, eşleşen öğe için her zaman en az bir bağımsız değişken alır, ancak bu durumda, ad *Parametreli etkin düzeni* geçerli olacak şekilde ek bağımsız değişkenler de olabilir. Ek bağımsız değişkenler, genel bir düzenin özelleştireklenmesine izin verir. Örneğin, dizeleri ayrıştırmak için normal ifadeler kullanan etkin desenler, bir önceki kod örneğinde tanımlanan kısmi etkin deseni `Integer` de kullanan aşağıdaki kodda olduğu gibi normal ifadeyi ek bir parametre olarak içerir. Bu örnekte, çeşitli tarih biçimleri için normal ifadeler kullanan dizeler, genel ParseRegex etkin modelini özelleştirmek için verilmiştir. Tamsayı etkin stili, eşleşen dizeleri DateTime oluşturucusuna geçirilebilecek tamsayılara dönüştürmek için kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Etkin desenler yalnızca desen eşleştirme ifadelerine kısıtlanmaz, bunları Let bağlamaları üzerinde de kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Eşleşme İfadeleri](match-expressions.md)
