---
title: "Yöntemler (F#)"
description: "Nasıl bir F # yöntemi işlevsellik ve nesneler ve türlerle davranışını uygular ve kullanıma sunmak için kullanılan bir türle ilişkilendirilmiş bir işlevi olduğunu öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a>Yöntemler

A *yöntemi* türü ile ilişkilendirilmiş bir işlevdir. Nesne odaklı programlama içinde yöntemleri işlevsellik ve nesneler ve türlerle davranışını uygular ve kullanıma sunmak için kullanılır.


## <a name="syntax"></a>Sözdizimi

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde yöntemi bildirimler ve tanımlar çeşitli biçimlerde görebilirsiniz. Uzun yöntem gövdeleri eşittir (=) satır sonu izler ve tüm yöntem gövdesi girintili.

Öznitelikler için herhangi bir yöntem bildirimi uygulanabilir. Bunlar, bir yöntemin tanımı sözdizimi koyun ve genellikle ayrı bir satırda listelenir. Daha fazla bilgi için bkz: [öznitelikleri](../attributes.md).

Yöntemleri işaretlenir `inline`. Hakkında bilgi için `inline`, bkz: [satır içi işlevler](../functions/inline-functions.md).

Satır içi olmayan yöntemleri türü içinde kullanılan yinelemeli olabilir; açıkça kullanmaya gerek yoktur `rec` anahtar sözcüğü.


## <a name="instance-methods"></a>Örnek yöntemleri
Örnek yöntemleri ile bildirildiğinde `member` anahtar sözcüğü ve *kendi kendine tanımlayıcı*takip eden bir nokta (.) ve yöntem adı ve parametreleri. İçin olduğu gibi `let` bağlamaları *parametre listesi* bir desen olabilir. Diğer .NET Framework dillerde oluşturduğunuzda genellikle, Parametreler şekilde yöntemleri bir tanımlama grubu formunda parantez içinde görüntülenir yöntemi F # alın. Ancak, curried formun (parametrelerini boşluklarla ayırarak) de yaygındır ve diğer desenleri de desteklenir.

Aşağıdaki örnek, bir Özet olmayan örnek yöntemin kullanılması ve tanımı gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Örnek yöntemleri içinde kendi kendine tanımlayıcı let bağlamaları kullanarak tanımlanan erişim alanları kullanmayın. Kendi kendine tanımlayıcı diğer üyeleri ve özellikleri erişirken kullanın.


## <a name="static-methods"></a>Statik yöntemler
Anahtar sözcüğü `static` bir yöntem örneği çağrılabilir belirtmek için kullanılır ve bir nesne örneği ile ilişkili değil. Aksi takdirde, örnek yöntemleri yöntemleridir.

Sonraki bölümdeki örnek ile bildirilen alanlarını gösterir `let` özelliği üyelerini anahtar sözcüğü, bildirilen ile `member` anahtar sözcüğü ve bir statik yöntem ile bildirilen `static` anahtar sözcüğü.

Aşağıdaki örnek, tanım ve statik yöntemler kullanımını gösterir. Bu yöntem tanımlarını olduğunu varsayın `SomeType` önceki bölümdeki sınıfı.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemleri
Anahtar sözcüğü `abstract` bir yöntem bir sanal dağıtım yuvasına sahip ve bir tanımı sınıfında olmayabilir gösterir. A *sanal dağıtım yuvası* çalışma zamanında sanal işlevini aramak için kullanılan içte oluşturulmuş tabloya işlevlerin bir girişe çağıran bir nesne yönelimli türü değil. Sanal dağıtım mekanizması uygulayan mekanizmasıdır *çok biçimlilik*, nesne odaklı programlama önemli bir özelliğidir. Bir tanımı olmadan en az bir soyut yöntemi olan bir sınıfı olan bir *soyut sınıf*, yani bu sınıfının hiçbir örneği oluşturulabilir. Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut sınıflar](../abstract-classes.md).

