---
title: Sınıflar (F#)
description: 'F # sınıflarının özellikleri, yöntemleri ve olayları sahip nesneleri temsil eden türlerin nasıl olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 67164bd9f91c14f465bf05630259ad70cb8d90e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565892"
---
# <a name="classes"></a>Sınıflar

*Sınıfları* özellikleri, yöntemleri ve olayları sahip nesneleri temsil türleridir.


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
Sınıfları .NET nesne türlerini temel açıklamasını temsil eder; sınıf nesne odaklı programlama F #'de destekleyen birincil tür kavramdır.

Yukarıdaki söz diziminde `type-name` geçerli bir tanımlayıcı değil. `type-params` İsteğe bağlı genel tür parametreleri açıklar. Tür parametre adları ve kısıtlamalar açılı ayraç oluşur (`<` ve `>`). Daha fazla bilgi için bkz: [genel türler](generics/index.md) ve [kısıtlamaları](generics/constraints.md). `parameter-list` Oluşturucu parametreleri açıklar. İlk erişim değiştiricisi türü için geçerlidir; ikinci birincil oluşturucuya ilgilidir. Her iki durumda da, varsayılan değer `public`.

Kullanarak bir sınıf için taban sınıf belirtin `inherit` anahtar sözcüğü. Taban sınıf oluşturucu için ayraç içinde bağımsız değişken sağlamanız gerekir.

Alanları bildirme veya işlevini kullanarak sınıfı için yerel olan değerleri `let` bağlamalar ve için genel kurallar uymalıdır `let` bağlar. `do-bindings` Bölüm nesne oluşturması yürütülmek üzere kod içerir.

`member-list` Ek Oluşturucular, örneği ve statik yöntem bildirimleri, arabirimi bildirimleri, soyut bağlamalar ve özelliğe ve olaya bildirimleri oluşur. Bunlar [üyeleri](members/index.md).

`identifier` Kullanılan isteğe bağlı WITH `as` anahtar sözcüğü örnek değişkeni veya tür tanımında türü örneğine başvuru yapmak için kullanılan kendi kendine tanımlayıcı bir ad sağlar. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde Self tanımlayıcıları bölümüne bakın.

Anahtar sözcükler `class` ve `end` başlangıç işaretleyin ve tanımının bitiş isteğe bağlı.

Birbirine başvuru türleri olan özyinelemeli türleri ile birlikte birbirini katılan `and` karşılıklı özyinelemeli işlevler olarak yalnızca anahtar sözcüğü. Örneğin, karşılıklı özyinelemeli türleri bölümüne bakın.


## <a name="constructors"></a>Oluşturucular
Oluşturucusu sınıf türünün bir örneği oluşturan kodudur. Diğer .NET dilleri göründüklerinden oluşturucuları sınıfları için biraz farklı F #'de çalışır. Bir F # sınıfında yok her zaman olan bağımsız değişkenler bölümünde açıklanmıştır birincil Oluşturucusu `parameter-list` tür adı ve, gövde oluşur izleyen `let` (ve `let rec`) sınıf bildirimi ve başlangıcındabağlamaları`do`izleyin bağlar. Sınıf bildirimi boyunca kapsamdaki birincil Oluşturucunun bağımsız değişkenler.

Kullanarak ek oluşturucular ekleyebilirsiniz `new` anahtar şu şekilde bir üye eklemek için:

`new`(`argument-list`) = `constructor-body`

Yeni Oluşturucusu gövdesi sınıf bildiriminin en üstünde belirtilen birincil oluşturucuyu çağırmanız gerekir.

Aşağıdaki örnekte bu kavramı gösterir. Aşağıdaki kodda, `MyClass` iki Oluşturucusu vardır, iki bağımsız değişkenleri ve başka bir oluşturucuyu alan bir birincil oluşturucu bağımsız değişken almayan.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]
    
## <a name="let-and-do-bindings"></a>let ve do bağlamaları

