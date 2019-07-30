---
title: Atama ve Dönüştürmeler
description: F# Programlama dilinin çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri nasıl sağladığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630426"
---
# <a name="casting-and-conversions-f"></a>Atama ve Dönüştürmeler (F#)

Bu konuda içindeki F#tür dönüştürmeleri için destek açıklanmaktadır.

## <a name="arithmetic-types"></a>Aritmetik türler

F#tamsayı ve kayan nokta türleri arasındaki gibi çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri sağlar. İntegral ve Char dönüştürme işleçleri denetlenen ve Denetlenmemiş formlara sahiptir; kayan nokta işleçleri ve `enum` dönüştürme işleci değildir. Denetlenmemiş Formlar ' de `Microsoft.FSharp.Core.Operators` tanımlanmıştır ve denetlenen formlarda ' de `Microsoft.FSharp.Core.Operators.Checked`tanımlanmıştır. Denetlenen formlar taşma durumunu denetler ve elde edilen değer hedef türün sınırlarını aşarsa bir çalışma zamanı özel durumu oluşturur.

Bu işleçlerin her biri, hedef türünün adı ile aynı ada sahiptir. Örneğin, aşağıdaki kodda, türlerin açıkça açıklandığı `byte` , iki farklı anlam ile görünür. İlk oluşum türdür, ikincisi ise dönüştürme işleçtir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

Aşağıdaki tabloda ' de F#tanımlanan dönüştürme işleçleri gösterilmektedir.

|İşleç|Açıklama|
|--------|-----------|
|`byte`|8 bit işaretsiz bir tür bayta Dönüştür.|
|`sbyte`|İşaretli bayta Dönüştür.|
|`int16`|16 bit işaretli tamsayıya Dönüştür.|
|`uint16`|16 bit işaretsiz tamsayıya Dönüştür.|
|`int32, int`|32 bitlik işaretli tamsayıya Dönüştür.|
|`uint32`|32 bitlik işaretsiz tamsayıya Dönüştür.|
|`int64`|64 bitlik işaretli tamsayıya Dönüştür.|
|`uint64`|64 bitlik işaretsiz tamsayıya Dönüştür.|
|`nativeint`|Yerel tamsayıya Dönüştür.|
|`unativeint`|İşaretsiz yerel tamsayıya Dönüştür.|
|`float, double`|64 bitlik bir çift duyarlıklı IEEE kayan noktalı sayıya dönüştürün.|
|`float32, single`|32 bitlik tek duyarlıklı bir IEEE kayan noktalı sayıya dönüştürün.|
|`decimal`|Öğesine `System.Decimal`Dönüştür.|
|`char`|`System.Char`Unicode karaktere Dönüştür.|
|`enum`|Numaralandırılmış bir türe Dönüştür.|

Yerleşik temel türlerin yanı sıra, bu işleçleri, veya `op_Explicit` `op_Implicit` uygun imzalara sahip Yöntemler uygulayan türlerle birlikte kullanabilirsiniz. Örneğin, `int` dönüştürme işleci, türü parametre olarak alan ve döndüren `int`statik bir yöntem `op_Explicit` sağlayan herhangi bir tür ile birlikte kullanılır. Genel kurala özel bir özel durum olarak, metotları dönüş türü tarafından aşırı yüklenemez, ve `op_Explicit` `op_Implicit`için bunu yapabilirsiniz.

## <a name="enumerated-types"></a>Numaralandırılmış türler

İşleci, dönüştürülecek `enum` öğesinin türünü temsil eden bir tür parametresi alan genel bir işleçtir. `enum` Numaralandırılmış bir türe dönüşürse, dönüştürmek istediğiniz öğesinin `enum` türünü belirlemekte çıkarım denemeleri yazın. Aşağıdaki örnekte, değişkeni `col1` açıkça açıklama eklenmiş değildir, ancak türü daha sonraki eşitlik testinde çıkarsanamıyor. Bu nedenle, derleyici bir `Color` numaralandırmaya dönüştürmekte olduğunuz tarafından ortaya çıkarılamıyor. Alternatif olarak, aşağıdaki örnekte olduğu gibi `col2` bir tür ek açıklaması sağlayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Hedef numaralandırma türünü, aşağıdaki kodda olduğu gibi açıkça bir tür parametresi olarak da belirtebilirsiniz:

```fsharp
let col3 = enum<Color> 3
```

Sabit listesinin, yalnızca Numaralandırmadaki temeldeki tür, dönüştürülmekte olan türle uyumluysa çalıştığını unutmayın. Aşağıdaki kodda, ve `int32` `uint32`arasındaki uyuşmazlığın nedeniyle dönüştürme derlenemiyor.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Daha fazla bilgi için bkz. [numaralandırmalar](enumerations.md).

