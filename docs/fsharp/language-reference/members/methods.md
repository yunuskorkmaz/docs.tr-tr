---
title: Yöntemler
description: 'Bilgi nasıl bir F# yöntemdir: kullanıma sunmak ve davranışı nesnelerin ve türleri ve işlevleri uygulamak için kullanılan bir türü ile ilişkili bir işlev.'
ms.date: 05/16/2016
ms.openlocfilehash: 03150cc67f79bfde58cf27e4a9d4dfa9e9ff3f55
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614032"
---
# <a name="methods"></a>Yöntemler

A *yöntemi* türü ile ilişkilendirilmiş bir işlevdir. Nesne yönelimli programlama, yöntemleri, kullanıma ve davranışı nesnelerin ve türleri ve işlevleri uygulamak için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, çeşitli forms yöntemi bildirimlerinin ve tanımlarının görebilirsiniz. Uzun metot gövdeleri eşittir (=) satır sonu izler ve tüm yöntem gövdesini girintili hale getirilir.

Öznitelikler için herhangi bir yöntem bildiriminde uygulanabilir. Bunlar, bir yöntem tanımını sözdizimi koyun ve genellikle ayrı bir satıra listelenir. Daha fazla bilgi için [öznitelikleri](../attributes.md).

Yöntemleri işaretlenebilir `inline`. Hakkında bilgi için `inline`, bkz: [satır içi işlevleri](../functions/inline-functions.md).

Satır içi yöntemler türü içinde kullanılan yinelemeli olarak olabilir. açıkça kullanmaya gerek yoktur `rec` anahtar sözcüğü.

## <a name="instance-methods"></a>Örnek yöntemleri

Örnek yöntemleri ile bildirilmiş `member` anahtar sözcüğü ve *kendi kendine tanımlayıcısı*ve ardından bir nokta (.) ve yöntem adı ve parametreleri. İçin olduğu gibi `let` bağlamaları *parametre-listesi* desen olabilir. Genellikle, yöntemlerin bir kayıt düzeni formunda parantez içinde parametreleri görünür yöntemi içine alın F# ne zaman oluşturulduğu diğer .NET Framework dillerinde. Ancak, curried (parametrelerini boşluklarla ayırarak) Ayrıca yaygın biçimidir ve diğer desenleri de desteklenir.

Aşağıdaki örnekte, soyut olmayan örnek yöntemi kullanımını ve tanımı gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Örnek yöntemler let bağlamaları kullanılarak tanımlanmış erişim alanlarına erişmek için kendi kendine tanımlayıcısı kullanmayın. Diğer üyeleri ve özelliklerine erişirken kendini tanımlayıcısı kullanın.

## <a name="static-methods"></a>Statik yöntemler

Anahtar sözcüğü `static` örneği olmadan bir yöntem çağrılabilir belirtmek için kullanılır ve bir nesne örneği ile ilişkili değil. Aksi takdirde, örnek yöntemler yöntemlerdir.

Sonraki bölümde örnek alanları ile bildirilen gösterir `let` özelliği üyelerini anahtar sözcüğü ile bildirilmiş `member` anahtar sözcüğü ve ile bildirilen bir statik yöntem `static` anahtar sözcüğü.

Aşağıdaki örnek, statik yöntemler kullanımını ve tanımı gösterilmektedir. Bu yöntem tanımlarını olduğunu varsayın `SomeType` önceki bölümde sınıfı.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemleri

Anahtar sözcüğü `abstract` bir yöntem bir sanal dağıtım yuvasına sahiptir ve bir tanımı sınıfında olmayabilir gösterir. A *sanal dağıtım yuvası* olduğundan çalışma zamanında sanal işlevini aramak için kullanılan dahili olarak tutulan bir tabloda işlevlerin bir giriş bir nesne yönelimli türünün çağırır. Sanal dağıtım mekanizması uygular mekanizmadır *çok biçimlilik*, nesne yönelimli programlama önemli bir özelliğidir. Bir tanımı olmadan en az bir soyut yöntemi olan bir sınıfı, bir *soyut sınıf*, yani bu sınıfının hiçbir örneği oluşturulabilir. Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut sınıflar](../abstract-classes.md).