`let` Ve `do` bağlamaları sınıf tanımında form birincil sınıf oluşturucu gövdesi ve bu nedenle çalıştıkları her bir sınıf örneği oluşturulur. Varsa bir `let` bağlama bir işlevi olan sonra üyesi derlenir. Varsa `let` bağlama herhangi bir işlev veya üye kullanılmayan bir değerdir ve ardından onu oluşturucuya yerel bir değişken derlenir. Aksi takdirde, bu sınıfın bir alana derlenir. `do` İzleyin ifadeleri birincil oluşturucuya derlenir ve her örneği için başlatma kodunu yürütün. Tüm ek oluşturucular her zaman birincil Oluşturucusu çağırması nedeniyle `let` bağlamalar ve `do` bağlamaları her zaman yürütme bağımsız olarak Oluşturucusu çağrılır.

Tarafından oluşturulan alanları `let` bağlamaları erişilebilir sınıfının özelliklerini ve yöntemlerini; statik yöntemler bir örnek değişkeni bir parametre olarak geçirmesine olsa bile ancak, bunlar statik yöntemleri, erişilemez. Varsa, kendi kendine tanımlayıcısı kullanılarak erişilemez.


## <a name="self-identifiers"></a>Kendine yönelik tanımlayıcılar

A *kendini tanımlayıcı* geçerli örneği temsil eden bir addır. Kendine yönelik tanımlayıcılar benzer `this` C# ya da C++ anahtar sözcük veya `Me` Visual Basic'te. Kapsamdaki tüm sınıf tanımını veya yalnızca tek bir yöntemi olması için kendi kendine tanımlayıcısı mi istediğinize bağlı olarak, iki farklı yolla kendini tanımlayıcı tanımlayabilirsiniz.

Tüm sınıfı için kendi kendine bir tanımlayıcı tanımlamak için `as` ayraç Oluşturucusu parametresinin sonra anahtar sözcüğü listelemek ve tanımlayıcı adı belirtin.

Yalnızca bir yöntem için kendi kendine bir tanımlayıcı tanımlamak için hemen önce yöntem adını ve ayırıcı olarak bir nokta (.) üye bildirimi kendini tanımlayıcıda sağlar.

