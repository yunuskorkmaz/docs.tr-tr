---
title: "Seçenekler (F#)"
description: "Bir adlandırılmış değeri veya değişken türleri gerçek bir değer olduğunda var olmayabilir F # seçeneği kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a15b5cf1-9055-4481-918c-4c8a051b5829
ms.openlocfilehash: 537ba69aecc1ab489de63d67c5f9ff857afb4a28
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="options"></a>Seçenekler

Bir adlandırılmış değeri veya değişken için bir gerçek değer var olmayabilir F # seçenek türü kullanılır. İsteğe bağlı bir temel alınan tür vardır ve bu türde bir değer tutabilir veya bir değere sahip olmayabilir.

## <a name="remarks"></a>Açıklamalar
Aşağıdaki kod bir seçenek türü oluşturan bir işlev gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Varsa görebileceğiniz gibi giriş `a` 0'dan büyük `Some(a)` oluşturulur.  Aksi takdirde `None` oluşturulur.

Değer `None` bir seçenek bir asıl değere sahip olmadığında kullanılır. Aksi takdirde, ifade `Some( ... )` bir değer seçeneği sunar. Değerleri `Some` ve `None` düzeni, olduğu gibi aşağıdaki işlevi eşleştirmelerinde yararlıdır `exists`, döndüren `true` seçeneği bir değeri varsa ve `false` mevcut değilse.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Seçeneklerini kullanma
Bir arama eşleşen bir sonuç döndürmüyor olduğunda seçenekleri aşağıdaki kodda gösterildiği gibi yaygın olarak kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

Önceki kodda Aranan yinelemeli olarak listesidir. İşlev `tryFindMatch` koşul bir işlev alır `pred` bir Boole değeri ve aramak için bir liste döndürür. Koşulu karşılayan bir öğe bulunursa, özyineleme sona erer ve işlevi döndürür değer ifadesi bir seçenek olarak `Some(head)`. Boş bir liste eşleştiğinde özyineleme sona erer. Bu noktada değeri `head` bulunamadı, ve `None` döndürülür.

Bir koleksiyonu olabilir veya return olmayabilir bir değer için arama birçok F # kitaplığı işlevleri `option` türü. Bu işlevler kurala göre başlayın `try` önek, örneğin, [ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).

Ayrıca bir değer, mümkünse bir değer oluşturmaya çalışırken bir özel durum, örneğin mevcut olmayabilir seçenekleri kullanışlı olabilir. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile` Önceki örnekte işlevi türüne sahip `string -> File option` onu döndürdüğünden bir `File` dosya başarıyla açılır, nesne ve `None` bir özel durum oluşursa. Durum bağlı olarak, bu yayılmasına izin vererek yerine bir özel durum yakalamak için bir uygun tasarım seçiminin olmayabilir.


## <a name="option-properties-and-methods"></a>Seçenek özellikleri ve yöntemleri
Seçenek türü aşağıdaki özellikleri ve yöntemleri destekler.



|Özelliği veya yöntemi|Tür|Açıklama|
|------------------|----|-----------|
|[Yok](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Sahip bir seçenek değeri oluşturmanızı sağlayan bir statik özellik `None` değeri.|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Döndürür `true` seçeneği varsa `None` değeri.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Döndürür `true` seçeneği olmayan bir değer varsa `None`.|
|[Bazı](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Bir seçenek oluşturan statik bir üyenin olmayan bir değere sahip `None`.|
|[Değer](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Temel alınan değeri döndürür veya oluşturur bir `System.NullReferenceException` değer ise `None`.|

## <a name="option-module"></a>Option Modülü
Bir modül yok [seçeneği](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), seçenekleri işlemleri yararlı işlevler içerir. Bazı işlevler özellikleri işlevselliğini yineleyin ancak burada bir işlev gerekli bağlamlarda yararlıdır. [Option.IsSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) ve [Option.IsNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) bir seçenek değeri tutan olup olmadığını test hem modülü işlevlerdir. [Option.get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) varsa değerini alır. Değer yoksa oluşturur `System.ArgumentException`.

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) işlevi bir değer ise bu işlev değerine göre yürütür. İşlev tam olarak bir bağımsız değişken almanız gerekir ve parametre türü seçenek türü olmalıdır. İşlevinin dönüş değeri, yalnızca başka bir seçenek türüdür.

Option modülü listeler, dizileri, dizileri ve diğer koleksiyon türleri için kullanılabilen işlevlerin karşılık işlevleri de içerir. Bu işlevler [ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622), [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99), [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb), [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), ve [ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876). Bu işlevler sıfır veya bir öğe koleksiyonunu gibi kullanılması için seçenekler sağlar. Daha fazla bilgi ve örnekler için toplama işlevlerinde tartışma bkz [listeler](lists.md).


## <a name="converting-to-other-types"></a>Diğer türleri dönüştürme
Seçenekler, listeleri ya da diziler dönüştürülebilir. Bir seçenek bu veri yapıları birini dönüştürüldüğünde ortaya çıkan veri yapısı sıfır veya bir öğeye sahip. Dizi için bir seçenek dönüştürmek için [ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Bir liste için bir seçenek dönüştürmek için [ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).


## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)

[F # türleri](fsharp-types.md)
