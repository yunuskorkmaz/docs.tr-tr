---
title: "Kayıtlar (F#)"
description: "F # kayıtları üyeleri isteğe bağlı olarak adlandırılmış değerler basit toplamalar nasıl temsil öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: 478ab74ad32cc6e53daffd1bd6229729149d2a1e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="records"></a>Kayıtlar

Kayıtları üyeleri isteğe bağlı olarak adlandırılmış değerler basit toplamalar temsil eder.  F # 4.1 ile başlayarak, bunlar yapılar veya reference türü ya da olabilir.  Başvuru türleri varsayılan olarak oldukları.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde *typename* kayıt türünün adı *label1* ve *label2* adları olarak adlandırılan değerlerin *etiketleri*, ve *type1* ve *type2* bu değerleri türleridir. *üye listesi* üye türü için isteğe bağlı bir listedir.  Kullanabileceğiniz `[<Struct>]` bir başvuru türü olan bir kaydı yerine bir yapı kaydı oluşturmak için öznitelik.

Bazı örnekler verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Her etiket ayrı bir satırda, noktalı virgülü isteğe bağlı olur.

Değerleri olarak bilinen ifadelerde belirleyebileceğiniz *kayıt ifadeleri*. Derleyici (etiketleri yeterince farklı diğer kayıt türleri olanlardan varsa) kullanılan etiketler türünden oluşturur. Kaşlı ayraçlar kayıt deyimi alın. Aşağıdaki kod etiketlerle üç float öğeleri içeren bir kayıt başlatır kayıt ifade gösterir `x`, `y` ve `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Olabilir, ayrıca aynı etikete sahip başka bir tür kısaltılmış şekilde kullanmayın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

En son bildirilen etiketleri olanlar daha önce bildirilen bir türe önceliklidir önceki örnekte, bunu `mypoint3D` olmasını olayla `Point3D`. Aşağıdaki kod olduğu gibi kayıt türü açık olarak belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Yöntemleri, yalnızca sınıf türleri için kayıt türleri için tanımlanabilir.

## <a name="creating-records-by-using-record-expressions"></a>Kayıt ifadeler kullanarak kayıtları oluşturma
Kayıtları kayıtta tanımlı etiketleri kullanarak başlatabilirsiniz. Bu bir ifade olarak adlandırılır bir *kayıt ifade*. Kayıt deyimi alın ve noktalı virgül ayırıcı olarak kullanmak için ayraç kullanın.

Aşağıdaki örnek, bir kayıt oluşturmak gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Kayıt ifadesinde ve tür tanımı son alanından sonra noktalı alanların tümünü tek bir satırı içinde olup bağımsız olarak isteğe bağlıdır.

Bir kayıt oluşturduğunuzda, her bir alan için değer sağlamanız gerekir. Herhangi bir alan için başlatma ifadedeki diğer alanların değerlerini başvuramaz.

Aşağıdaki kodda, türü `myRecord2` alanları adlarından algılanır. İsteğe bağlı olarak, tür adı açıkça belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Varolan bir kaydı kopyalayın ve büyük olasılıkla bazı alan değerleri değiştirmek zorunda kayıt yapım başka bir formu kullanışlı olabilir. Aşağıdaki kod satırını bunu göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Bu form kayıt ifadesinin adlı *kopyalama ve güncelleştirme kayıt ifade*.

Varsayılan olarak değişmez kayıtlarıdır; Ancak, kopyalama ve güncelleştirme ifade kullanarak değiştirilen kayıtları kolayca oluşturabilirsiniz. Aynı zamanda açıkça değişebilir bir alan belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

DefaultValue özniteliği kaydı alanlarla kullanmayın. Daha iyi bir kayıt başlatılmış alanları ile varsayılan örnekleri için varsayılan değerleri tanımlayın ve ardından bir kopyasını kullanın ve varsayılan değerlerinden farklı alanları ayarlamak için kayıt ifade güncelleştirmek için yaklaşımdır.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a>Desen eşleştirme kayıtlarıyla
Kayıtları desen eşleştirme ile kullanılabilir. Bazı alanlar açıkça belirtmek ve bir eşleşme oluştuğunda atanacak diğer alanlar için değişkenleri sağlayın. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Bu kod çıkışı aşağıdaki gibidir.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Kayıtlar ve sınıflar arasındaki farklar
Kayıt alanları otomatik olarak bir özellik olarak sunulan ve oluşturmada kullanılan ve kayıtların kopyalama sınıflardan farklılık gösterir. Kayıt oluşturma da sınıfı yapım farklıdır. Bir kayıt türü bir oluşturucu tanımlanamıyor. Bunun yerine, bu konuda açıklanan yapım sözdizimi geçerlidir. Sınıfları Oluşturucusu parametreleri, alanları ve özellikleri arasında doğrudan hiçbir ilişki sahiptir.

Birleşim ve yapı türleri gibi kayıtları yapısal eşitlik semantiklerine sahip. Sınıfları sahip referans eşitlik semantiği. Aşağıdaki kod örneğinde bu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Sınıfları içeren aynı kodu yazarsanız, iki sınıf nesnelerine çünkü iki değer yığında iki nesneleri temsil eder ve yalnızca adresleri karşılaştırıldığında eşit olacaktır (sınıf türü geçersiz kılmadıkça `System.Object.Equals` yöntemi).

Eşitlik kayıtları için referans olursa öznitelik Ekle `[<ReferenceEquality>]` kaydı üstünde.

## <a name="see-also"></a>Ayrıca Bkz.
[F# Türleri](fsharp-types.md)

[Sınıflar](classes.md)

[F# Dili Başvurusu](index.md)

[Başvuru eşitliği](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[Desen Eşleştirme](pattern-matching.md)