Aşağıdaki kod örneğinde bir kendi kendini tanımlayıcı oluşturmanın iki yolu gösterilmektedir. İlk satırdaki `as` anahtar sözcüğü kendini tanımlayıcı tanımlamak için kullanılır. Beşinci satır tanımlayıcısı olarak `this` kapsamını yöntemi kısıtlıdır self bir tanımlayıcı tanımlamak için kullanılan `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Ancak, istediğiniz aksine diğer .NET dilleri, kendi kendine tanımlayıcı adı verebilirsiniz; adları gibi sınırlı değildir `self`, `Me`, veya `this`.

İle bildirilen kendini tanımlayıcı `as` kadar anahtar sözcüğü başlatılmadı sonra `let` bağlamaları çalıştırılır. Bu nedenle, onu kullanılamaz `let` bağlar. Kendi kendine tanımlayıcıda kullanabilirsiniz `do` bağlamaları bölümü.


## <a name="generic-type-parameters"></a>Genel Tür Parametreleri

Genel tür parametreleri açılı ayraçları içinde belirtilen (`<` ve `>`), ardından bir tanımlayıcısını tek tırnak işareti biçiminde. Birden fazla genel tür parametreleri virgülle ayrılır. Genel tür parametresi kapsam bildirimi boyunca kullanılıyor. Aşağıdaki kod örneğinde, genel tür parametreleri belirtin gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Tür bağımsız değişkenleri türü kullanıldığında algılanır. Aşağıdaki kodda çıkarılan türü başlık bir dizidir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]
    
## <a name="specifying-inheritance"></a>Devralma belirtme

`inherit` Yan tümcesi varsa doğrudan temel sınıf tanımlar. F #'ta doğrudan yalnızca bir temel sınıf izin verilir. Bir sınıf uygular arabirimleri temel sınıflar olarak kabul edilmez. Arabirimler içinde ele alınmıştır [arabirimleri](Interfaces.md) konu.

Dil anahtar sözcüğünü kullanarak türetilmiş sınıftan temel sınıfının özelliklerini ve yöntemlerini erişebilirsiniz `base` bir tanımlayıcı olarak ve ardından bir nokta (.) ve üyenin adını tarafından.

Daha fazla bilgi için bkz: [devralma](inheritance.md).


## <a name="members-section"></a>Üyeler bölümü
Bu bölümde, statik veya örnek yöntemler, özellikler, arabirim uygulamaları, soyut üyelerini, olay bildirimleri ve ek oluşturucular tanımlayabilirsiniz. Bu bölümde bağlamaları bulunamaz yapın ve sağlar. F # türleri sınıfları yanı sıra çeşitli üyeleri eklenebilir olduğundan, ayrı bir konuda ele alınan [üyeleri](members/index.md).


## <a name="mutually-recursive-types"></a>Karşılıklı özyinelemeli türleri
Döngüsel bir şekilde birbirine başvuru türleri tanımladığınızda, birlikte tür tanımları kullanarak dize `and` anahtar sözcüğü. `and` Anahtar sözcüğü değiştirir `type` şekilde ilk tanım dışında tüm anahtar sözcüğü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Çıkış, geçerli dizindeki tüm dosyaları listesidir.


## <a name="when-to-use-classes-unions-records-and-structures"></a>Sınıfları, birleşimler, kaydeder ve yapıları ne zaman kullanılacağını
Aralarından seçim yapabileceğiniz türleri çeşitli verildiğinde, ne her türü için belirli bir durum için uygun türü seçmek için tasarlanmıştır, iyi anlamış olmanız gerekir. Sınıfları, nesne odaklı programlama bağlamlarda kullanmak için tasarlanmıştır. Nesne odaklı programlama için .NET Framework yazılmış uygulamalarda kullanılan baskın örnektir. F # kod .NET Framework veya başka bir nesne yönelimli kitaplığı ile yakından çalışmaya varsa ve özellikle kullanıcı Arabirimi kitaplığı gibi bir nesne yönelimli türü sisteminden genişletmek varsa, büyük olasılıkla uygun sınıflarıdır.

Yakından nesne yönelimli kod ile birlikte çalışma değil ya da kendi içinde bulunan ve bu nedenle, nesne yönelimli kod sık etkileşim karşı korumalıdır kod yazıyorsanız, kayıtları kullanmayı düşünmeniz gerekir ve birleşimler. Tek bir iyi düşünce – çıkış kodu, eşleşen uygun düzeni ile birlikte ayrılmış birleşim genellikle bir nesne hiyerarşisi için daha basit bir alternatif olarak kullanılabilir. Ayrılmış birleşimler hakkında daha fazla bilgi için bkz: [ayrılmış birleşimler](discriminated-unions.md).

Kayıtları sınıfları basit olma avantajına sahiptir, ancak bir türü taleplerini ile bunların Basitlik gerçekleştirilebilir aştıklarında kayıtları uygun değildir. Değerleri, özel eylemleri gerçekleştirebilirsiniz ayrı Oluşturucular, gizli alanlar, olmadan ve devralma veya arabirim uygulamaları temelde basit toplamalar kayıtlarıdır. Üye özellikleri ve yöntemleri gibi davranışlarını daha karmaşık hale kayıtlara eklenebilir karşın, bir kayıtta depolanan hala değerlerin basit bir toplama alanlardır. Kayıt hakkında daha fazla bilgi için bkz: [kayıtları](records.md).

Yapıları ayrıca veri küçük Toplamalar için yararlı olan, ancak .NET değer türleri olduklarından, sınıflar ve kayıtları bunların farklı. Sınıfları ve kayıtları .NET başvurusu türleridir. Değer türleri değeri tarafından geçirilen değer türleri ve başvuru türleri semantiği farklı bir seçenektir. Kopyalanan sanal yani bir parametre olarak geçirilen veya bir işlevinden döndürülen bitini bit. Bunlar ayrıca yığında depolanan veya, yerine üst nesnenin içinde katıştırılmış bir alan olarak kullanılıyorsa yığın ayrı kendi konumunda depolanır. Bu nedenle, öbek erişme yükünü bir sorun olduğunda yapıları sık erişilen veriler için uygundur. Yapılar hakkında daha fazla bilgi için bkz: [yapıları](structures.md).


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Üyeler](members/index.md)

[Devralma](inheritance.md)

[Arabirimler](interfaces.md)

