---
title: Sınıflar
description: 'F # sınıflarının özelliklere, yöntemlere ve olaylara sahip olan nesneleri temsil eden türler olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: fd6638e0f1c08cf667a73582e19b2bb5bba46e20
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970173"
---
# <a name="classes"></a>Sınıflar

*Sınıflar* , özelliklere, yöntemlere ve olaylara sahip olabilir nesneleri temsil eden türlerdir.

## <a name="syntax"></a>Syntax

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

Sınıflar .NET nesne türlerinin temel açıklamasını temsil eder; sınıfı, F # içinde nesne odaklı programlamayı destekleyen birincil tür kavramıdır.

Önceki sözdiziminde, `type-name` geçerli bir tanıtıcıdır. `type-params`İsteğe bağlı genel tür parametrelerini açıklar. Bu, açılı ayraçlar (ve) içine alınmış parametre adları ve kısıtlamalarından oluşur `<` `>` . Daha fazla bilgi için bkz. [Genel türler](./generics/index.md) ve [kısıtlamalar](./generics/constraints.md). `parameter-list`Oluşturucu parametrelerini açıklar. İlk erişim değiştiricisi türe aittir; İkincisi, birincil oluşturucuya aittir. Her iki durumda da varsayılan olur `public` .

Anahtar sözcüğünü kullanarak bir sınıf için taban sınıfı belirtirsiniz `inherit` . Taban sınıf oluşturucusu için parantez içinde bağımsız değişkenler sağlamanız gerekir.

Bağlamaları kullanarak sınıfa yerel olan alanları veya işlev değerlerini bildirir `let` ve bağlamaların genel kurallarını izlemeniz gerekir `let` . `do-bindings`Bölüm, nesne oluşturma sırasında yürütülecek kodu içerir.

`member-list`Ek oluşturucular, örnek ve statik yöntem bildirimleri, arabirim bildirimleri, soyut bağlamalar ve özellik ve olay bildirimleri oluşur. Bunlar [Üyelerde](./members/index.md)açıklanmıştır.

`identifier`İsteğe bağlı anahtar sözcüğü ile birlikte kullanılan, `as` örnek değişkenine veya türün örneğine başvurmak için tür tanımında kullanılabilecek bir ad verir. Daha fazla bilgi için, bu konunun ilerleyen kısımlarında yer almaktadır.

`class` `end` Tanımın başlangıcını ve bitişini işaretleyen anahtar sözcükler ve isteğe bağlıdır.

Birbirini gösteren türler olan birbirini dışlayan özyinelemeli türler, `and` tıpkı karşılıklı özyinelemeli işlevlerin olduğu gibi anahtar sözcükle birlikte birleştirilir. Bir örnek için, birbirini dışlayan özyinelemeli türler bölümüne bakın.

## <a name="constructors"></a>Oluşturucular

Oluşturucu, sınıf türünün bir örneğini oluşturan koddur. Sınıfların oluşturucuları, F # ' ta diğer .NET dillerinde olduklarından farklı şekilde çalışır. Bir F # sınıfında, bağımsız değişkenleri `parameter-list` tür adını izleyen ' de açıklanan ve gövdesi `let` `let rec` sınıf bildiriminin başlangıcında ve izleyen bağlamalardan oluşan (ve) bağlamalardan oluşan bir birincil Oluşturucu vardır `do` . Birincil oluşturucunun bağımsız değişkenleri, sınıf bildiriminin tamamında kapsamdadır.

`new`Aşağıdaki gibi bir üye eklemek için anahtar sözcüğünü kullanarak ek oluşturucular ekleyebilirsiniz:

`new`(`argument-list`) = `constructor-body`

Yeni oluşturucunun gövdesi, sınıf bildiriminin en üstünde belirtilen birincil oluşturucuyu çağırmalıdır.

Aşağıdaki örnekte bu kavram gösterilmektedir. Aşağıdaki kodda, iki `MyClass` bağımsız değişken alan bir birincil Oluşturucu ve bağımsız değişken içermeyen başka bir Oluşturucu olan iki Oluşturucu vardır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>Let ve do bağlamaları

