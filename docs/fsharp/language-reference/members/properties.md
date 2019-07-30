---
title: Özellikler
description: Bir nesneyle F# ilişkili değerleri temsil eden Üyeler olan özellikler hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: c202927fd0022e042703640cd55fb632c7e36068
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627417"
---
# <a name="properties"></a>Özellikler

*Özellikler* , bir nesneyle ilişkili değerleri temsil eden üyeleridir.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Açıklamalar

Özellikler, nesne odaklı programlamada, nesne örnekleriyle ilişkili verileri temsil eden veya statik özellikler için, türü ile birlikte "" a "ilişkisini temsil eder.

Özelliği için temel alınan değeri (yedekleme deposu olarak da bilinir) açıkça belirtmek isteyip istemediğinize veya derleyicinin sizin için otomatik olarak yedekleme deposunu oluşturmasına izin vermek istiyorsanız, özellikleri iki şekilde bildirebilirsiniz. Genellikle, özelliğin önemsiz olmayan bir uygulamasına sahip olması ve özelliğin bir değer ya da değişken için yalnızca basit bir sarmalayıcı olması durumunda, otomatik olarak daha açık bir yöntem kullanmanız gerekir. Bir özelliği açıkça bildirmek için `member` anahtar sözcüğünü kullanın. Bu bildirim temelli söz dizimi, `get` sonra da *erişimcileri*adlı ve `set` yöntemlerini belirten sözdizimi tarafından izlenir. Sözdizimi bölümünde gösterilen açık sözdiziminin çeşitli biçimleri, okuma/yazma, salt okunurdur ve salt yazılır özellikler için kullanılır. Salt okuma özellikleri için yalnızca bir `get` yöntemi tanımlarsınız; salt yazılır özellikler için yalnızca bir `set` yöntemi tanımlayın. Bir özellik hem hem `get` `set` de erişimcileri olduğunda, alternatif sözdizimi, aşağıdaki kodda gösterildiği gibi her erişimci için farklı öznitelikler ve erişilebilirlik değiştiricileri belirtmenizi sağlar.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Hem `get` hem de `set` yönteminesahip`set` olan okuma/yazma özellikleri için, sırası vetersalınabilir.`get` Alternatif olarak, `get` yalnızca için gösterilen söz dizimini ve yalnızca için `set` gösterilen sözdizimini birleştirilmiş sözdizimini kullanmak yerine sağlayabilirsiniz. Bunu yapmak, tek yapmanız gereken bir şey ise, `get` her `set` şeyi veya yöntemi açıklamayı daha kolay hale getirir. Birleşik söz dizimini kullanmanın bu alternatifi aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Özellikler için verileri tutan özel değerler *Mağaza yedekleme*olarak adlandırılır. Derleyicinin yedekleme deposunu otomatik olarak oluşturmasını sağlamak için, anahtar sözcüklerini `member val`kullanın, kendi kendine tanımlayıcıyı atlayın ve sonra özelliği başlatmak için bir ifade sağlayın. Özelliği değiştirilebilir ise, dahil `with get, set`edin. Örneğin, aşağıdaki sınıf türü otomatik olarak uygulanan iki özelliği içerir. `Property1`salt okunurdur ve birincil oluşturucuya sunulan bağımsız değişkene başlatılır ve `Property2` boş bir dizeye başlatılan ayarlanabilir bir özelliktir:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Otomatik uygulanan özellikler bir tür başlatmanın bir parçasıdır. bu nedenle, bir tür tanımındaki bağlamalar ve `let` `do` bağlamalar gibi diğer üye tanımlarından önce dahil olmaları gerekir. Otomatik olarak uygulanan bir özelliği Başlatan ifadenin, her özelliğe erişildiğinde değil, yalnızca başlatma sonrasında değerlendirildiğini unutmayın. Bu davranış, açıkça uygulanan bir özelliğin davranışının aksine. Bunun ne kadar etkili olduğu, bu özellikleri başlatacak kodun bir sınıfın oluşturucusuna eklendiği şeydir. Bu farkı gösteren aşağıdaki kodu göz önünde bulundurun:

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**Output**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

