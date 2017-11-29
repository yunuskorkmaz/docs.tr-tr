---
title: "Klavye Başvurusu (F#)"
description: "Tüm F # dili anahtar hakkında bilgilere bağlantılar bulma."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: cdfdd86843acf05a8b33647823f934a161f6d885
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="keyword-reference"></a>Klavye Başvurusu

Bu konu, tüm F # dili anahtar sözcükler hakkında bilgilere bağlantılar içerir.

## <a name="f-keyword-table"></a>F # anahtar tablosu

Aşağıdaki tabloda tüm F # anahtar sözcükleri kısa açıklamaları ve daha fazla bilgi içeren ilgili konulara bağlantılar ile birlikte alfabetik sırada gösterir.

|Anahtar sözcüğü|Bağlantı|Açıklama|
|-------|----|-----------|
|`abstract`|[Üyeleri](members/index.md)<br /><br />[Soyut sınıflar](abstract-classes.md)|Hiçbir uygulama türü, onu bildirilmiş veya, sanal ve varsayılan uygulama ya da sahip bir yöntemi gösterir.|
|`and`|[`let`Bağlamaları](functions/let-bindings.md)<br /><br />[Üyeleri](members/index.md)<br /><br />[Kısıtlamaları](generics/constraints.md)|Karşılıklı özyinelemeli bağlamaları genel parametreler üzerinde birden çok kısıtlamalar ile özellik bildirimleri kullanılır.|
|`as`|[Sınıfları](classes.md)<br /><br />[Desen eşleştirme](Pattern-Matching.md)|Bir nesne adı geçerli sınıf nesnesi vermek için kullanılır. Desen eşleştirme içinde tam bir desenle bir ad vermek için de kullanılır.|
|`assert`|[Onaylar](assertions.md)|Hata ayıklama sırasında kodu doğrulamak için kullanılır.|
|`base`|[Sınıfları](classes.md)<br /><br />[Devralma](inheritance.md)|Taban sınıf nesnesi adı olarak kullanılır.|
|`begin`|[Ayrıntılı sözdizimi](verbose-syntax.md)|Ayrıntılı sözdizimi kod bloğunun gösterir.|
|`class`|[Sınıfları](classes.md)|Ayrıntılı sözdizimi içinde bir sınıf tanımı başlangıcını gösterir.|
|`default`|[Üyeleri](members/index.md)|Bir Özet yöntemin bir uygulaması, gösterir; sanal bir yöntem oluşturmak için bir Özet yöntem bildirimi ile birlikte kullanılır.|
|`delegate`|[Temsilciler](delegates.md)|Bir temsilci bildirmek için kullanılır.|
|`do`|[do bağlamaları](functions/do-bindings.md)<br /><br />[Döngüler: `for...to` ifade](loops-for-to-expression.md)<br /><br />[Döngüler: `for...in` ifade](loops-for-in-expression.md)<br /><br />[Döngüler: `while...do` ifade](loops-while-do-expression.md)|Döngü yapıları veya kesinlik temelli kod yürütmek için kullanılır.|
|`done`|[Ayrıntılı sözdizimi](verbose-syntax.md)|Ayrıntılı sözdizimi içinde bir döngü ifadesinde kod bloğunu sonunu gösterir.|
|`downcast`|[Atama ve dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha düşük bir türe dönüştürmek için kullanılır.|
|`downto`|[Döngüler: `for...to` ifade](loops-for-to-expression.md)|İçinde bir `for` ifadesi, geriye doğru sayarak kullanılır.|
|`elif`|[Koşullu ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanma kullanılır. Kısa biçimi `else if`.|
|`else`|[Koşullu ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanma kullanılır.|
|`end`|[Yapıları](structures.md)<br /><br />[Ayrılmış birleşimler](discriminated-unions.md)<br /><br />[Kayıtları](records.md)<br /><br />[Tür uzantıları](type-extensions.md)<br /><br />[Ayrıntılı sözdizimi](verbose-syntax.md)|Tür tanımları ve tür uzantıları, üye tanımları bir bölümünü sonunu gösterir.<br /><br />İle başlayan bir kod bloğunun sonunu belirtmek için kullanılan ayrıntılı sözdiziminde `begin` anahtar sözcüğü.|
|`exception`|[Özel durum işleme](exception-handling/index.md)<br /><br />[Özel durum türleri](exception-handling/exception-types.md)|Özel durum türü bildirmek için kullanılır.|
|`extern`|[Dış İşlevler](functions/external-functions.md)|Bildirilen bir program öğesi başka bir ikili dosya veya derleme tanımlı gösterir.|
|`false`|[İlkel türler](primitive-types.md)|Boole sabit değer olarak kullanılır.|
|`finally`|[Özel durumlar: `try...finally` ifade](exception-handling/the-try-finally-expression.md)|İle birlikte kullanılan `try` olup bir özel durum meydana bağımsız olarak yürütülen kod bloğunu tanıtmak için.|
|`fixed`|[Sabit](fixed.md)|"Yığında toplanacak engelleyen bir işaretçi sabitlemek için" kullanılır.|
|`for`|[Döngüler: `for...to` ifade](loops-for-to-expression.md)<br /><br />[Döngüler: for... ifadesinde](loops-for-in-expression.md)|Döngü yapıları kullanılır.|
|`fun`|[Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md)|Lambda ifadeleri, olarak da bilinen anonim işlevler kullanılır.|
|`function`|[Eşleşme ifadeleri](match-expressions.md)<br /><br />[Lambda ifadeleri: Fun anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md)|Daha kısa bir alternatif olarak kullanılan `fun` anahtar sözcüğü ve `match` ifadesi bir lambda ifadesinde tek bir bağımsız değişken eşleştirme deseni vardır.|
|`global`|[Ad alanları](namespaces.md)|Üst düzey .NET ad alanı başvurmak için kullanılır.|
|`if`|[Koşullu ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanma yapılardan kullanılır.|
|`in`|[Döngüler: for... ifadesinde](loops-for-in-expression.md)<br /><br />[Ayrıntılı sözdizimi](verbose-syntax.md)|Sequence ifadeleri için ve ayrıntılı sözdizimi bağlamaları gelen ifadeleri ayırmak için kullanılır.|
|`inherit`|[Devralma](inheritance.md)|Bir temel sınıf veya temel arabirim belirtmek için kullanılır.|
|`inline`|[İşlevler](functions/index.md)<br /><br />[Satır içi işlevler](functions/inline-functions.md)|Doğrudan arayanın koda tümleşik bir işlev göstermek için kullanılır.|
|`interface`|[Arabirimleri](interfaces.md)|Bildirme ve arabirimleri uygulamak için kullanılır.|
|`internal`|[Erişim denetimi](access-control.md)|Üye görünür olduğunu belirtmek için kullanılan bütünleştirilmiş kod içindeki ancak değil dışında.|
|`lazy`|[Geç hesaplamalar](lazy-computations.md)|Yalnızca bir sonuç gerektiğinde gerçekleştirilmesi gereken bir hesaplama belirtmek için kullanılır.|
|`let`|[`let`Bağlamaları](functions/let-bindings.md)|Bağlama, bir değer veya işlevi için bir ad veya ilişkilendirmek için kullanılır.|
|`let!`|[Zaman uyumsuz iş akışları](asynchronous-workflows.md)<br /><br />[Hesaplama ifadeleri](computation-expressions.md)|Zaman uyumsuz bir hesaplama sonucu için bir ad bağlamak için zaman uyumsuz iş akışları veya hesaplama türü bir sonuç için bir ad bağlamak için kullanılan diğer hesaplama ifadeleri kullanılır.|
|`match`|[Eşleşme ifadeleri](match-expressions.md)|Değer bir desenle karşılaştırarak dal için kullanılan.|
|`member`|[Üyeleri](members/index.md)|Bir özellik veya bir nesne türü yönteminde bildirmek için kullanılır.|
|`module`|[Modülleri](modules.md)|Bir grup ilgili türleri, değerler ve İşlevler, mantıksal olarak diğer kodundan ayırmak için bir ad ilişkilendirmek için kullanılır.|
|`mutable`|[let bağlamaları](functions/let-bindings.md)|Bir değişken, diğer bir deyişle, değiştirilebilir bir değer bildirmek için kullanılır.|
|`namespace`|[Ad alanları](namespaces.md)|Bir grup ilgili türleri ve modülleri, mantıksal olarak diğer kodundan ayırmak için bir ad ilişkilendirmek için kullanılır.|
|`new`|[Oluşturucular](members/constructors.md)<br /><br />[Kısıtlamaları](generics/constraints.md)|Bildirme tanımlayın veya oluşturur veya bir nesne oluşturan bir oluşturucu çağırmak için kullanılır.<br /><br />Ayrıca genel parametresini kısıtlamalarını bir türü belirli bir oluşturucusu olmalıdır göstermek için kullanılır.|
|`not`|[Simge ve işleç başvurusu](symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamaları](generics/constraints.md)|Aslında bir anahtar sözcük. Ancak, `not struct` birlikte genel parametre kısıtlama olarak kullanılır.|
|`null`|[Null değerler](values/null-values.md)<br /><br />[Kısıtlamaları](generics/constraints.md)|Bir nesne olmaması gösterir.<br /><br />Ayrıca genel parametresini kısıtlamalar kullanılır.|
|`of`|[Ayrılmış birleşimler](discriminated-unions.md)<br /><br />[Temsilciler](delegates.md)<br /><br />[Özel durum türleri](exception-handling/exception-types.md)|Kategoriler değerlerin türünü belirtmek için ayrılmış birleşimler ve temsilci ve özel durum bildirimleri kullanılır.|
|`open`|[İçeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md)|Bir ad alanı veya modülü içeriğini niteliğe olmadan kullanılabilir yapmak için kullanılır.|
|`or`|[Simge ve işleç başvurusu](symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamaları](generics/constraints.md)|Boole koşullarla bir Boolean olarak kullanılan `or` işleci. Eşdeğer '||`.<br /><br />Ayrıca üye kısıtlamalar kullanılır.|
|`override`|[Üyeleri](members/index.md)|Temel sürümü sürümünden farklı bir Özet veya sanal yöntemi sürümünü gerçekleştirmek için kullanılır.|
|`private`|[Erişim denetimi](access-control.md)|Aynı tür veya modülü kodda üye olan erişimi sınırlandırır.|
|`public`|[Erişim denetimi](access-control.md)|Türü dışında aynı üyesine erişim sağlar.|
|`rec`|[İşlevler](functions/index.md)|Özyinelemeli bir işlevi olduğunu göstermek için kullanılır.|
|`return`|[Zaman uyumsuz iş akışları](Asynchronous-Workflows.md)<br /><br />[Hesaplama ifadeleri](computation-expressions.md)|Hesaplama ifadesi sonucu olarak sağlamak için bir değer belirtmek için kullanılır.|
|`return!`|[Hesaplama ifadeleri](computation-expressions.md)<br /><br />[Zaman uyumsuz iş akışları](asynchronous-workflows.md)|Hesaplama ifadesi göstermek için kullanılır, değerlendirildiğinde, içeren hesaplama ifadesi sonucu sağlar.|
|`select`|[Sorgu ifadeleri](query-expressions.md)|Sorgu ifadelerinde hangi alanların veya ayıklamak için sütunları belirtmek için kullanılır. Bunun gerçekten ayrılmış bir sözcük değildir ve yalnızca bir anahtar sözcük uygun bağlamda gibi davranan anlamına gelir bağlamsal bir anahtar olduğunu unutmayın.|
|`static`|[Üyeleri](members/index.md)|Bir yöntemi veya bir türün bir örneği çağrılabilir özelliği veya türü tüm örnekler arasında paylaşılan bir değer üyesi göstermek için kullanılır.|
|`struct`|[Yapıları](structures.md)<br /><br />[Kısıtlamaları](generics/constraints.md)|Bir yapı türüne bildirmek için kullanılır.<br /><br />Ayrıca genel parametresini kısıtlamalar kullanılır.<br /><br />Modül tanımları OCaml uyumluluğu için kullanılır.|
|`then`|[Koşullu ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Oluşturucular](members/constructors.md)|Koşullu ifadelerle kullanılır.<br /><br />Nesne oluşturması sonra yan etkileri gerçekleştirmek için de kullanılır.|
|`to`|[Döngüler: `for...to` ifade](loops-for-to-expression.md)|Kullanılan `for` döngüler aralık belirtmek için.|
|`true`|[İlkel türler](primitive-types.md)|Boole sabit değer olarak kullanılır.|
|`try`|[Özel durumlar: Try... with ifadesi](exception-handling/the-try-with-expression.md)<br /><br />[Özel durumlar: Try... finally ifadesi](exception-handling/the-try-finally-expression.md)|Bir özel durum oluşturabilir kod bloğunu tanıtmak için kullanılır. İle birlikte kullanılan `with` veya `finally`.|
|`type`|[F # türleri](fsharp-types.md)<br /><br />[Sınıfları](classes.md)<br /><br />[Kayıtları](records.md)<br /><br />[Yapıları](structures.md)<br /><br />[Numaralandırmalar](enumerations.md)<br /><br />[Ayrılmış birleşimler](discriminated-unions.md)<br /><br />[Tür kısaltmaları](type-abbreviations.md)<br /><br />[Ölçü birimleri](units-of-measure.md)|Bir sınıf, kayıt, yapısı, ayrılmış UNION, numaralandırma türü, ölçü bildirme veya türü kısaltma için kullanılır.|
|`upcast`|[Atama ve dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha yüksek bir türe dönüştürmek için kullanılır.|
|`use`|[Kaynak Yönetimi: `use` anahtar sözcüğü](resource-management-the-use-keyword.md)|Yerine kullanılan `let` gerektiren değerleri için `Dispose` kaynakları serbest bırakmak için çağrılabilir.|
|`use!`|[Hesaplama ifadeleri](computation-expressions.md)<br /><br />[Zaman uyumsuz iş akışları](asynchronous-workflows.md)|Yerine kullanılan `let!` zaman uyumsuz iş akışları ve diğer hesaplama ifadeleri gerektiren değerleri için `Dispose` kaynakları serbest bırakmak için çağrılabilir.|
|`val`|[Açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md)<br /><br />[İmzaları](signatures.md)<br /><br />[Üyeleri](members/index.md)|Bir değer belirtmek için bir imza ya da bir tür sınırlı durumlarda üyesi bildirmek için kullanılır.|
|`void`|[İlkel türler](primitive-types.md)|.NET gösterir `void` türü. Diğer .NET dilleri ile birlikte çalışırken kullanılır.|
|`when`|[Kısıtlamaları](generics/constraints.md)|Boole koşullar için kullanılan (*zaman koruyucuları*) desen eşleşmeleri ve genel tür parametresi için bir kısıtlama yan tümcesi tanıtmak için.|
|`while`|[Döngüler: `while...do` ifade](loops-while-do-expression.md)|Döngü yapısı tanıtır.|
|`with`|[Eşleşme ifadeleri](match-expressions.md)<br /><br />[Nesne ifadeleri](object-expressions.md)<br /><br />[Kopyalama ve güncelleştirme kayıt ifadeleri](copy-and-update-record-expressions.md)<br /><br />[Tür uzantıları](type-extensions.md)<br /><br />[Özel durumlar: `try...with` ifade](exception-handling/the-try-with-expression.md)|İle birlikte kullanılan `match` ifadeleri eşleşen kalıbı anahtar sözcük. Ayrıca nesne ifadeleri, kayıt kopyalama ifadeleri ve tür uzantıları üye tanımları tanıtmak için ve özel durum işleyicileri tanıtmak için kullanılır.|
|`yield`|[Dizileri](sequences.md)|Bir sıra ifadesi, bir sıra için bir değer üretmek için kullanılır.|
|`yield!`|[Hesaplama ifadeleri](computation-expressions.md)<br /><br />[Zaman uyumsuz iş akışları](asynchronous-workflows.md)|Bir hesaplama ifadesi içeren hesaplama ifadesi için sonuçları koleksiyonu verilen hesaplama ifadesi sonucu eklemek için kullanılır.|

Aşağıdaki belirteçleri F #'ta OCaml dilindeki anahtar sözcükler olduklarından ayrılmıştır:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Kullanırsanız `--mlcompatibility` derleyici seçeneği, yukarıdaki sözcükler kullanılabilir tanımlayıcıları.

Aşağıdaki belirteçleri, F # dilinin gelecekteki genişleme için anahtar olarak ayrılmıştır:

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `fixed`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)

[Simge ve işleç başvurusu](symbol-and-operator-reference/index.md)

[Derleyici Seçenekleri](compiler-options.md)