`let` `do` Bir sınıf tanımındaki ve bağlamaları, birincil sınıf oluşturucusunun gövdesini oluşturur ve bu nedenle her bir sınıf örneği oluşturulduğunda çalışır. `let`Bağlama bir işlev ise, bir üyeye derlenir. `let`Bağlama herhangi bir işlevde veya üyede kullanılmayan bir değer ise, oluşturucunun yerel bir değişkenine derlenir. Aksi halde, sınıfının bir alanına derlenir. `do`Aşağıdaki ifadeler birincil oluşturucuya derlenir ve her örnek için başlatma kodunu yürütür. Herhangi bir ek Oluşturucu her zaman birincil oluşturucuyu çağırdığından, `let` bağlamalar ve `do` bağlamalar hangi oluşturucunun çağrıldığına bakılmaksızın her zaman yürütülür.

`let`Bağlamalarla oluşturulan alanlara sınıfının yöntemleri ve özellikleri boyunca erişilebilir; ancak, statik yöntemler parametre olarak bir örnek değişkeni alsa bile, bunlara statik metotlardan erişilemez. Bir varsa, kendi kendine tanımlayıcı kullanılarak erişilemez.

## <a name="self-identifiers"></a>Kendi kendine tanımlayıcılar

*Kendi kendine tanımlayıcı* , geçerli örneği temsil eden bir addır. Kendi tanımlayıcıları, `this` C# veya C++ veya Visual Basic içindeki anahtar sözcüğe benzer `Me` . Kendi sınıf tanımının veya yalnızca tek bir yöntemin kapsamında olmasını isteyip istemediğinize bağlı olarak, kendinden tanımlayıcıyı iki farklı şekilde tanımlayabilirsiniz.

Tüm sınıf için kendi kendine tanımlayıcı tanımlamak için, `as` Oluşturucu parametre listesinin kapatma parantezinden sonra anahtar sözcüğünü kullanın ve tanımlayıcı adını belirtin.

Yalnızca bir yöntem için kendi kendine tanımlayıcı tanımlamak üzere, üye bildiriminde, yöntem adından ve bir nokta (.) ayırıcı olarak kendi kendine tanımlayıcıyı sağlayın.

Aşağıdaki kod örneği, kendi kendine tanımlayıcı oluşturmanın iki yolunu göstermektedir. İlk satırda, `as` anahtar sözcüğü kendi tanımlayıcısını tanımlamak için kullanılır. Beşinci satırda, `this` kapsamı yöntemiyle kısıtlanmış bir kendi tanımlayıcısını tanımlamak için tanımlayıcı kullanılır `PrintMessage` .

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Diğer .NET dillerinin aksine, kendi tanımlayıcısını istediğiniz şekilde adlandırın; , veya gibi adlarla sınırlı değilsiniz `self` `Me` `this` .

Anahtar sözcüğüyle belirtilen kendine tanımlayıcı, `as` temel oluşturucudan sonra başlatılmaz. Bu nedenle, temel oluşturucunun öncesinde veya içinde kullanıldığında, `System.InvalidOperationException: The initialization of an object or value resulted in an object or value being accessed recursively before it was fully initialized.` çalışma zamanı sırasında tetiklenir. Kendi kendine tanımlayıcıyı, bağlama veya bağlamalar gibi temel oluşturucudan sonra ücretsiz olarak kullanabilirsiniz `let` `do` .

## <a name="generic-type-parameters"></a>Genel Tür Parametreleri

Genel tür parametreleri `<` `>` , tek tırnak işareti ve ardından bir tanımlayıcı tarafından izlenen köşeli ayraç (ve) biçiminde belirtilir. Birden çok genel tür parametresi virgülle ayrılır. Genel tür parametresi, bildirim genelinde kapsamdadır. Aşağıdaki kod örneği, genel tür parametrelerinin nasıl ekleneceğini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Tür bağımsız değişkenleri tür kullanıldığında algılanır. Aşağıdaki kodda, gösterilen tür bir tanımlama grubu dizisidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Devralmayı belirtme

`inherit`Yan tümcesi, varsa doğrudan temel sınıfı tanımlar. F # içinde yalnızca bir doğrudan taban sınıfa izin verilir. Bir sınıfın uyguladığı arabirimler temel sınıflar olarak kabul edilmez. Arabirimler, [arabirimler](Interfaces.md) konusunda ele alınmıştır.

Dil anahtar sözcüğünü `base` tanımlayıcı olarak ve ardından bir nokta (.) ve üyenin adını kullanarak türetilmiş sınıftan temel sınıfın yöntemlerine ve özelliklerine erişebilirsiniz.