Soyut yöntem bildirimleri bir yöntem gövdesi içermez. Bunun yerine, yöntemin adı iki nokta üst üste (:) ve bir tür imzası yöntemi tarafından izlenir. Bir yöntem tür imzası, fare işaretçisini bir yöntem adı Visual Studio Kod Düzenleyicisi'nde, üzerinde dışında parametre adları duraklattığınızda IntelliSense tarafından gösterilen aynıdır. Etkileşimli olarak çalışırken türü imzalarını fsi.exe yorumlayıcısı tarafından da görüntülenir. Tür imzası bir yöntemin kullanıma uygun ayırıcı semboller dönüş türüyle ardından, parametre türleri listesi tarafından oluşturulur. Curried parametreleri ayrılır `->` ve demet parametre ayrılır `*`. Bağımsız değişken tarafından gelen dönüş değeri her zaman ayrılmış bir `->` sembol. Parantezler, bir işlev türü bir parametre olduğunda gibi karmaşık parametreler, Grup veya tek bir parametre yerine iki parametre olarak bir tanımlama grubu ne zaman işlendiğini belirten kullanılabilir.

De soyut yöntemler varsayılan tanımları tanımı sınıfa ekleme ve kullanma tanıyabilirsiniz `default` anahtar sözcüğü, bu konudaki sözdizimi bloğunda gösterildiği gibi. Aynı sınıf içinde bir tanıma sahip soyut bir yöntemi, diğer .NET Framework dillerinde sanal bir yöntem eşdeğerdir. Bir tanımı var olup olmadığını `abstract` anahtar sözcüğü, sınıfın sanal işlev tablosuna yeni bir dağıtım yuvası oluşturur.

Bir taban sınıfı soyut yöntemlerini mi uygulayan bağımsız olarak, türetilmiş sınıflar uygulamaları soyut yöntemler sağlar. Türetilen bir sınıfta bir soyut yönteminden uygulamak için kullanımı dışında türetilmiş sınıf içinde aynı ada ve imzaya sahip bir yöntemi tanımlamak `override` veya `default` anahtar sözcüğü ve yöntem gövdesini belirtin. Anahtar sözcükler `override` ve `default` tam olarak aynı anlama gelir. Kullanma `override` yeni bir temel sınıf uygulaması; kılma kullanırsanız `default` özgün soyut bildirimiyle aynı sınıftaki bir uygulama oluşturduğunuzda. Kullanmayın `abstract` anahtar sözcüğü, soyut temel sınıfta bildirilen yöntemini uygulayan bir yöntem.

Aşağıdaki örnekte bir soyut yönteminden `Rotate` bir varsayılan uygulama, .NET Framework sanal bir yöntem denk olan.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Aşağıdaki örnek, bir temel sınıf yöntemini geçersiz kılan türetilmiş bir sınıf göstermektedir. Bu durumda geçersiz kılma davranışı değiştirir, böylece yöntemi hiçbir şey yapmaz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler

Belirli bir türde aynı ada sahip olan ancak farklı bağımsız değişkenleri olan yöntemleri aşırı yüklenmiş yöntemlerdir. İçinde F#, isteğe bağlı bağımsız değişkenler genellikle aşırı yüklenmiş yöntemler yerine kullanılır. Bununla birlikte, bağımsız değişken değil curried form, tanımlama grubu form olması koşuluyla aşırı yüklenmiş yöntemler dilde izin verilir.

## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler

İle başlayarak F# 4.1, varsayılan parametre değeri ile isteğe bağlı bağımsız değişkenlere yöntemleri de vardır.  C# kod ile birlikte çalışma kolaylaştırmaya yardımcı olması için budur.  Aşağıdaki örnek, sözdizimini gösterir:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

İçinde geçirilen değer için Not `DefaultParameterValue` giriş türüyle eşleşmelidir.  Yukarıdaki örnekte olduğu bir `int`.  Bir tamsayı olmayan değerde geçirmeye çalışırken `DefaultParameterValue` bir derleme hatasına neden olur.

## <a name="example-properties-and-methods"></a>Örnek: Özellikleri ve yöntemleri

Aşağıdaki örnek, alanları, özel işlevler, özellikler ve bir statik yöntem örnekleri olan bir türü içerir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)