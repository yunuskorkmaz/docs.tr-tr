---
title: Atama ve Dönüştürmeler
description: Bilgi nasıl F# programlama dili sağlayan dönüştürme işleçleri aritmetik dönüştürmeler çeşitli ilkel türler arasında.
ms.date: 05/16/2016
ms.openlocfilehash: 2a12d48106a267edfc67c9e7b3d3a7bd41d8261c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966627"
---
# <a name="casting-and-conversions-f"></a>Atama ve Dönüştürmeler (F#)

Bu konuda, tür dönüştürmelerinde desteği açıklanmaktadır F#.

## <a name="arithmetic-types"></a>Aritmetik tür

F#Dönüştürme işleçleri aritmetik dönüştürmeler çeşitli ilkel türler arasında gibi tamsayı ve kayan nokta türleri arasında sağlar. İntegral ve karakter dönüştürme işleçleri iade etmiş ve Denetlenmeyen forms; kayan nokta işleçler ve `enum` dönüştürme işleci yapın. Denetlenmeyen forms tanımlanan `Microsoft.FSharp.Core.Operators` ve işaretli forms tanımlanan `Microsoft.FSharp.Core.Operators.Checked`. İşaretli formları için taşmayı denetle ve sonuç değerini hedef türünün limitlerini aşarsam bir çalışma zamanı özel durumu oluşturur.

Bu işleçlerden her biri, hedef türünün adı ile aynı ada sahiptir. Hangi türleri açıkça ek açıklama, örneğin, aşağıdaki kodda, `byte` ile iki farklı anlamları görünür. İlk yinelenme türüdür ve ikincisi dönüştürme işleci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

Aşağıdaki tabloda tanımlanan dönüşüm işleçleri gösterilmektedir F#.

|İşleç|Açıklama|
|--------|-----------|
|`byte`|Bir 8 bit işaretsiz türe bayta dönüştürün.|
|`sbyte`|İmzalanan byte'a Dönüştür.|
|`int16`|16 bit işaretli bir tamsayıya dönüştürün.|
|`uint16`|Bir 16 bitlik işaretsiz tamsayı dönüştürün.|
|`int32, int`|32-bit işaretli bir tamsayıya dönüştürün.|
|`uint32`|Bir 32-bit işaretsiz tamsayıyı dönüştürün.|
|`int64`|Bir 64-bit işaretli bir tamsayıya dönüştürün.|
|`uint64`|Bir 64-bit işaretsiz tamsayıyı dönüştürün.|
|`nativeint`|Yerel bir tamsayıya dönüştürün.|
|`unativeint`|Yerel bir işaretsiz tamsayı dönüştürün.|
|`float, double`|Bir 64-bit çift duyarlıklı IEEE kayan noktalı sayı dönüştürün.|
|`float32, single`|Bir 32-bit tek duyarlıklı IEEE kayan noktalı sayı dönüştürün.|
|`decimal`|Dönüştürme `System.Decimal`.|
|`char`|Dönüştürme `System.Char`, bir Unicode karakter.|
|`enum`|Numaralandırılmış bir türe dönüştürün.|

Ek olarak yerleşik temel türler, bu işleçler uygulayan türler ile kullanabilirsiniz `op_Explicit` veya `op_Implicit` uygun imzalara sahip yöntemleri. Örneğin, `int` çalışır bir statik yöntem sağlar herhangi bir tür dönüştürme işleci `op_Explicit` türü bir parametre olarak alır ve döndürür `int`. Yöntem dönüş türüne göre aşırı yüklenemez genel kural için bir özel durum bunu yapabilmeniz `op_Explicit` ve `op_Implicit`.

## <a name="enumerated-types"></a>Numaralandırılmış türler

`enum` İşlecidir türünü temsil eden bir tür parametre alan bir genel işleç `enum` dönüştürmek için. Numaralandırılmış bir türe dönüştürürken türünü belirlemek için çıkarım denemeleri yazın `enum` dönüştürmek istediğiniz. Aşağıdaki örnekte, değişken `col1` açıkça açıklama değil, ancak sonraki eşitlik testi türünü algılanır. Bu nedenle, derleyici için dönüştürdüğünüz çıkarabilir bir `Color` sabit listesi. Alternatif olarak, bir tür ek açıklamasına sağlayabilirsiniz olduğu gibi `col2` aşağıdaki örnekte.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Hedef numaralandırma türüne açıkça aşağıdaki kodda gösterildiği gibi bir tür parametresi olarak belirtebilirsiniz:

```fsharp
let col3 = enum<Color> 3
```