Daha fazla bilgi için bkz. [Devralma](inheritance.md).

## <a name="members-section"></a>Üyeler bölümü

Bu bölümde statik veya örnek yöntemleri, özellikleri, arabirim uygulamalarını, soyut üyeleri, olay bildirimlerini ve ek oluşturucuları tanımlayabilirsiniz. Let ve do bağlamaları bu bölümde görünemez. Üyeler sınıflara ek olarak çeşitli F # türlerine eklenebildiğinden, bunlar ayrı bir konuda, [üyelerinde](./members/index.md)ele alınmıştır.

## <a name="mutually-recursive-types"></a>Birbirini dışlayan özyinelemeli türler

Birbirini dairesel bir şekilde birbirlerine başvuran türler tanımladığınızda, anahtar sözcüğünü kullanarak tür tanımlarını birlikte dizolursunuz `and` . `and`Anahtar sözcüğü, `type` aşağıdaki gibi, ilk tanım hariç tüm anahtar kelimesinin yerini alır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Çıktı, geçerli dizindeki tüm dosyaların bir listesidir.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Sınıfların, birleşimlerin, kayıtların ve yapıların ne zaman kullanılacağı

Aralarından seçim yapabileceğiniz çeşitli türler verildiğinde, belirli bir durum için uygun türü seçmek üzere her bir türün ne şekilde tasarlandığına ilişkin iyi bir fikir sahibi olmanız gerekir. Sınıflar, nesne odaklı programlama bağlamlarında kullanılmak üzere tasarlanmıştır. Nesne odaklı programlama, .NET Framework için yazılan uygulamalarda kullanılan baskın paradigma. F # kodunuzun .NET Framework veya başka bir nesne tabanlı kitaplıkla yakından çalışması gerekiyorsa ve özellikle de bir UI kitaplığı gibi nesne yönelimli bir tür sisteminden genişletmeniz gerekiyorsa, sınıflar muhtemelen uygun olabilir.

Nesne odaklı kodla yakından birlikte bulundurduysanız veya kendi içinde bulunan ve bu nedenle nesne odaklı kod ile sık etkileşim 'ten korunan bir kod yazıyorsanız, kayıtları ve ayırt edici birleşimleri kullanmayı göz önünde bulundurmanız gerekir. Uygun düzende eşleşen kod ile birlikte, tek ve iyi düşünce bir ayrılmış birleşim, genellikle bir nesne hiyerarşisinin daha basit bir alternatifi olarak kullanılabilir. Ayrılmış birleşimler hakkında daha fazla bilgi için bkz. [ayırt edici birleşimler](discriminated-unions.md).

Kayıtlar, sınıflardan daha basit olmasının avantajına sahiptir, ancak bir tür talepleri basitlikle neler yapılabileceğini aşarsa kayıtlar uygun değildir. Kayıtlar, gizli alanlar olmadan ve devralma ya da arabirim uygulamaları olmadan özel eylemler gerçekleştirebilen ayrı oluşturucular olmadan, temelde basit değer toplalarıdır. Özellikleri ve yöntemleri gibi Üyeler davranışlarını daha karmaşık hale getirmek için kayıtlara eklenebilse de, bir kayıtta depolanan alanlar yine de basit değerler toplamasıdır. Kayıtlar hakkında daha fazla bilgi için bkz. [kayıtlar](records.md).

Yapıları, küçük veri toplamaları için de kullanışlıdır, ancak .NET değer türleri oldukları sınıfların ve kayıtlardan farklıdır. Sınıflar ve kayıtlar .NET başvuru türleridir. Değer türleri ve başvuru türleri semantiği değer tarafından geçirilir. Bu, bir parametre olarak geçirildiği veya bir işlevden döndürüldüğü zaman bit için bit olarak kopyalandığı anlamına gelir. Ayrıca, yığın üzerinde saklanır veya bir alan olarak kullanılıyorsa, yığın üzerinde kendi ayrı konumlarına depolanması yerine üst nesnenin içine gömülü olurlar. Bu nedenle, yığına erişim ek yükü bir sorun olduğunda yapılar sık erişilen veriler için uygundur. Yapılar hakkında daha fazla bilgi için bkz. [yapılar](structures.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Üyeler](./members/index.md)
- [Devralma](inheritance.md)
- [Arabirimler](interfaces.md)
