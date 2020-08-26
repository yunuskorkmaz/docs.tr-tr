---
title: Kayıtlar
description: 'F # kayıtlarının, isteğe bağlı olarak, adlandırılmış değerlerin basit toplamlarını nasıl temsil ettiğini öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: a72c0f15b58407e7d759e2fb5a1b35a7fc0d29e3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812360"
---
# <a name="records"></a>Kayıtlar

Kayıtlar, isteğe bağlı olarak Üyeler ile adlandırılmış değerlerin basit toplamlarını temsil eder. Bunlar, yapılar veya başvuru türleri olabilir.  Bunlar varsayılan olarak başvuru türlerdir.

## <a name="syntax"></a>Syntax

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *TypeName* kayıt türünün adı, *Label1* ve *Etiket 2* değerleri *Etiketler*olarak adlandırılır ve *Type1* ve *type2* bu değerlerin türleridir. *üye listesi* , türü için isteğe bağlı üyelerin listesidir.  `[<Struct>]`Özniteliği, başvuru türü olan bir kayıt yerine bir struct kaydı oluşturmak için kullanabilirsiniz.

Bazı örnekler aşağıda verilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Her etiket ayrı bir satırda olduğunda, noktalı virgül isteğe bağlıdır.

*Kayıt ifadeleri*olarak bilinen ifadelerde değerler belirleyebilirsiniz. Derleyici, kullanılan etiketlerden tür kullanır (Etiketler diğer kayıt türlerinden yeterince farklı olursa). Küme ayraçları ({}) kayıt ifadesini kapsar. Aşağıdaki kod, etiketleriyle üç float öğesi olan bir kaydı Başlatan bir kayıt ifadesi gösterir `x` `y` `z` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Aynı etiketlere de sahip olan başka bir tür varsa, kısaltılmış biçimi kullanmayın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

En son tanımlanan türün etiketleri, önceden tanımlanmış olan türden önceliklidir, bu nedenle önceki örnekte olduğu gibi `mypoint3D` algılanır `Point3D` . Kayıt türünü aşağıdaki kodda olduğu gibi açıkça belirtebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Yöntemler, sınıf türleri için olduğu gibi kayıt türleri için tanımlanabilir.

## <a name="creating-records-by-using-record-expressions"></a>Kayıt Ifadeleri kullanarak kayıt oluşturma

Kayıtları kayıtta tanımlanan etiketleri kullanarak başlatabilirsiniz. Bunu yapan bir ifade, *kayıt ifadesi*olarak adlandırılır. Kayıt ifadesini kapsamak ve noktalı virgülü sınırlayıcı olarak kullanmak için küme ayraçları kullanın.

Aşağıdaki örnek, bir kaydın nasıl oluşturulacağını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Kayıt ifadesindeki son alandan sonra tür tanımında bulunan noktalı virgül, alanların tümünün tek bir satırda olup olmamasından bağımsız olarak isteğe bağlıdır.

Bir kayıt oluşturduğunuzda, her bir alan için değerler sağlamanız gerekir. Herhangi bir alan için başlatma ifadesindeki diğer alanların değerlerine başvuramaz.

Aşağıdaki kodda, türü `myRecord2` alanların adlarından algılanır. İsteğe bağlı olarak, tür adını açık şekilde belirtebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Başka bir kayıt oluşturma biçimi, var olan bir kaydı kopyalamanız gerektiğinde ve muhtemelen alan değerlerinden bazılarını değiştirebilmeniz yararlı olabilir. Aşağıdaki kod satırı bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Kayıt ifadesinin bu formu, *Copy ve Update Record ifadesi*olarak adlandırılır.

Kayıtlar varsayılan olarak sabittir; Ancak, bir Kopyala ve Güncelleştir ifadesi kullanarak, değiştirilmiş kayıtları kolayca oluşturabilirsiniz. Ayrıca, açıkça kesilebilir bir alan belirtebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

DefaultValue özniteliğini kayıt alanları ile kullanmayın. Daha iyi bir yaklaşım, varsayılan değerlere başlatılan alanlara sahip kayıtların varsayılan örneklerini tanımlamak ve sonra varsayılan değerlerden farklı olan alanları ayarlamak için bir Kopyala ve Güncelleştir ifadesi kullanmaktır.

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

## <a name="creating-mutually-recursive-records"></a>Birbirini dışlayan özyinelemeli kayıtlar oluşturma

Kayıt oluştururken, daha sonra tanımlamak istediğiniz başka bir türe bağlı olmasını isteyebilirsiniz. Bu, karşılıklı özyinelemeli olacak kayıt türlerini tanımlamadığınız takdirde bir derleme hatasıdır.

Birbirini dışlayan özyinelemeli kayıtların tanımlanması `and` anahtar sözcükle yapılır. Bu, 2 veya daha fazla kayıt türünü birbirine bağlamanızı sağlar.

Örneğin, aşağıdaki kod bir `Person` ve `Address` türünü birbirini dışlayan özyinelemeli olarak tanımlar:

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
    PostCode: string
    Occupant: Person }
```

Önceki örneği anahtar sözcüğü olmadan tanımlamanız durumunda `and` derlenmez. `and`Anahtar sözcüğü, karşılıklı özyinelemeli tanımlar için gereklidir.

## <a name="pattern-matching-with-records"></a>Kayıtlarla eşleşen desenler

Kayıtlar, model eşleştirme ile kullanılabilir. Bazı alanları açık bir şekilde belirtebilir ve bir eşleşme gerçekleştiğinde atanacak diğer alanlar için değişken sağlayabilirsiniz. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Bu kodun çıktısı aşağıdaki gibidir.

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a>Kayıtlar ve Üyeler

Kayıtlar üzerinde, sınıflar ile yaptığınız gibi Üyeler belirtebilirsiniz. Alanlar için destek yoktur. Yaygın bir yaklaşım, `Default` kolay kayıt oluşturma için statik bir üye tanımlamaktır:

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

Kendi kendine tanımlayıcı kullanırsanız, bu tanımlayıcı, üyesini çağıran kaydın örneğine başvurur:

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123 }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a>Kayıtlar ve sınıflar arasındaki farklılıklar

Kayıt alanları, otomatik olarak özellikler olarak sunuldukları sınıflardan farklıdır ve kayıtların oluşturulması ve kopyalanması halinde kullanılır. Kayıt oluşturma, sınıf yapılamadan da farklıdır. Bir kayıt türünde, bir Oluşturucu tanımlayamazsınız. Bunun yerine, bu konuda açıklanan yapım sözdizimi geçerlidir. Sınıfların Oluşturucu parametreleri, alanları ve özellikleri arasında doğrudan bir ilişkisi yoktur.

Birleşim ve yapı türleri gibi, kayıtların yapısal eşitlik semantiği vardır. Sınıflarda başvuru eşitlik semantiği vardır. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Bu kodun çıktısı aşağıdaki gibidir:

```console
The records are equal.
```

Aynı kodu sınıflarla yazarsanız, iki değer yığında iki nesneyi temsil ettiğinden ve yalnızca adresler karşılaştırılacağından (sınıf türü yöntemi geçersiz kılmadığı takdirde), iki sınıf nesnesi eşit değildir `System.Object.Equals` .

Kayıtlar için başvuru eşitlik gerekiyorsa, `[<ReferenceEquality>]` kaydın üzerine özniteliği ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Türleri](fsharp-types.md)
- [Sınıflar](classes.md)
- [F # dil başvurusu](index.md)
- [Başvuru-eşitlik](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-referenceequalityattribute.html)
- [Model eşleştirme](pattern-matching.md)
