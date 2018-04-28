---
title: Özellikler (F#)
description: 'Bir nesneyle ilişkilendirilmiş değerlerini temsil eden üyeleri olan F # özellikleri hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 6cad5d0e32958374e080f9b8046f7eb73b6bf615
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="properties"></a>Özellikler

*Özellikler* bir nesneyle ilişkilendirilmiş değerlerini temsil eden üyeleridir.


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
Özelliklerini temsil eder "sahip bir" nesne örnekleri ile veya türüyle statik özellikler için ilişkili verileri temsil eden nesne odaklı programlama ilişkisinde.

Özellikler (yedekleme deposu olarak da adlandırılır) temel alınan değer özelliği için açıkça belirtmek istediğiniz veya yedekleme deposu sizin için otomatik olarak oluşturmak derleyici izin vermek istediğiniz bağlı olarak iki yolla bildirebilirsiniz. Genellikle, özelliği yalnızca bir değer veya değişken için basit bir sarmalayıcı olduğunda daha açık şekilde Önemsiz olmayan bir uygulama özelliğine sahipse ve otomatik şekilde kullanması gerekir. Bir özellik açıkça bildirmek için kullanın `member` anahtar sözcüğü. Bu tanımlayıcı sözdizimi belirten sözdizimi tarafından izlenir `get` ve `set` olarak da adlandırılan yöntemleri *erişimciler*. Çeşitli tür sözdizimi bölümünde gösterilen açık sözdizimi okuma/yazma, salt okunur ve salt yazılır özellikler için kullanılır. Salt okunur özellikler yalnızca tanımladığınız bir `get` yöntemi; salt yazılır özellikler yalnızca tanımlayan bir `set` yöntemi. Hem bir özelliğe sahip olduğunda unutmayın `get` ve `set` erişimciler, alternatif bir sözdizimi öznitelikleri ve aşağıdaki kodda gösterildiği gibi her erişimci için farklı erişilebilirlik değiştiricileri belirtmenize olanak sağlar.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Hem de okuma/yazma özellikleri için bir `get` ve `set` yöntemi, sırasını `get` ve `set` ters çevrilebilir. Alternatif olarak, gösterilen sözdizimi sağlayabilir `get` yalnızca ve için sözdizimini `set` birleşik sözdizimi yerine yalnızca. Bunun yapılması kolaylaştırır açıklamaya tek tek çıkışı `get` veya `set` yöntemi ise, bir şey yapmanız gerekebilir. Bu alternatif birleşik sözdizimini kullanarak aşağıdaki kodda gösterilir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Özel özellikler için verileri çağrılır ayrı tutmayı değerleri *depolarını yedekleme*. Derleyicinin yedekleme deposu otomatik olarak oluşturmak için anahtar sözcüklerini kullanın `member val`, kendi kendine tanımlayıcı çıkarın ve ardından özelliği başlatmak için bir ifade girin. Özelliği değişebilir olması gerekiyorsa dahil `with get, set`. Örneğin, aşağıdaki sınıf türü iki otomatik olarak uygulanan özellikler içerir. `Property1` salt okunur ve birincil oluşturucuya sağlanan değişkeni başlatılır ve `Property2` boş bir dize olarak başlatılan bir özelliğidir ayarlanabilir:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Otomatik uygulanan özellikler bunlar diğer üye tanımları önce tıpkı dahil edilmesi için bir tür başlatma parçası olan `let` bağlamalar ve `do` tür tanımında bağlar. Otomatik olarak uygulanan bir özellik başlatır ifade başlatma sırasında ve değil özelliği her erişildiğinde yalnızca değerlendirilir unutmayın. Açıkça gerçekleştirilen özellik aksine bu davranış davranıştır. Ne bu etkili bir şekilde, bu özellikleri başlatmak için kod olduğu anlamına gelir, bir sınıfın oluşturucuya eklenir. Bu farklılık gösteren aşağıdaki kodu göz önünde bulundurun:

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

Önceki kod çıkışı ExplicitProperty her çağrıldığında değişir ancak AutoProperty değerini tekrar tekrar çağrıldığında değiştirilmemiş olduğunu gösterir. Açık özellik alıcısı yöntemi olarak ifade otomatik olarak uygulanan bir özellik için her zaman değerlendirilmez gösterir.


>[!WARNING]
Entity Framework gibi bazı kitaplığı (`System.Data.Entity`), özel işlemi gerçekleştirir temel sınıf Yapıcılardaki de otomatik olarak uygulanan özellikler başlatma ile çalışmaz. Bu durumlarda, açık özelliklerini kullanmayı deneyin.

Özellikler, sınıflar, yapılar, ayrılmış birleşimler, kayıtları, arabirimler ve tür uzantıları üyesi olabilir ve nesne ifadelerde de tanımlanabilir.

Öznitelikleri özelliklerine uygulanabilir. Öznitelik bir özelliğe uygulamak için ayrı bir satırda özelliği önce öznitelik yazma. Daha fazla bilgi için bkz: [öznitelikleri](../attributes.md).

Varsayılan olarak, ortak özelliklerdir. Erişilebilirlik değiştiricileri özelliklerine de uygulanabilir. Her ikisini de uygulamak için istediyseniz erişim değiştiricisi uygulamak için bu özelliğin adı hemen önce ekleyin `get` ve `set` yöntemleri; önce eklemek `get` ve `set` farklı erişilebilirlik ise anahtar sözcükler her erişimci için gereklidir. *Erişim değiştiricisi* şunlardan biri olabilir: `public`, `private`, `internal`. Daha fazla bilgi için bkz: [erişim denetimi](../access-control.md).

Özellik uygulamaları bir özelliği her erişildiğinde yürütülür.


## <a name="static-and-instance-properties"></a>Statik ve örnek özellikleri
Özellikler, statik ya da Özellikler örneği. Statik özellikler örneği çağrılabilir ve türü değil ayrı ayrı nesneleri ile ilişkili değerleri için kullanılır. Statik özellikler için kendi kendine tanımlayıcısı yok sayın. Kendi kendine tanımlayıcısı örneği özellikleri için gereklidir.

Aşağıdaki statik özellik tanımını statik bir alana sahip bir senaryo tabanlı `myStaticValue` özelliği için diğer bir deyişle yedekleme deposu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Özellikler de olabilir dizi benzeri; bu durumda adlı *özellikleri dizine*. Daha fazla bilgi için bkz: [Dizinli Özellikler](indexed-properties.md).


## <a name="type-annotation-for-properties"></a>Özellikleri için tür ek açıklaması
Çoğu durumda, derleyici tür yedekleme deposu özelliğinden türünü anlamak için yeterli bilgiye sahip, ancak türü ek açıklama ekleyerek türü açıkça ayarlayabilirsiniz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Özelliğini kullanarak set erişimcileri
Sağlayan özellikleri ayarlayabilirsiniz `set` kullanarak erişimciler `<-` işleci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Çıktı **20**.


## <a name="abstract-properties"></a>Soyut Özellikler
Özellikler soyut olabilir. Yöntemleriyle olduğu gibi `abstract` yeni özellik ile ilişkilendirilmiş sanal bir gönderme olduğu anlamına gelir. Diğer bir deyişle, soyut özellikleri aynı sınıf tanımında olmadan gerçekten soyut olabilir. Böyle bir özellik içeren bu nedenle bir Özet sınıf sınıftır. Alternatif olarak, Özet yalnızca bir sanal bir özelliktir ve bu durumda, bir tanım aynı sınıfta bulunmalıdır anlamına gelebilir. Soyut özellikler özel olmamalı ve bir erişimci soyut ise, diğer ayrıca soyut olmalıdır unutmayın. Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut sınıflar](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Ayrıca Bkz.
[Üyeler](index.md)

[Yöntemler](methods.md)
