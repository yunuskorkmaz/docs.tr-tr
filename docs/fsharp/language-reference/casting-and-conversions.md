---
title: Atama ve Dönüştürmeler
description: F# Programlama dilinin çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri nasıl sağladığını öğrenin.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543592"
---
# <a name="casting-and-conversions-f"></a>Atama ve Dönüştürmeler (F#)

Bu konuda içindeki F#tür dönüştürmeleri için destek açıklanmaktadır.

## <a name="arithmetic-types"></a>Aritmetik türler

F#tamsayı ve kayan nokta türleri arasındaki gibi çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri sağlar. İntegral ve Char dönüştürme işleçleri denetlenen ve Denetlenmemiş formlara sahiptir; kayan nokta işleçleri ve `enum` dönüştürme işleci değildir. Denetlenmemiş formlar `Microsoft.FSharp.Core.Operators` tanımlanmıştır ve denetlenen formlar `Microsoft.FSharp.Core.Operators.Checked`tanımlanmıştır. Denetlenen formlar taşma durumunu denetler ve elde edilen değer hedef türün sınırlarını aşarsa bir çalışma zamanı özel durumu oluşturur.

Bu işleçlerin her biri, hedef türünün adı ile aynı ada sahiptir. Örneğin, aşağıdaki kodda, türlerin açıkça açıklandığı, `byte` iki farklı anlam ile görünür. İlk oluşum türdür, ikincisi ise dönüştürme işleçtir.

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
|`decimal`|`System.Decimal`Dönüştür.|
|`char`|Bir Unicode karakter olan `System.Char`Dönüştür.|
|`enum`|Numaralandırılmış bir türe Dönüştür.|

Yerleşik temel türlerin yanı sıra, bu işleçleri, uygun imzalara sahip `op_Explicit` veya `op_Implicit` Yöntemler uygulayan türlerle kullanabilirsiniz. Örneğin, `int` dönüştürme işleci, türü parametre olarak alan ve `int`döndüren statik bir yöntem `op_Explicit` sağlayan herhangi bir tür ile birlikte kullanılır. Genel kurala özel bir özel durum olarak, metotları dönüş türü tarafından aşırı yüklenemez, bunu `op_Explicit` ve `op_Implicit`için yapabilirsiniz.

## <a name="enumerated-types"></a>Numaralandırılmış türler

`enum` işleci, dönüştürülecek `enum` türünü temsil eden bir tür parametresi alan genel bir işleçtir. Numaralandırılmış bir türe dönüşürse, dönüştürmek istediğiniz `enum` türünü tespit etmek için çıkarım denemeleri yazın. Aşağıdaki örnekte `col1` değişkeni açıkça açıklanmaz, ancak türü daha sonraki eşitlik testinde çıkarsanamıyor. Bu nedenle, derleyici `Color` bir numaralandırmaya dönüştürmekte olduğunuz tarafından ortaya çıkarılamıyor. Alternatif olarak, aşağıdaki örnekte `col2` gibi bir tür ek açıklaması sağlayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Hedef numaralandırma türünü, aşağıdaki kodda olduğu gibi açıkça bir tür parametresi olarak da belirtebilirsiniz:

```fsharp
let col3 = enum<Color> 3
```

Sabit listesinin, yalnızca Numaralandırmadaki temeldeki tür, dönüştürülmekte olan türle uyumluysa çalıştığını unutmayın. Aşağıdaki kodda, `int32` ve `uint32`arasındaki uyuşmazlık nedeniyle dönüştürme derlenemiyor.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Daha fazla bilgi için bkz. [numaralandırmalar](enumerations.md).

## <a name="casting-object-types"></a>Nesne türlerini atama

