---
title: Özellikler (F#)
description: 'Bir nesneyle ilişkili değerlerini temsil eden üyeleri olan F # özellikleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50043653"
---
# <a name="properties"></a>Özellikler

*Özellikleri* bir nesneyle ilişkili değerlerini temsil eden üyeleridir.

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

Özellikleri temsil eder "olan bir" nesne örnekleri ile veya türü ile statik özellikler ilişkili verileri temsil eden nesne yönelimli programlama, ilişkide.

Özellikleri veya (yedekleme deposu olarak da bilinir) temel alan değeri özellik için açıkça belirtmek istediğiniz yedekleme deposu sizin için otomatik olarak oluşturmak derleyicinin izin vermek isteyip istemediğinizi bağlı olarak iki yolla bildirebilirsiniz. Genellikle, özelliği bir değer ya da değişken için yalnızca basit bir sarmalayıcı olduğunda Önemsiz olmayan bir uygulama özelliği varsa, daha açık şekilde ve otomatik bir yolu kullanması gerekir. Bir özelliği açıkça bildirmek için kullanın `member` anahtar sözcüğü. Bu bildirim temelli söz dizimi belirten sözdizimi tarafından izlenir `get` ve `set` yöntemleri olarak da adlandırılan, *erişimcileri*. Çeşitli türleri söz dizimi bölümünde açık sözdizimini, okuma/yazma, salt okunur ve salt yazılır özellikler için kullanılır. Salt okunur özellikler, yalnızca, tanımladığınız bir `get` yöntemi; salt yazılır özellikler yalnızca tanımlamak bir `set` yöntemi. Her ikisi de bir özelliğe sahip olduğunda dikkat `get` ve `set` erişimcileri, farklı bir sözdizimi öznitelikleri ve aşağıdaki kodda gösterildiği gibi her bir erişimci farklı erişilebilirlik değiştiricileri belirtmenize imkan tanır.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Her ikisi de okuma/yazma özellikleri için bir `get` ve `set` yöntemi, sırası `get` ve `set` ters çevrilebilir. Alternatif olarak, için sözdizimini sağlayabilir `get` yalnızca ve için sözdizimini `set` birleştirilmiş sözdizimi yerine yalnızca. Bunu kolaylaştırır, tek tek yorum `get` veya `set` yöntemi ise, bir şey yapmanız gerekebilir. Birleşik söz dizimini kullanarak bu alternatif aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Özel özellikler için verileri çağrılır, tutulan değerler *depolarını yedekleme*. Derleyicinin yedekleme deposu otomatik olarak oluşturmak için anahtar sözcükleri kullanın `member val`, kendi kendine tanımlayıcısı çıkarın ve ardından özelliğini başlatmak için bir ifade girin. Özelliği değişebilir olmasını içermesi `with get, set`. Örneğin, aşağıdaki sınıf türü iki otomatik olarak uygulanan özellikler içerir. `Property1` salt okunur ve birincil oluşturucuya, sağlanan bağımsız değişken olarak başlatılır ve `Property2` boş dize olarak başlatılmış bir ayarlanabilir özelliği:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Otomatik olarak uygulanan özellikler, bunlar diğer üye tanımları önce tıpkı dahil edilmesi için başlatma türünün bir parçası olan `let` bağlamaları ve `do` bağlamaları bir tür tanımı. Otomatik olarak uygulanan bir özellik başlatan ifade yalnızca ve başlatma sonrasında özelliği erişilmeyen her zaman değerlendirilir unutmayın. Açıkça uygulanan bir özellik aksine bu davranışı davranıştır. Ne bu etkili bir şekilde, bu özellikleri başlatmaya yarayacak koda anlamına gelir, bir sınıf oluşturucusuna eklenir. Bu fark gösteren aşağıdaki kodu göz önünde bulundurun:

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

Önceki kodun çıktısı her çağrıldığında ExplicitProperty değiştirir ancak AutoProperty değerini tekrar tekrar çağrıldığında değiştirilmemiş olduğunu gösterir. Açık özelliği için alıcı yöntemi olduğundan her zaman otomatik olarak uygulanan bir özellik için ifade değerlendirilmez gösterir.

>[!WARNING]
Entity Framework gibi bazı kitaplıklar vardır (`System.Data.Entity`) otomatik olarak uygulanan özellikler başlatma ile düzgün çalışmayan bir temel sınıf oluşturucuları, özel işlemler gerçekleştiren. Bu gibi durumlarda, açık özelliklerini kullanmayı deneyin.

Özellikler, sınıflar, yapılar, ayrılmış birleşimler, kayıtları, arabirimleri ve tür uzantıları üyesi olabilir ve nesne ifadelerinde da tanımlanabilir.

Öznitelikleri özelliklerine uygulanabilir. Bir özellik için bir öznitelik uygulamak için önce özelliği ayrı bir satırda öznitelik yazın. Daha fazla bilgi için [öznitelikleri](../attributes.md).

Varsayılan olarak, özellikleri ortaktır. Erişilebilirlik değiştiricileri özellikleri için de uygulanabilir. Her ikisini de uygulamak için kullanılacaksa bir erişilebilirlik değiştiricisine uygulamak için özelliğin adı hemen önce ekleme `get` ve `set` yöntemleri; önce ekleme `get` ve `set` farklı erişilebilirlik ise anahtar sözcükleri Her erişimcisi için gereklidir. *Erişilebilirlik değiştiricisi* aşağıdakilerden biri olabilir: `public`, `private`, `internal`. Daha fazla bilgi için [erişim denetimi](../access-control.md).

Özellik uygulamaları bir özelliğine erişinceye her zaman yürütülür.

## <a name="static-and-instance-properties"></a>Statik ve örnek özellikleri

Özellikler, statik veya örnek özellikleri. Statik özellikler örneği olmadan çağrılabilir ve ayrı ayrı nesneleri ile değil, türü ile ilişkili değerler için kullanılır. Statik özellikler için kendi kendine tanımlayıcısı yok sayın. Kendi kendine tanımlayıcı, örnek özellikleri için gereklidir.

Aşağıdaki statik özellik tanımı, statik bir alana sahip bir senaryoya bağlıdır `myStaticValue` özelliği için diğer bir deyişle yedekleme deposu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Özellikleri de olabilir dizi benzeri, bu durumda adlı *özellikleri dizine*. Daha fazla bilgi için [dizini oluşturulmamış Özellikler](indexed-properties.md).

## <a name="type-annotation-for-properties"></a>Özelliklerin tür ek açıklaması

Çoğu durumda, derleyici yedekleme deposu türünden bir özelliğinin türünü çıkarsamak için yeterli bilgiye sahip, ancak bir tür ek açıklamasına ekleyerek türü açıkça ayarlayabilirsiniz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Set erişimcilerine özelliğini kullanma

Sağlayan özellikleri ayarlayabilirsiniz `set` kullanarak erişimcileri `<-` işleci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Çıktı **20**.

## <a name="abstract-properties"></a>Soyut Özellikler

Özellikler, soyut olabilir. Yöntemleriyle yönteminde olduğu gibi `abstract` yalnızca özellikle ilişkili bir sanal dağıtım olduğunu gösterir. Diğer bir deyişle, soyut özellikler aynı sınıftaki bir tanımı olmadan tamamen soyut olabilir. Böyle bir özellik içeren sınıf bu nedenle bir soyut sınıftır. Alternatif olarak, Özet, yalnızca bir sanal bir özelliktir ve bu durumda, bir tanımı aynı sınıf içinde bulunmalıdır gelebilir. Soyut özellikler özel olmamalıdır ve bir erişimci soyut ise, diğeri de soyut olmalıdır unutmayın. Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut sınıflar](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [Yöntemler](methods.md)