Sabit listesi türünü temel dönüştürülen türü ile uyumlu ise sabit iş bıraktığı unutmayın. Aşağıdaki kodda, dönüştürme başarısız arasındaki uyumsuzluk nedeniyle derleme `int32` ve `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Daha fazla bilgi için [numaralandırmalar](enumerations.md).

## <a name="casting-object-types"></a>Nesne türlerini atama

Bir nesne sıradüzeni türleri arasında dönüştürme, nesne yönelimli programlama için temeldir. İki temel tür dönüştürmeleri vardır: (yukarı çevrim) atama ve atama (Alta). Bir hiyerarşi atama temel nesne başvurusu için türetilmiş nesneden başvurudan atama anlamına gelir. Böyle bir dönüştürme, temel sınıfın türetilmiş sınıf devralma hiyerarşisinde olduğu sürece çalışmak için sağlanır. Yalnızca nesne (türetilmiş) doğru hedef türüne veya hedef türünden türetilmiş bir tür örneği gerçekten ise bir hiyerarşiden bir türetilmiş nesne başvurusu bir temel nesne başvurusu aşağı atama başarılı olur.

F#Bu türde dönüştürme işleçleri sağlar. `:>` İşleci hiyerarşisinde yukarı çevirir ve `:?>` işleci hiyerarşinin çevirir.

### <a name="upcasting"></a>Yukarı çevrim

Birçok nesne odaklı dildeki içinde yukarı çevrim örtük olarak; içinde F#, kuralları biraz farklıdır. Bir nesne türü yöntemi için değişken geçtiğinizde yukarı çevrim otomatik olarak uygulanır. Parametre türü esnek bir türü olarak bildirilmiş sürece ancak, Modül içindeki let bağlı işlevler için yukarı çevrim otomatik, değildir. Daha fazla bilgi için [esnek türler](flexible-Types.md).

`:>` İşleç gerçekleştirir statik atama, atama başarılı derleme zamanında belirlenir anlamına gelir. Kullanan bir tür dönüştürme, `:>` başarıyla derlenir, geçerli bir yayın olduğunu ve hiçbir şansı çalışma zamanında hata.

Ayrıca `upcast` böyle bir dönüştürme gerçekleştirmek için işleci. Aşağıdaki ifade, hiyerarşi bir dönüştürme belirtir:

```fsharp
upcast expression
```

Upcast işleci kullandığınızda derleyici bağlamdan dönüştürüyorsanız türünün çıkarsanması çalışır. Derleyicinin hedef türü belirlenemiyor ise, derleyici bir hata bildirir.

### <a name="downcasting"></a>Alta dönüştürme işlemi

`:?>` İşleci gerçekleştiren bir dinamik atama, atama başarılı çalışma zamanında belirlenir anlamına gelir. Kullanan bir yayın `:?>` işleci, derleme zamanında; işaretlenmediği ancak çalışma zamanında girişimini belirtilen türe için yapılır. Nesne hedef türüyle uyumlu ise, atama başarılı olur. Nesne hedef türüyle uyumlu değil, çalışma zamanı başlatır. bir `InvalidCastException`.

Ayrıca `downcast` dinamik tür dönüştürmesi gerçekleştirmek için işleci. Aşağıdaki ifade, hiyerarşide aşağı doğru programı bağlamından çıkarılan bir türe dönüştürmeyi belirtir:

```fsharp
downcast expression
```

Olarak `upcast` işleci, derleyici bağlamından belirli hedef türü çıkarımı yapılamıyor, rapor bir hata oluştu.

Aşağıdaki kod kullanışını `:>` ve `:?>` işleçleri. Kod gösterir `:?>` işleci oluşturur, çünkü dönüştürme başarılı olur olduğunu bildiğiniz durumlarda en iyi şekilde kullanılan `InvalidCastException` dönüştürme başarısız olursa. Dönüştürme başarılı olur, kullanan bir tür testi bilmiyorsanız bir `match` ifadesi, bir özel durum oluşturma ek yükü önlediği için iyidir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Çünkü genel işleçler `downcast` ve `upcast` Yukarıdaki koddaki bağımsız değişkenin ve dönüş türünü belirlemek için tür çıkarımı dayanır, değiştirebilirsiniz

```fsharp
let base1 = d1 :> Base1
```

örneklerini şununla değiştirin:

```fsharp
let base1 = upcast d1
```

Önceki kodda, bağımsız değişken türü ve dönüş türleri olan `Derived1` ve `Base1`sırasıyla.

Türü testleri hakkında daha fazla bilgi için bkz: [eşleşme ifadeleri](match-Expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
