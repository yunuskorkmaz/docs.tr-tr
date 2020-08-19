---
title: Seçenekler
description: 'Adlandırılmış bir değer veya değişken için gerçek bir değer bulunmaması durumunda F # seçenek türlerini nasıl kullanacağınızı öğrenin.'
ms.date: 08/13/2020
ms.openlocfilehash: 0618590c10f6ecac51a23483ca0ab6cd66f2df4f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557574"
---
# <a name="options"></a>Seçenekler

F # içindeki seçenek türü, bir gerçek değer, adlandırılmış bir değer veya değişken için mevcut olmadığında kullanılır. Bir seçenek, temel alınan bir türe sahiptir ve bu tür bir değeri tutabilir ya da bir değere sahip olmayabilir.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki kod, bir seçenek türü üreten bir işlevi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Gördüğünüz gibi `a` , giriş 0 ' dan büyükse, `Some(a)` oluşturulur.  Aksi takdirde, `None` oluşturulur.

Değer, `None` bir seçenek gerçek değere sahip olmadığında kullanılır. Aksi takdirde, ifade, `Some( ... )` seçeneğe bir değer verir. Değerler `Some` ve, `None` Bu, `exists` seçeneğin bir değeri varsa ve yoksa ' i döndüren aşağıdaki işlevde gösterildiği gibi, model eşleştirme için yararlıdır `true` `false` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Seçenekleri kullanma

Aşağıdaki kodda gösterildiği gibi, bir arama eşleşen bir sonuç döndürmezse, Seçenekler yaygın olarak kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

Önceki kodda, bir liste özyinelemeli olarak aranır. İşlevi `tryFindMatch` `pred` , Boole değeri döndüren bir koşul işlevini ve arama yapılacak bir listeyi alır. Koşulu karşılayan bir öğe bulunursa, özyineleme sonlanır ve işlev değeri ifadede bir seçenek olarak döndürür `Some(head)` . Boş liste eşleştiğinde özyineleme sona erer. Bu noktada değer `head` bulunamadı ve `None` döndürülür.

Var olan veya mevcut olmayan bir değer için koleksiyon araymakta olan çok sayıda F # Kitaplığı işlevi türü döndürür `option` . Kurala göre, bu işlevler, `try` Örneğin, önekiyle başlar [`Seq.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex) .

Seçenekler bir değer mevcut olmadığında da yararlı olabilir, örneğin bir değer oluşturmaya çalıştığınızda bir özel durum oluşturulması mümkündür. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile`Önceki örnekteki işlevin türü vardır `string -> File option` çünkü `File` dosya başarılı bir şekilde açılırsa ve `None` bir özel durum oluşursa bir nesne döndürür. Duruma bağlı olarak, yaymaya izin vermek yerine özel bir durum yakalamak için uygun bir tasarım seçeneği olmayabilir.

Buna ek olarak, `null` `Some` bir seçenek olması durumunda ya da null değer olan bir değer geçirmek mümkün olacaktır. Bu genellikle kaçınılmaz ve genellikle rutin F # programlamasında bulunur, ancak .NET 'teki başvuru türlerinin doğası nedeniyle mümkündür.

## <a name="option-properties-and-methods"></a>Seçenek özellikleri ve yöntemleri

Seçenek türü, aşağıdaki özellikleri ve yöntemleri destekler.

|Özellik veya Yöntem|Tür|Açıklama|
|------------------|----|-----------|
|[Hiçbiri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#None)|`'T option`|Değer içeren bir seçenek değeri oluşturmanızı sağlayan statik özellik `None` .|
|[IsNone](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsNone)|`bool`|`true`Seçeneğin değere sahip olup olmadığını döndürür `None` .|
|[IsSome](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsSome)|`bool`|`true`Seçenekte olmayan bir değer varsa döndürür `None` .|
|[Bazen](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Some)|`'T option`|Olmayan bir değer içeren bir seçenek oluşturan statik üye `None` .|
|[Değer](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Value)|`'T`|Temel değeri döndürür veya değer ise bir oluşturur `System.NullReferenceException` `None` .|

## <a name="option-module"></a>Seçenek modülü

Seçenekler üzerinde işlemler gerçekleştiren yararlı işlevler içeren bir modül, [seçeneği](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html)vardır. Bazı işlevler özelliklerin işlevselliğini yineler ancak bir işlevin gerekli olduğu bağlamlarda faydalıdır. [Option. IsSome](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isSome) ve [Option. ınone](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isNone) , bir seçeneğin bir değer içerip içermediğini test eden modül işlevleridir. [Seçenek. Get](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#get) , varsa değeri edinir. Değer yoksa, oluşturur `System.ArgumentException` .

[Option. Bind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#bind) işlevi bir değer varsa değer üzerinde bir işlevi yürütür. İşlev tam olarak bir bağımsız değişken almalıdır ve parametre türü seçenek türü olmalıdır. İşlevin dönüş değeri başka bir seçenek türüdür.

Seçenek modülü Ayrıca listeler, diziler, diziler ve diğer koleksiyon türleri için kullanılabilen işlevlere karşılık gelen işlevleri de içerir. Bu işlevler,,,,, [`Option.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#map) [`Option.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#iter) ve içerir [`Option.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#forall) [`Option.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#exists) [`Option.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#foldBack) [`Option.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#fold) [`Option.count`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#count) . Bu işlevler, bir sıfır veya bir öğe koleksiyonu gibi seçeneklerin kullanılmasını sağlar. Daha fazla bilgi ve örnek için [listelerdeki](lists.md)koleksiyon işlevlerinin tartışmalarına bakın.

## <a name="converting-to-other-types"></a>Diğer türlere dönüştürme

Seçenekler, listelere veya dizilere dönüştürülebilir. Bir seçenek bu veri yapılarından birine dönüştürüldüğünde, sonuçta elde edilen veri yapısının sıfır veya bir öğesi vardır. Bir seçeneği diziye dönüştürmek için kullanın [`Option.toArray`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toArray) . Bir seçeneği listeye dönüştürmek için kullanın [`Option.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toList) .

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