Önceki kodun çıktısı, tekrar tekrar çağrıldığında,, her çağrıldığında açıkça IProperty değiştiği zaman, tekrar tekrar çağrıldığında, tekrar özelliğinin değerinin değiştirilmemiş olduğunu gösterir. Bu, açık özelliğin alıcı yöntemi olduğu gibi, otomatik olarak uygulanan bir özelliğin ifadesinin her seferinde değerlendirilmeyeceğini gösterir.

>[!WARNING]
>Otomatik olarak uygulanan özelliklerin başlatılmasına göre iyi çalışmayan temel sınıf`System.Data.Entity`oluşturucuları içinde özel işlemler gerçekleştiren Entity Framework () gibi bazı kitaplıklar vardır. Bu durumlarda, açık özellikleri kullanmayı deneyin.

Özellikler sınıfların, yapıların, ayrılmış birleşimlerin, kayıtların, arabirimlerin ve tür uzantılarının üyeleri olabilir ve ayrıca nesne ifadelerinde de tanımlanabilir.

Öznitelikler, özelliklere uygulanabilir. Bir özelliğe öznitelik uygulamak için, özelliğinden önce özniteliği ayrı bir satıra yazın. Daha fazla bilgi için bkz. [öznitelikler](../attributes.md).

Varsayılan olarak, Özellikler geneldir. Erişilebilirlik değiştiricileri de özelliklere uygulanabilir. Bir erişilebilirlik değiştiricisi uygulamak için `get` , hem hem de `set` yöntemlerine uygulanacaksa, özelliğin adından hemen önce ekleyin; farklı erişilebilirlik ise, `get` ve `set` anahtar sözcüklerinden önce ekleyin Her erişimci için gereklidir. *Erişilebilirlik-değiştirici* aşağıdakilerden biri olabilir: `public`, `private`, `internal`. Daha fazla bilgi için bkz. [Access Control](../access-control.md).

Özellik uygulamaları her bir özelliğe erişildiğinde yürütülür.

## <a name="static-and-instance-properties"></a>Statik ve örnek özellikleri

Özellikler statik veya örnek özellikleri olabilir. Statik özellikler bir örnek olmadan çağrılabilir ve ayrı nesneler ile değil, türle ilişkili değerler için kullanılır. Statik özellikler için, kendi kendine tanımlayıcıyı atlayın. Örnek özellikleri için kendi kendine tanımlayıcı gereklidir.

Aşağıdaki statik özellik tanımı, özelliği için yedekleme deposu olan bir statik alana `myStaticValue` sahip olduğunuz bir senaryoyu temel alır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Özellikler ayrıca dizi benzeri olabilir, bu durumda *dizinlenmiş özellikler*olarak adlandırılırlar. Daha fazla bilgi için bkz. [dizinli Özellikler](indexed-properties.md).

## <a name="type-annotation-for-properties"></a>Özellikler için tür ek açıklaması

Çoğu durumda, derleyicinin bir özelliğin türünü, yedekleme deposunun türünden çıkarması için yeterli bilgi vardır, ancak tür ek açıklaması ekleyerek türü açıkça ayarlayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Özellik kümesi erişimcileri kullanma

İşlecini kullanarak erişimciler sağlayan `set` özellikleri ayarlayabilirsiniz. `<-`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Çıktı **20**' dir.

## <a name="abstract-properties"></a>Soyut Özellikler

Özellikler soyut olabilir. Metotlarda olduğu gibi `abstract` , özelliği ile ilişkili bir sanal dağıtım olduğu anlamına gelir. Soyut Özellikler gerçekten soyut olabilir, diğer bir deyişle, aynı sınıfta bir tanım olmadan. Böyle bir özelliği içeren sınıf bu nedenle soyut bir sınıftır. Alternatif olarak, soyut bir özelliğin sanal olduğu anlamına gelir ve bu durumda bir tanım aynı sınıfta bulunmalıdır. Soyut özelliklerin özel olmaması gerektiğini ve bir erişimcinin soyut olduğunu, diğerinin de soyut olması gerektiğini unutmayın. Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut sınıflar](../abstract-classes.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [Yöntemler](methods.md)