## <a name="casting-object-types"></a>Nesne türlerini atama

Nesne hiyerarşisindeki türler arasında dönüştürme, nesne odaklı programlama için temel bir nesnedir. İki temel dönüştürme türü vardır: atama (yukarı atama) ve (aşağı atama). Bir hiyerarşiyi atama, türetilmiş bir nesne başvurusundan bir temel nesne başvurusuna atama anlamına gelir. Bu tür bir dönüştürme, temel sınıf türetilmiş sınıfın devralma hiyerarşisinde olduğu sürece çalışma garantisi verir. Bir hiyerarşiyi, bir temel nesne başvurusundan türetilmiş bir nesne başvurusuna dönüştürme işlemi, yalnızca nesne doğru hedef (türetilen) türünün bir örneği veya hedef türünden türetilmiş bir tür olduğunda başarılı olur.

F#Bu dönüştürme türleri için işleçler sağlar. İşleci hiyerarşiyi yayınlar `:?>` ve operatör hiyerarşiyi aşağı yayınlar. `:>`

### <a name="upcasting"></a>Yukarı atama

Birçok nesne yönelimli dilde, yukarı atama örtük bir şekilde; ' F#de, kurallar biraz farklıdır. Bağımsız değişkenleri bir nesne türündeki yöntemlere geçirdiğinizde, upatama otomatik olarak uygulanır. Ancak, bir modüldeki izin-sınırlı işlevler için, parametre türü esnek bir tür olarak bildirilemediği sürece, UPI otomatik değildir. Daha fazla bilgi için bkz. [Esnek türler](flexible-Types.md).

`:>` İşleci statik bir atama gerçekleştirir, bu, dönüştürmenin başarısı derleme zamanında belirlendiği anlamına gelir. Kullanan `:>` bir tür başarıyla derleniyorsa, bu geçerli bir tür ve çalışma zamanında hata şansı yoktur.

Bu tür bir dönüştürme gerçekleştirmek `upcast` için işlecini de kullanabilirsiniz. Aşağıdaki ifade hiyerarşinin bir dönüşümünü belirtir:

```fsharp
upcast expression
```

Upcast işlecini kullandığınızda, derleyici, bağlamındaki dönüştürmekte olduğunuz türü çıkarmakta çalışır. Derleyici hedef türünü tespit leyemiyorsa, derleyici bir hata bildirir.

### <a name="downcasting"></a>Alta çevrim

`:?>` İşleci dinamik bir atama gerçekleştirir, bu, dönüştürmenin başarısı çalışma zamanında belirlendiği anlamına gelir. `:?>` İşleci kullanan bir tür derleme zamanında denetlenmez; ancak çalışma zamanında, belirtilen türe atama için bir deneme yapılır. Nesne hedef türle uyumluysa, atama başarılı olur. Nesne hedef türle uyumlu değilse, çalışma zamanı bir `InvalidCastException`oluşturur.

Dinamik bir tür dönüştürmesi gerçekleştirmek `downcast` için işlecini de kullanabilirsiniz. Aşağıdaki ifade, hiyerarşinin bir program bağlamından çıkarılan bir türe dönüştürülmesini belirtir:

```fsharp
downcast expression
```

`upcast` İşleci olarak, derleyici bağlamdan belirli bir hedef türü çıkarsanamıyor bir hata bildirir.

Aşağıdaki kod, `:>` ve `:?>` işleçlerinin kullanımını gösterir. Kod, dönüştürmenin başarılı `:?>` `InvalidCastException` olacağını bildiğiniz zaman, dönüştürmenin başarısız olup olmadığını belirten işlecin en iyi şekilde kullanıldığını gösterir. Dönüştürmenin başarılı olacağını görmüyorsanız, bir `match` ifade kullanan bir tür testi daha iyidir, çünkü özel durum oluşturma ek yükünü önler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Bağımsız değişkeni ve `downcast` dönüş `upcast` türünü belirleyebilmek için genel işleçler ve tür çıkarımı kullandığından, yukarıdaki kodda değiştirebilirsiniz

```fsharp
let base1 = d1 :> Base1
```

örneklerini şununla değiştirin:

```fsharp
let base1 = upcast d1
```

Önceki kodda, bağımsız değişken türü ve dönüş türleri sırasıyla ve `Derived1` `Base1`' dir.

Tür testleri hakkında daha fazla bilgi için bkz. [Match ifadeleri](match-Expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