Özet yöntem bildirimleri bir yöntem gövdesi dahil etmeyin. Bunun yerine, iki nokta üst üste (:) ve bir tür imzası yöntemi için yöntem adını izler. Bir yöntemin tür imzası fare işaretçisi bir yöntem adı Visual Studio Kod Düzenleyicisi'nde, üzerinden dışında parametre adları duraklattığınızda IntelliSense tarafından gösterilen aynıdır. Etkileşimli olarak çalışırken türü imzaları fsi.exe yorumlayıcısı tarafından da görüntülenir. Bir yöntemin tür imzası uygun ayırıcı simgelerle dönüş türü ve ardından bu parametreleri türlerini listeleme tarafından oluşturulmuş. Curried parametreleri ayrılır `->` ve tanımlama grubu parametreleri ayrılır `*`. Dönüş değeri her zaman değişkenleriyle gelen ayrılmış bir `->` simgesi. Parantez işlevi türü bir parametre olduğunda gibi karmaşık parametreleri, Grup veya tek bir parametre olarak yerine iki parametre olarak bir tanımlama grubu ne zaman işleneceğini belirtmek için kullanılabilir.

Ayrıca soyut yöntemler varsayılan tanımları tanımı sınıfına ekleme ve kullanarak verebilirsiniz `default` anahtar sözcüğü, bu konudaki sözdizimi bloğunda gösterildiği gibi. Aynı sınıfta bir tanımı sahip bir soyut yöntemi, sanal bir yöntem diğer .NET Framework dillerde eşdeğerdir. Olsun veya olmasın bir tanım var, `abstract` anahtar sözcüğü sınıfı için sanal işlev tablosunda yeni bir dağıtım yuvası oluşturur.

Türetilen sınıflar temel sınıf soyut yöntemler olup uygulayan bağımsız olarak, soyut yöntemler uygulamaları sağlayabilir. Türetilen bir sınıfta soyut bir yöntem uygulamak için kullanımı dışında türetilmiş sınıfında imza ve aynı ada sahip bir yöntemi tanımlamak `override` veya `default` anahtar sözcüğü ve yöntem gövdesi sağlayın. Anahtar sözcükler `override` ve `default` tam olarak aynı anlama gelir. Kullanmak `override` bir temel sınıf uygulamasını; yeni yöntemini geçersiz kılar kullanırsanız `default` özgün soyut bildirimi ile aynı sınıfta bir uygulama oluşturduğunuzda. Kullanmayın `abstract` anahtar sözcüğü taban sınıf içinde soyut bildirildi yöntemi uygulayan yöntemi.

Aşağıdaki örnekte, soyut bir yöntem gösterilmektedir `Rotate` varsayılan uygulama, .NET Framework sanal bir yöntem denk sahip.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Aşağıdaki örnek, bir temel sınıf yöntemini geçersiz kılar türetilmiş bir sınıf gösterilmektedir. Bu durumda, geçersiz kılma yöntemi, hiçbir şey yapmıyor şekilde davranışını değiştirir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler
Aşırı yüklenmiş yöntemler, belirli bir türde aynı adlara sahip ancak farklı bağımsız değişkenleri sahip yöntemlerdir. F #'ta isteğe bağlı bağımsız değişkenler genellikle aşırı yüklenmiş yöntemler yerine kullanılır. Ancak, bağımsız değişken değil curried form, tanımlama grubu form olması koşuluyla aşırı yüklenmiş yöntemler dilde izin verilir.

## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler

F # 4.1 ile başlayarak, yöntemleri varsayılan parametre değeri ile isteğe bağlı bağımsız değişkenler de sahip olabilir.  C# kod ile birlikte çalışma kolaylaştırmaya yardımcı olması için budur.  Aşağıdaki örnek sözdizimi gösterilmektedir:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Değer geçirilen için Not `DefaultParameterValue` giriş türüyle eşleşmelidir.  Yukarıdaki örnekte olduğu bir `int`.  Tamsayı olmayan değerler uygulamasına geçirmek çalışırken `DefaultParameterValue` bir derleme hatasına neden olur.

## <a name="example-properties-and-methods"></a>Örnek: Özellikleri ve yöntemleri
Aşağıdaki örnek, alanları, özel işlevler, özellikleri ve bir statik yöntem örnekleri olan bir türü içerir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Ayrıca Bkz.
[Üyeleri](index.md)
