---
title: Seçenekler (F#)
description: 'Adlandırılmış değer veya değişken için gerçek bir değer türleri var olmayabilir F # seçeneği kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 0859cb42e72ef9e67551b884f5cf6130fb099a78
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187828"
---
# <a name="options"></a>Seçenekler

F # seçenek türünde gerçek bir değer olmayabilir adlandırılmış değer veya değişken için kullanılır. İsteğe bağlı bir temel alınan tür vardır ve bu türde bir değer içerebilir ya da bir değer olmayabilir.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki kod bir seçenek türü oluşturan bir işlev göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Varsa görebileceğiniz gibi giriş `a` 0'dan büyükse `Some(a)` oluşturulur.  Aksi takdirde, `None` oluşturulur.

Değer `None` bir seçenek gerçek bir değer olmadığında kullanılır. Aksi takdirde, ifade `Some( ... )` seçeneği bir değer sunar. Değerleri `Some` ve `None` deseni, aşağıdaki işlevi olduğu gibi eşleşen yararlıdır `exists`, döndüren `true` seçeneği bir değer varsa ve `false` Aksi takdirde.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Seçeneklerini kullanma

Bir arama eşleşen bir sonuç döndürmez olduğunda seçenekler aşağıdaki kodda gösterildiği gibi yaygın olarak kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

Önceki kodda, aranan yinelemeli olarak listesidir. İşlev `tryFindMatch` koşul işlevini alır `pred` bir Boole değeri ve aramak için bir liste döndürür. Koşulu karşılayan bir öğe bulunmazsa, özyineleme sona erer ve işlev döndürür değer ifadesi bir seçenek olarak `Some(head)`. Boş liste eşleştiğinde özyineleme sona erer. Bu noktada değeri `head` bulunmadı, ve `None` döndürülür.

Dönüş yok veya bir değer için bir koleksiyon arama çoğu F # kitaplığı işlevleri `option` türü. Kural olarak, bu işlevler şununla `try` önek, örneğin, [ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).

Bir değer, bir değer oluşturmak çalıştığınızda bir özel durum, mümkünse, örneğin mevcut olmayabilir, seçenekleri de yararlı olabilir. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile` Önceki örnekte işlev türüne sahip `string -> File option` döndürür, çünkü bir `File` dosya başarıyla açılır, nesne ve `None` bir özel durum oluşursa. Duruma bağlı olarak, bu yayılmasına izin vererek yerine bir özel durum yakalamak için bir uygun tasarımı seçim olmayabilir.

## <a name="option-properties-and-methods"></a>Seçenek özellikleri ve yöntemleri

Seçenek türü, aşağıdaki özellikleri ve yöntemleri destekler.

|Özelliği veya yöntemi|Tür|Açıklama|
|------------------|----|-----------|
|[Yok](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Sahip bir seçenek değeri oluşturmanızı sağlayan statik bir özellik `None` değeri.|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Döndürür `true` seçeneği belirtildiyse `None` değeri.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Döndürür `true` seçeneği olmayan bir değere sahip olursa `None`.|
|[Bazı](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Bir seçenek oluşturan bir statik üye olmayan bir değere sahip `None`.|
|[Değer](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Temeldeki değeri döndürür veya oluşturur bir `System.NullReferenceException` değer ise `None`.|

## <a name="option-module"></a>Seçenek Modülü

Bir modülü [seçeneği](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), seçenekleri işlemleri kullanışlı işlevler içerir. Bazı işlevler özelliklerini işlevselliğini yineleyin ancak bir işlev gerekmesi halinde bağlamlarda yararlıdır. [Option.isSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) ve [Option.isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) seçeneği bir değer tutuyor olup olmadığını test iki modül işlevler. [Option.get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) varsa değeri alır. Hiçbir değer yoksa, onu oluşturur `System.ArgumentException`.

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) işlevi bir değer ise bu işlev değerine göre yürütür. İşlev tam olarak bir bağımsız değişken almalıdır ve parametre türünü seçenek türü olmalıdır. İşlev dönüş değeri başka bir seçenek türüdür.

İçin seçenek modülüne listeler, diziler, dizileri ve diğer koleksiyon türleri için kullanılabilir olan işlevlerin karşılık gelen işlevleri de içerir. Bu işlevler dahil [ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622), [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99), [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb), [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), ve [ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876). Bu işlevler, sıfır veya bir öğe koleksiyonunu gibi kullanılacak seçeneklerini etkinleştirin. Daha fazla bilgi ve örnekler için toplama işlevleri bkz [listeler](lists.md).

## <a name="converting-to-other-types"></a>Diğer türlerine dönüştürme

Seçenekleri, liste veya diziler için dönüştürülebilir. Bir seçenek ya da bu veri yapılarının dönüştürüldüğünde, sonuçta elde edilen veri yapısı sıfır veya bir öğeye sahip. İsteğe bağlı bir diziye dönüştürülecek kullanın [ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). İsteğe bağlı bir listeye dönüştürmek için [ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
