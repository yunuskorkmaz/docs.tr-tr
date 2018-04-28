---
title: Atama ve Dönüştürmeler (F#)
description: 'Nasıl F # programlama dili dönüşüm işleçleri çeşitli ilkel türler arasında aritmetik dönüşümler için sağladığını öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 410c7da2b7ae8a09c58e8c89b24d0093a7f33a5c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="casting-and-conversions-f"></a>Atama ve Dönüştürmeler (F#)

Bu konu, F # tür dönüştürmeleri için destek açıklanır.

## <a name="arithmetic-types"></a>Aritmetik türleri
F # dönüşüm işleçleri için çeşitli ilkel türler arasında aritmetik dönüşümler gibi tamsayı ve kayan nokta türleri arasında sağlar. İntegral ve karakter dönüştürme işleçleri denetlediyseniz ve Denetlenmeyen forms; kayan nokta işleçler ve `enum` dönüşüm işleci yapın. Unchecked forms tanımlanan `Microsoft.FSharp.Core.Operators` ve denetlenen forms tanımlanan `Microsoft.FSharp.Core.Operators.Checked`. Checked forms taşma durumunu denetleyin ve hedef türü sınırları sonuç değeri aşarsa, bir çalışma zamanı özel durumu oluşturur.

Her bu işleçlerinin hedef türünün adı ile aynı ada sahip. Hangi türleri açıkça açıklama, örneğin, aşağıdaki kodda, `byte` ile iki farklı anlamları görüntülenir. Birinci türü ve ikinci dönüştürme işleci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

Aşağıdaki tabloda, F #'de tanımlanan dönüştürme işleçleri gösterir.

|İşleç|Açıklama|
|--------|-----------|
|`byte`|Bir 8 bit işaretsiz tür bayta dönüştürün.|
|`sbyte`|İmzalı bayta dönüştürün.|
|`int16`|Bir 16 bit işaretli tamsayıyı dönüştürün.|
|`uint16`|Bir 16 bit işaretsiz tamsayıya dönüştürür.|
|`int32, int`|Bir 32 bit işaretli tamsayıyı dönüştürün.|
|`uint32`|32-bit işaretsiz tamsayıya dönüştürür.|
|`int64`|Bir 64-bit işaretli tamsayıyı dönüştürün.|
|`uint64`|Bir 64-bit işaretsiz tamsayıya dönüştürür.|
|`nativeint`|Yerel bir tamsayıya dönüştürür.|
|`unativeint`|İmzasız yerel tamsayıya dönüştürür.|
|`float, double`|Bir 64-bit çift duyarlıklı IEEE kayan noktalı sayıyı dönüştürün.|
|`float32, single`|Bir 32-bit tek duyarlıklı IEEE kayan noktalı sayıyı dönüştürün.|
|`decimal`|Dönüştür `System.Decimal`.|
|`char`|Dönüştür `System.Char`, Unicode karakter.|
|`enum`|Bir numaralandırılmış türüne dönüştürün.|
Ek olarak yerleşik ilkel türler, uygulama türleri ile bu işleçleri kullanabilirsiniz `op_Explicit` veya `op_Implicit` uygun imzaları yöntemleriyle. Örneğin, `int` dönüştürme işleci çalışır bir statik yöntem sağlar herhangi bir türü `op_Explicit` , türünü bir parametre olarak alıp döndüren `int`. Yöntemleri tarafından dönüş türü aşırı genel kural için bir özel durum bunu yapabilmeniz `op_Explicit` ve `op_Implicit`.

## <a name="enumerated-types"></a>Numaralandırılmış türler
`enum` İşlecidir türünü temsil eden bir tür parametre alan genel bir işleç `enum` dönüştürmek için. Numaralandırılmış bir türe dönüştürür, çıkarım türünü belirleme girişimleri yazın `enum` dönüştürmek istediğiniz. Aşağıdaki örnekte, değişken `col1` açıkça açıklama değil, ancak türü sonraki eşitlik testten algılanır. Bu nedenle, derleyici için dönüştürüyorsunuz türetme bir `Color` numaralandırması. Alternatif olarak, bir tür ek açıklama sağlayabilir olduğu gibi `col2` aşağıdaki örnekte.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
Ayrıca hedef numaralandırma türü açıkça aşağıdaki kodu olduğu gibi bir tür parametresi olarak belirtebilirsiniz:

```fsharp
let col3 = enum<Color> 3
```

Yalnızca sabit temel alınan türü dönüştürülmekte olan türü ile uyumlu ise numaralandırması iş çevirir unutmayın. Aşağıdaki kodda arasındaki uyumsuzluk nedeniyle derlemek dönüştürme başarısız `int32` ve `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Daha fazla bilgi için bkz: [numaralandırmalar](enumerations.md).

## <a name="casting-object-types"></a>Nesne türlerini dönüştürmeyi
Bir nesne hiyerarşideki türleri arasında dönüştürme nesne odaklı programlama için temel önemdedir. İki temel tür dönüşümleri vardır: (üst türe çevirme) atama ve (alt türe çevirme) atama. Bir hiyerarşi atama temel nesne başvurusu için bir türetilen nesne başvurusundan atama anlamına gelir. Bu tür bir cast türetilmiş sınıf devralma hiyerarşisini temel sınıftır sürece çalışmak için sağlanır. Yalnızca nesne örneği (türetilmiş) doğru hedef türü veya hedef türden türetilmiş bir tür gerçekte ise bir hiyerarşiden bir türetilen nesne başvurusu bir temel nesne başvurusu aşağı atama başarılı olur.

F # işleçleri bu tür dönüştürmeleri için sağlar. `:>` İşleci çevirir hiyerarşisinde yukarı ve `:?>` işleci hiyerarşide aşağıda çevirir.

### <a name="upcasting"></a>Üst türe çevirme
Birçok nesne yönelimli dilde üst türe çevirme örtük; F #'ta kuralları biraz farklılık gösterir. Bir nesne türü yöntemleri için bağımsız değişken geçirdiğinizde üst türe çevirme otomatik olarak uygulanır. Parametre türü esnek bir türü olarak bildirilmiş sürece ancak, bir modüldeki let bağlı işlevleri için üst türe çevirme otomatik, değildir. Daha fazla bilgi için bkz: [esnek türler](flexible-Types.md).

`:>` İşleci cast, cast başarısını derleme zamanında belirlenir başka bir deyişle, statik gerçekleştirir. Kullanan bir cast varsa `:>` başarıyla derlenen geçerli bir cast olduğundan ve hiçbir sıkıştırılabilmesi çalışma zamanında hata.

Aynı zamanda `upcast` böyle bir dönüştürme gerçekleştirmek için işleci. Aşağıdaki ifade, hiyerarşi içinde yukarı doğru bir dönüştürme belirtir:

```fsharp
upcast expression
```

Upcast işleci kullandığınızda, derleyici bağlamdan dönüştürüyorsunuz türü Infer dener. Derleyici hedef türü belirlenemiyor ise derleyici bir hata bildirir.

### <a name="downcasting"></a>Alt türe çevirme
`:?>` İşleci cast, cast başarısını çalışma zamanında belirlenir yani dinamik gerçekleştirir. Kullanan bir cast `:?>` işleci derleme zamanında; işaretlenmediği ancak çalışma zamanında denemesi belirtilen türe için yapılır. Nesne hedef türü ile uyumlu ise, cast başarılı olur. Nesne hedef türü ile uyumlu değilse, çalışma zamanı başlatır bir `InvalidCastException`.

Aynı zamanda `downcast` dinamik tür dönüştürme gerçekleştirmek için işleci. Aşağıdaki ifade program bağlamından çıkarımı yapılan tür hiyerarşide aşağı bir dönüştürme belirtir:

```fsharp
downcast expression
```

Olarak `upcast` işleci, derleyici bağlamı belirli hedef türünden gösterilemez, rapor hata.

Aşağıdaki kod kullanımını göstermektedir `:>` ve `:?>` işleçler. Kod gösterir `:?>` işleci oluşturur, çünkü dönüştürme başarılı olur olduğunu bildiğiniz durumlarda en iyi şekilde kullanılan `InvalidCastException` dönüştürme başarısız olursa. Dönüştürme başarılı olur, kullanan bir tür testini bilmiyorsanız bir `match` ifade olduğundan daha iyi bir özel durum oluşturma yükünü ortadan kaldırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Çünkü genel işleçler `downcast` ve `upcast` tür çıkarımı bağımsız değişkeni ve dönüş türü Yukarıdaki kod belirlemek için kullanır, değiştirebilirsiniz

```fsharp
let base1 = d1 :> Base1
```

örneklerini şununla değiştirin:

```fsharp
let base1 = upcast d1
```

Önceki kod içinde bağımsız değişken türü ve dönüş türleri olan `Derived1` ve `Base1`sırasıyla.

Türü testleri hakkında daha fazla bilgi için bkz: [eşleşme ifadeleri](match-Expressions.md).

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)
