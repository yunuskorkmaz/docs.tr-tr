---
title: Seçenekler
description: Adlandırılmış bir değer veya F# değişken için gerçek bir değer bulunmaması durumunda seçenek türlerini nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 9326cf04f53adac7422c09a49a59c4eecd49486d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627354"
---
# <a name="options"></a>Seçenekler

İçindeki F# seçenek türü, bir gerçek değer, adlandırılmış bir değer veya değişken için mevcut olmadığında kullanılır. Bir seçenek, temel alınan bir türe sahiptir ve bu tür bir değeri tutabilir ya da bir değere sahip olmayabilir.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki kod, bir seçenek türü üreten bir işlevi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Gördüğünüz gibi, giriş `a` 0 ' dan büyükse, `Some(a)` oluşturulur.  Aksi takdirde `None` , oluşturulur.

Değer `None` , bir seçenek gerçek değere sahip olmadığında kullanılır. Aksi takdirde, ifade `Some( ... )` , seçeneğe bir değer verir. Değerler `Some` `true` ve `None` , bu, seçeneğin bir değeri varsa ve `false` yoksa ' i döndüren `exists`aşağıdaki işlevde gösterildiği gibi, model eşleştirme için yararlıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Seçenekleri kullanma

Aşağıdaki kodda gösterildiği gibi, bir arama eşleşen bir sonuç döndürmezse, Seçenekler yaygın olarak kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

Önceki kodda, bir liste özyinelemeli olarak aranır. İşlevi `tryFindMatch` , Boole değeri döndüren bir `pred` koşul işlevini ve arama yapılacak bir listeyi alır. Koşulu karşılayan bir öğe bulunursa, özyineleme sonlanır ve işlev değeri ifadede `Some(head)`bir seçenek olarak döndürür. Boş liste eşleştiğinde özyineleme sona erer. Bu noktada değer `head` bulunamadı ve `None` döndürülür.

Var F# olan veya mevcut olmayan bir değer için koleksiyon arama yapan birçok kitaplık işlevi `option` türü döndürür. Kurala göre, bu işlevler, örneğin, `try` [`Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)önekiyle başlar.

Seçenekler bir değer mevcut olmadığında da yararlı olabilir, örneğin bir değer oluşturmaya çalıştığınızda bir özel durum oluşturulması mümkündür. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

Önceki örnekteki `string -> File option`işlevintürü vardır çünkü dosya başarılı bir şekilde açılırsa ve `File` `None` bir özel durum oluşursa bir nesne döndürür. `openFile` Duruma bağlı olarak, yaymaya izin vermek yerine özel bir durum yakalamak için uygun bir tasarım seçeneği olmayabilir.

Buna ek olarak, bir seçenek `null` `Some` olması durumunda ya da null değer olan bir değer geçirmek mümkün olacaktır. Bu genellikle kaçınılmaz ve genellikle rutin F# programlamada, ancak .net 'teki başvuru türlerinin doğası nedeniyle mümkündür.

## <a name="option-properties-and-methods"></a>Seçenek özellikleri ve yöntemleri

Seçenek türü, aşağıdaki özellikleri ve yöntemleri destekler.

|Özellik veya Yöntem|Tür|Açıklama|
|------------------|----|-----------|
|[Yok.](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|`None` Değer içeren bir seçenek değeri oluşturmanızı sağlayan statik özellik.|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Seçeneğin `true` değere`None` sahip olup olmadığını döndürür.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Seçenekte `true` olmayan`None`bir değer varsa döndürür.|
|[Bazı](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Olmayan `None`bir değer içeren bir seçenek oluşturan statik üye.|
|[Değer](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Temel değeri döndürür veya `System.NullReferenceException` `None`değer ise bir oluşturur.|

## <a name="option-module"></a>Seçenek modülü

Seçenekler üzerinde işlemler gerçekleştiren yararlı işlevler içeren bir modül, [seçeneği](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c)vardır. Bazı işlevler özelliklerin işlevselliğini yineler ancak bir işlevin gerekli olduğu bağlamlarda faydalıdır. [Option. IsSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) ve [Option. ınone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) , bir seçeneğin bir değer içerip içermediğini test eden modül işlevleridir. [Seçenek. Get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) , varsa değeri edinir. Değer yoksa, oluşturur `System.ArgumentException`.

[Option. Bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) işlevi bir değer varsa değer üzerinde bir işlevi yürütür. İşlev tam olarak bir bağımsız değişken almalıdır ve parametre türü seçenek türü olmalıdır. İşlevin dönüş değeri başka bir seçenek türüdür.

Seçenek modülü Ayrıca listeler, diziler, diziler ve diğer koleksiyon türleri için kullanılabilen işlevlere karşılık gelen işlevleri de içerir. Bu [`Option.map`](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622)işlevler [,`Option.exists`](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99) [,,`Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876),, ve içerir. [`Option.iter`](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191) [`Option.forall`](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428) [`Option.foldBack`](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb) [`Option.fold`](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8) Bu işlevler, bir sıfır veya bir öğe koleksiyonu gibi seçeneklerin kullanılmasını sağlar. Daha fazla bilgi ve örnek için [listelerdeki](lists.md)koleksiyon işlevlerinin tartışmalarına bakın.

## <a name="converting-to-other-types"></a>Diğer türlere dönüştürme

Seçenekler, listelere veya dizilere dönüştürülebilir. Bir seçenek bu veri yapılarından birine dönüştürüldüğünde, sonuçta elde edilen veri yapısının sıfır veya bir öğesi vardır. Bir seçeneği diziye dönüştürmek için kullanın [`Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Bir seçeneği listeye dönüştürmek için kullanın [`Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
