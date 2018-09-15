---
title: Sınıflar (F#)
description: 'F # sınıfları, özellikleri, yöntemleri ve olayları olabilir nesneleri temsil eden türler nasıl olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 71cd713d192d28565e879b79b2fc9e0530e5f841
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45641579"
---
# <a name="classes"></a>Sınıflar

*Sınıflar* özellikleri, yöntemleri ve olayları olabilir nesneleri temsil türleridir.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a>Açıklamalar

Sınıflar, .NET nesne türlerini temel açıklamasını temsil; F # nesne yönelimli programlama destekleyen birincil türü kavramı sınıftır.

Yukarıdaki söz diziminde `type-name` herhangi geçerli bir tanımlayıcıdır. `type-params` İsteğe bağlı bir genel tür parametreleri açıklar. Tür parametresi adlarına ve köşeli ayraçlar içine alınan kısıtlamalar oluşur (`<` ve `>`). Daha fazla bilgi için [genel türler](generics/index.md) ve [kısıtlamaları](generics/constraints.md). `parameter-list` Oluşturucu parametreler açıklanmıştır. İlk erişim değiştiricisi türünü içerir; ikinci birincil oluşturucuya ilgilidir. Her iki durumda da varsayılandır `public`.

Kullanarak bir sınıf için taban sınıf belirtin `inherit` anahtar sözcüğü. Temel sınıf oluşturucusu için parantez içinde bağımsız değişken sağlamalısınız.

Alan veya çalışması kullanarak sınıf için yerel olan değerleri `let` bağlamaları ve genel kuralları izlemelidir `let` bağlar. `do-bindings` Bölüm nesne oluşturma sırasında yürütülen kod içerir.

`member-list` Ek Oluşturucular, örneği ve statik yöntem bildirimleri, arabirim bildirimi, soyut bağlamaları ve özellik ve olay bildirimlerini oluşur. Bunlar [üyeleri](members/index.md).

`identifier` Kullanılan isteğe bağlı `as` anahtar sözcüğü, örnek değişkeni veya tür tanımında türü örneğine başvurmak için kullanılan kendi kendine tanımlayıcısı için bir ad sağlar. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde Self tanımlayıcıları bölümüne bakın.

Anahtar sözcükler `class` ve `end` başlangıç işaretlemek ve tanımının son isteğe bağlı.

İle birlikte birbirine başvuru türleri olan özyinelemeli türleri karşılıklı olarak katılan `and` karşılıklı özyinelemeli işlevler olarak yalnızca anahtar sözcüğü. Örneğin, karşılıklı özyinelemeli türleri bölümüne bakın.

## <a name="constructors"></a>Oluşturucular

Sınıf türünün bir örneği oluşturan kodu oluşturucudur. Diğer .NET dillerinde arkadaşlarınıza kıyasla sınıfları için oluşturucular biraz farklı F #'de çalışır. Bir F # sınıfında var. her zaman birincil oluşturucu bağımsız değişkenleri açıklanır `parameter-list` tür adı ve gövde oluşan aşağıdaki `let` (ve `let rec`) bağlamaları sınıf bildiriminin ve başlangıcında`do`izleyin bağlar. Birincil oluşturucu bağımsız değişkenleri sınıf bildirimi içinde kapsamına dahildir.

Ek oluşturucuları kullanarak ekleyebilirsiniz `new` anahtar sözcüğü gibi bir üye eklemek için:

`new`(`argument-list`) = `constructor-body`

Yeni Oluşturucu gövdesinde, sınıf bildiriminin başında belirtilen birincil Oluşturucu çağırmanız gerekir.

Aşağıdaki örnek bu kavramı gösterir. Aşağıdaki kodda, `MyClass` iki Oluşturucusu vardır, iki bağımsız değişken ve başka bir oluşturucu, alan birincil bir oluşturucu bağımsız değişken olur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>let ve do bağlamaları

`let` Ve `do` bağlamaları bir sınıf tanımı birincil sınıf oluşturucu gövdesinde oluşturur ve bu nedenle çalıştıkları her bir sınıf örneği oluşturulur. Varsa bir `let` bağlamadır bir işlev, ardından bir üye derlenir. Varsa `let` bağlama herhangi bir işlevi veya üye kullanılmayan bir değerdir ve ardından bu oluşturucuya yerel bir değişken derlenir. Aksi takdirde, bu sınıfın bir alana derlenir. `do` İzleyin ifadeleri birincil oluşturucuya derlenir ve her örneği için başlatma kodunu yürütün. Hiçbir ek Oluşturucu her zaman birincil oluşturucusunu çağırın çünkü `let` bağlamaları ve `do` her zaman bağlamaları yürütmek bağımsız olarak Oluşturucu çağrılır.

Tarafından oluşturulan alanlar `let` sınıfının özellikleri ve yöntemleri bağlamaları erişilebilir; statik yöntemler parametre olarak bir örnek değişkeni bile alırsanız ancak bunlar statik yöntemleri, erişilemez. Varsa, kendi kendine tanımlayıcısı kullanılarak erişilemez.

## <a name="self-identifiers"></a>Kendine yönelik tanımlayıcılar

A *kendini tanımlayıcısı* geçerli örneği temsil eden bir addır. Kendine yönelik tanımlayıcılar benzer `this` C# veya C++ anahtar sözcüğü veya `Me` Visual Basic'te. Kendi kendine bir tanımlayıcı, kapsamdaki tüm sınıf tanımı için veya yalnızca tek bir yöntem olarak kendi kendine tanımlayıcısı istemenize bağlı olarak, iki farklı yolla tanımlayabilirsiniz.

Tüm sınıf için kendi kendine bir tanımlayıcı tanımlamak için `as` Oluşturucu parametresi, ayraç sonra anahtar sözcüğü listesinde ve tanımlayıcı adı belirtin.

Yalnızca bir yöntem için kendi kendine bir tanımlayıcı tanımlamak için üye bildiriminde hemen önce yöntem adını ve nokta (.) ayırıcı olarak kendi kendine tanımlayıcı sağlar.

Aşağıdaki kod örneği, bir kendi kendini tanımlayıcı oluşturmanın iki yolu gösterilmektedir. İlk satırda `as` anahtar sözcüğü, kendi kendine tanımlayıcısını tanımlamak için kullanılır. Beşinci satırında, tanımlayıcı `this` kapsamı yöntemi kısıtlıdır kendi kendine bir tanımlayıcı tanımlamak için kullanılan `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

İstediğiniz ancak aksine diğer .NET dillerinde, kendi kendine tanımlayıcı ad verebilirsiniz; adları gibi sınırlı değildir `self`, `Me`, veya `this`.

Kendi kendine tanımlayıcı ile bildirilen `as` kadar anahtar sözcüğü başlatılmadı sonra `let` bağlamaları yürütülür. Bu nedenle, içinde kullanılamaz `let` bağlar. Kendi kendine tanımlayıcıda kullanabileceğiniz `do` bağlamalar bölümü.

## <a name="generic-type-parameters"></a>Genel Tür Parametreleri

Köşeli ayraçlar içine genel tür parametreleri belirtildi (`<` ve `>`), ardından bir tanımlayıcısını tek tırnak işareti biçiminde. Birden fazla genel tür parametreleri virgülle ayrılır. Bildirimi kapsamdadır genel tür parametresidir. Aşağıdaki kod örneği, genel tür parametreleri belirtmek gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Tür bağımsız değişkeni türü kullanıldığında algılanır. Aşağıdaki kodda gösterilen türü diziler dizisidir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Devralma belirtme

`inherit` Yan tümcesi varsa doğrudan temel sınıf tanımlar. F #'ta yalnızca bir doğrudan temel sınıf izin verilir. Bir sınıfın uyguladığı arabirimleri temel sınıflar olarak kabul edilmez. Arabirimler açıklanmıştır [arabirimleri](Interfaces.md) konu.

Dil anahtar sözcüğü kullanarak türetilen sınıfın temel sınıf özellikler ve yöntemler erişebilirsiniz `base` tanımlayıcı olarak ve ardından bir nokta (.) ile üyesinin adı.

Daha fazla bilgi için [devralma](inheritance.md).

## <a name="members-section"></a>Üyeler bölümü

Bu bölümde, statik veya örnek yöntemler, özellikler, arabirim uygulamaları, soyut üyeler, olay bildirimleri ve ek oluşturucular tanımlayabilirsiniz. Let ve bağlamaları Bu bölümde yer alamaz yapın. F # türleri sınıflar yanı sıra çeşitli üyeleri eklenebilir olduğundan, ayrı bir konuda ele alınmıştır [üyeleri](members/index.md).

## <a name="mutually-recursive-types"></a>Karşılıklı özyinelemeli türleri

Döngüsel bir şekilde birbirine başvuru türleri tanımladığınızda, birlikte tür tanımlarını kullanarak dize `and` anahtar sözcüğü. `and` Anahtar sözcüğü değiştirir `type` gösterildiği gibi ilk tanımının dışında tüm anahtar sözcüğü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Çıkış, geçerli dizindeki tüm dosyaları listesidir.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Sınıflar, birleşimler, kayıtlar ve yapıları ne zaman kullanılacağı

Aralarından seçim yapabileceğiniz türleri çeşitli göz önünde bulundurulduğunda, hangi her türü için uygun bir özel durum türünü seçmek için tasarlanmıştır, iyi anlamış olmanız gerekir. Sınıflar, nesne yönelimli programlama bağlamlarda kullanmak için tasarlanmıştır. Nesne yönelimli programlama, .NET Framework için yazılan uygulamaları kullanılan baskın örnektir. F # kodunuzu .NET Framework'ü veya başka bir nesne yönelimli kitaplığı ile yakından çalışmaya sahipse ve özellikle kullanıcı Arabirimi kitaplığı gibi bir nesne yönelimli tür sisteminden genişletmek varsa, büyük olasılıkla uygun sınıflardır.

Size yakın bir tümleştirmede nesne yönelimli kod ile birlikte çalışma değil veya müstakil ve bu nedenle korunan nesne yönelimli kod sık etkileşim uygulamadan kod yazıyorsanız, kayıtları kullanmayı düşünmeniz gerekir ve ayrılmış birleşimler. Tek bir iyi düşünce – çıkış kodu, uygun desen ile birlikte birleşimdir genellikle bir nesne hiyerarşisine daha basit bir alternatif olarak kullanılabilir. Ayrılmış birleşimler hakkında daha fazla bilgi için bkz: [ayırt edici birleşimler](discriminated-unions.md).

Kayıtların sınıfları basit olan avantajı vardır, ancak bir tür taleplerini kendi kolaylığıyla gerçekleştirilebilir aştığında kayıtları uygun değildir. Özel eylemler gerçekleştirebilir ayrı Oluşturucular, gizli alanlar, olmadan ve devralma veya arabirim uygulamaları değerleri temel basit toplamalarla kayıtlardır. Depolanan bir kayıttaki alanları yine de basit bir toplama değerleri, özellikler ve yöntemler gibi üyeleri davranışlarını daha karmaşık hale getirmek için kayıtlara eklenebilir ancak. Kayıt hakkında daha fazla bilgi için bkz: [kayıtları](records.md).

Yapıları da küçük veri Toplamalar için yararlı olan, ancak .NET değer türleridir, sınıflar ve kayıtları bunlar farklı. Sınıfları ve kayıtları .NET başvuru türleridir. Değer türleri değere göre geçirilir, değer türleri ve başvuru türleri semantiği farklıdır. Bu şekilde anlamına gelir. bir parametre olarak geçirilen veya bir işlevden döndürülen bit bit. Bunlar ayrıca yığında depolanmış alternatif olarak, yerine üst nesnenin içinde katıştırılmış bir alan olarak kullanılıyorsa yığında kendi ayrı konumlarda depolanır. Bu nedenle, yığın erişme yükünü bir sorun olduğunda yapıları sık erişilen veriler için uygundur. Yapılar hakkında daha fazla bilgi için bkz: [yapıları](structures.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Üyeler](members/index.md)
- [Devralma](inheritance.md)
- [Arabirimler](interfaces.md)
