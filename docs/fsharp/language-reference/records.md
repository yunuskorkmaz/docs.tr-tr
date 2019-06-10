---
title: Kayıtlar
description: Bilgi nasıl F# kayıtları basit toplamalarla üyeleri ile isteğe bağlı olarak adlandırılan değerleri temsil eder.
ms.date: 06/09/2019
ms.openlocfilehash: cfb8de8272b479571119ae4cf91ea1d6fd5db73c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816195"
---
# <a name="records"></a>Kayıtlar

Kayıtları basit toplamalarla üyeleri ile isteğe bağlı olarak adlandırılan değerleri temsil eder. Bunlar, yapılar veya başvuru türleri ya da olabilir.  Bunlar, başvuru türleri varsayılan olarak.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *typename* adı kayıt türü *label1* ve *etiket 2* adları olarak adlandırılan değerleri *etiketleri*, ve *type1* ve *type2* bu değerleri türleridir. *üye listesi* üye türü için isteğe bağlı bir listedir.  Kullanabileceğiniz `[<Struct>]` olan bir başvuru türüdür a kaydı yerine bir yapı kaydı oluşturmak için öznitelik.

Bazı örnekler aşağıda verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Her etiket ayrı bir satırda, noktalı virgül isteğe bağlıdır.

Bilinen ifadelerde değerlerini ayarlayabilirsiniz *kayıt ifadeleri*. Derleyici (etiketler yeterince diğer kayıt türleri olanlardan farklıdır) kullanılıyorsa etiketleri türünden çıkarır. Küme ayraçları ({}) kaydı ifadesi içine alın. Aşağıdaki kod etiketlerle üç float öğeleri içeren bir kayıt başlatan bir kayıt ifadesi gösterir `x`, `y` ve `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Ayrıca aynı etikete sahip başka bir tür olabilir, kısaltılmış kullanmayın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Etiketler en kısa süre önce bildirilen türü, bunlar daha önce bildirilen tür önceliklidir önceki örnekte, bu nedenle `mypoint3D` olmasını çıkarılan `Point3D`. Kayıt türü, aşağıdaki kodda gösterildiği gibi açıkça belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Yöntem, sınıf türleri olduğu gibi kayıt türleri için tanımlanabilir.

## <a name="creating-records-by-using-record-expressions"></a>Kayıt ifadelerini kullanarak kayıtları oluşturma

Kayıt içinde tanımlanan etiketleri kullanarak kayıtları başlatabilirsiniz. Bunu yapan bir ifade olarak belirtilen bir *kayıt ifade*. Kayıt ifadesi içine alın ve noktalı virgül sınırlayıcı olarak kullanmak için ayraç kullanın.

Aşağıdaki örnek, bir kayıt oluşturma işlemi gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Noktalı virgüller sonra kaydı ifadesinde ve tür tanımında son alan, alanların tümünü tek bir satırda olduğundan bağımsız olarak, isteğe bağlıdır.

Bir kayıt oluşturduğunuzda, her bir alan için değer sağlamanız gerekir. Herhangi bir alan için başlatma ifadesini diğer alanların değerlerine başvuruda bulunamaz.

Aşağıdaki kodda, türü `myRecord2` alanlarının adları algılanır. İsteğe bağlı olarak, tür adı açıkça belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Kayıtlardan kopyalayabilir ve büyük olasılıkla bazı alan değerleri değiştirmek olduğunda, başka bir form kayıt oluşturma yararlı olabilir. Aşağıdaki kod satırını bunu göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Bu formu kayıt ifadenin adlı *kopyalama ve güncelleştirme kayıt ifade*.

Varsayılan olarak kayıtları sabittir; Ancak, kopyalama ve güncelleştirme ifade kullanarak değiştirilmiş kayıtlar kolayca oluşturabilirsiniz. Değişebilir bir alan da açıkça belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

DefaultValue özniteliği kayıt alanlarla kullanmayın. Daha iyi bir yaklaşım, kayıt başlatılır alanları ile varsayılan örnekleri için varsayılan değerleri tanımlama ve ardından bir kopyayı kullanın ve varsayılan değerlerden farklı herhangi bir alan ayarlamak için kayıt ifadeyi güncelleştirin sağlamaktır.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a>Karşılıklı özyinelemeli kayıtlar oluşturma

Süre bir kayıt oluştururken, daha sonra tanımlamak için istediğiniz başka bir türüne bağlıdır isteyebilirsiniz. Karşılıklı özyinelemeli olarak kayıt türlerinin tanımlamadığınız sürece bir derleme hatası budur.

Karşılıklı özyinelemeli kayıtları tanımlama ile yapılır `and` anahtar sözcüğü. Bu, 2 veya daha fazla kayıt türü birlikte bağlantı sağlar.

Örneğin, aşağıdaki kodu tanımlayan bir `Person` ve `Address` karşılıklı özyinelemeli olarak türü:

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string }
```

Önceki örnekte olmadan tanımlamak için olsaydı `and` anahtar sözcüğü ve ardından derleme. `and` Karşılıklı özyinelemeli tanımları için anahtar sözcüğü gereklidir.

## <a name="pattern-matching-with-records"></a>Desen eşleştirme ile kayıtları

Kayıtları desen eşleştirme ile kullanılabilir. Bazı alanlar açıkça belirtin ve bir eşleşme olduğunda, atanacak diğer alanlar için değişkenleri belirtin. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Bu kodun çıktısı aşağıdaki gibidir.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Kayıt ve sınıfları arasındaki farklar

Kayıt alanları otomatik olarak bir özellik olarak kullanıma ve kullanılan oluşturma ve kopyalama kayıtların sınıflardan farklılık gösterir. Kayıt oluşturma da sınıfı oluşturma farklıdır. Bir kayıt türü bir oluşturucu tanımlanamıyor. Bunun yerine, bu konuda açıklanan yapım söz dizimi geçerlidir. Oluşturucu parametresi, alanlar ve özellikler arasında hiçbir doğrudan ilişki sınıfları içerir.

Birleşim ve yapı türleri gibi kayıtları yapısal eşitlik semantiklere sahip. Başvuru sınıfları sahip eşitlik semantiği. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Bu kodun çıktısı aşağıdaki gibidir:

```
The records are equal.
```

Sınıflarla aynı kod yazın, iki sınıf nesnelerine çünkü iki değer iki nesne yığını üzerindeki temsil eder ve yalnızca adreslerine kıyasla eşit olacaktır (sınıf türü geçersiz kılmadıkça `System.Object.Equals` yöntemi).

Kayıtlar için eşitlik başvuruyorsa öznitelik Ekle `[<ReferenceEquality>]` yukarıda kaydı.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Türleri](fsharp-types.md)
- [Sınıflar](classes.md)
- [F# Dili Başvurusu](index.md)
- [Başvuru eşitliği](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [Desen Eşleştirme](pattern-matching.md)