Nesne hiyerarşisindeki türler arasında dönüştürme, nesne odaklı programlama için temel bir nesnedir. İki temel dönüştürme türü vardır: atama (yukarı atama) ve (aşağı atama). Bir hiyerarşiyi atama, türetilmiş bir nesne başvurusundan bir temel nesne başvurusuna atama anlamına gelir. Bu tür bir dönüştürme, temel sınıf türetilmiş sınıfın devralma hiyerarşisinde olduğu sürece çalışma garantisi verir. Bir hiyerarşiyi, bir temel nesne başvurusundan türetilmiş bir nesne başvurusuna dönüştürme işlemi, yalnızca nesne doğru hedef (türetilen) türünün bir örneği veya hedef türünden türetilmiş bir tür olduğunda başarılı olur.

F#Bu dönüştürme türleri için işleçler sağlar. `:>` işleci hiyerarşiyi yayınlar ve `:?>` işleci hiyerarşiyi aşağı yayınlar.

### <a name="upcasting"></a>Yukarı atama

Birçok nesne yönelimli dilde, yukarı atama örtük bir şekilde; ' F#de, kurallar biraz farklıdır. Bağımsız değişkenleri bir nesne türündeki yöntemlere geçirdiğinizde, upatama otomatik olarak uygulanır. Ancak, bir modüldeki izin-sınırlı işlevler için, parametre türü esnek bir tür olarak bildirilemediği sürece, UPI otomatik değildir. Daha fazla bilgi için bkz. [Esnek türler](flexible-Types.md).

`:>` işleci statik bir atama gerçekleştirir, bu, dönüştürmenin başarısı derleme zamanında belirlendiği anlamına gelir. `:>` kullanan bir tür başarıyla derleniyorsa, bu geçerli bir tür ve çalışma zamanında başarısız olur.

Bu tür bir dönüştürme gerçekleştirmek için `upcast` işlecini de kullanabilirsiniz. Aşağıdaki ifade hiyerarşinin bir dönüşümünü belirtir:

```fsharp
upcast expression
```

Upcast işlecini kullandığınızda, derleyici, bağlamındaki dönüştürmekte olduğunuz türü çıkarmakta çalışır. Derleyici hedef türünü tespit leyemiyorsa, derleyici bir hata bildirir. Tür ek açıklaması gerekli olabilir.

### <a name="downcasting"></a>Alta çevrim

`:?>` işleci dinamik bir atama gerçekleştirir, bu, dönüştürmenin başarısı çalışma zamanında belirlendiği anlamına gelir. `:?>` işlecini kullanan bir tür derleme sırasında denetlenmez; Ancak çalışma zamanında, belirtilen türe dönüştürmek için bir girişimde bulunuldu. Nesne hedef türle uyumluysa, atama başarılı olur. Nesne hedef türle uyumlu değilse, çalışma zamanı bir `InvalidCastException`oluşturur.

Dinamik bir tür dönüştürmesi gerçekleştirmek için `downcast` işlecini de kullanabilirsiniz. Aşağıdaki ifade, hiyerarşinin bir program bağlamından çıkarılan bir türe dönüştürülmesini belirtir:

```fsharp
downcast expression
```

`upcast` işleci olarak, derleyici bağlamdan belirli bir hedef türü çıkarsanamıyor bir hata bildirir. Tür ek açıklaması gerekli olabilir.

Aşağıdaki kod `:>` ve `:?>` işleçlerinin kullanımını gösterir. Kod, dönüştürmenin başarılı olacağını bildiğiniz için `:?>` işlecinin en iyi kullanıldığını gösterir, çünkü dönüştürme başarısız olursa `InvalidCastException` oluşturur. Dönüştürmenin başarılı olacağını görmüyorsanız, bir özel durum oluşturma yükünü önlediği için `match` ifadesi kullanan bir tür testi daha iyidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Genel işleçler `downcast` ve `upcast` bağımsız değişkeni ve dönüş türünü belirleyebilmek için tür çıkarımı kullandığından, yukarıdaki kodda değiştirebilirsiniz

```fsharp
let base1 = d1 :> Base1
```

şununla değiştirin

```fsharp
let base1: Base1 = upcast d1
```

Bir tür ek açıklaması gerektiğini unutmayın, çünkü kendisi `upcast`, temel sınıfı belirleyemez.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
