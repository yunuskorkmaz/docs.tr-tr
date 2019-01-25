---
title: Klavye Başvurusu
description: Tüm ilgili bilgilere bağlantılar bulma F# dil anahtar sözcükleri.
ms.date: 05/16/2016
ms.openlocfilehash: 5a94a30ca0f73538cc22e76fa75bd76741b70d99
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857911"
---
# <a name="keyword-reference"></a>Klavye Başvurusu

Bu konu hakkındaki tüm bilgilere bağlantılar içerir F# dil anahtar sözcükleri.

## <a name="f-keyword-table"></a>F#Anahtar tablosu

Aşağıdaki tablo tüm gösterir F# kısa açıklamaları ve ilgili daha fazla bilgi içeren konulara bağlantılar ile birlikte alfabetik sırada anahtar sözcükleri.

|Anahtar sözcüğü|Bağlantı|Açıklama|
|-------|----|-----------|
|`abstract`|[Üyeler](members/index.md)<br /><br />[Soyut Sınıflar](abstract-classes.md)|Ya da tür içinde bildirildiği veya sanal olduğu ve varsayılan bir uygulama olan hiçbir uygulama sahip bir yöntemi gösterir.|
|`and`|[`let` Bağlamaları](functions/let-bindings.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Üyeler](members/index.md)<br /><br />[Kısıtlamalar](generics/constraints.md)|Karşılıklı özyinelemeli bağlamaları ve kayıtları, özellik bildirimlerini ve genel parametreler üzerinde birden fazla kısıtlama ile kullanılır.|
|`as`|[Sınıflar](classes.md)<br /><br />[Desen Eşleştirme](Pattern-Matching.md)|Geçerli sınıf nesnesini bir nesne adı vermek için kullanılır. Desen eşleşmesi içindeki tüm desen için bir ad vermek için de kullanılır.|
|`assert`|[Onaylamalar](assertions.md)|Hata ayıklama sırasında kodu doğrulamak için kullanılır.|
|`base`|[Sınıflar](classes.md)<br /><br />[Devralma](inheritance.md)|Temel sınıf nesnesi adı olarak kullanılır.|
|`begin`|[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Ayrıntılı sözdizimi bir kod bloğu başlangıcını gösterir.|
|`class`|[Sınıflar](classes.md)|Ayrıntılı sözdizimi bir sınıf tanımı başlangıcını gösterir.|
|`default`|[Üyeler](members/index.md)|Soyut Metoda ait bir uygulamasını gösterir. sanal bir yöntem oluşturmak için bir soyut metot bildirimi ile birlikte kullanılır.|
|`delegate`|[Temsilciler](delegates.md)|Bir temsilci bildirmek için kullanılır.|
|`do`|[do Bağlamaları](functions/do-bindings.md)<br /><br />[Döngüler: `for...to` İfade](loops-for-to-expression.md)<br /><br />[Döngüler: `for...in` İfade](loops-for-in-expression.md)<br /><br />[Döngüler: `while...do` İfade](loops-while-do-expression.md)|Döngü yapıları veya kesinlik temelli kod yürütmek için kullanılır.|
|`done`|[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Ayrıntılı sözdizimi döngü bir ifadede bir kod bloğunu sonuna gösterir.|
|`downcast`|[Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha düşük bir türe dönüştürmek için kullanılır.|
|`downto`|[Döngüler: `for...to` İfade](loops-for-to-expression.md)|İçinde bir `for` tersten hesaplanırken kullanılan bir ifade.|
|`elif`|[Koşullu ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanmayı kullanılır. Bir kısa formunu da `else if`.|
|`else`|[Koşullu ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanmayı kullanılır.|
|`end`|[Yapılar](structures.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Tür Uzantıları](type-extensions.md)<br /><br />[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Tür tanımları ve tür uzantıları, üye tanımlarının bir bölümün sonuna gösterir.<br /><br />İle başlayan bir kod bloğunun sonu belirtmek için kullanılan ayrıntılı sözdiziminde `begin` anahtar sözcüğü.|
|`exception`|[Özel Durum İşleme](exception-handling/index.md)<br /><br />[Özel Durum Türleri](exception-handling/exception-types.md)|Bir özel durum türü bildirmek için kullanılır.|
|`extern`|[Dış İşlevler](functions/external-functions.md)|Bildirilen program öğesi başka bir ikili ya da derleme tanımlanan gösterir.|
|`false`|[İlkel Türler](primitive-types.md)|Bir Boolean değişmez değer olarak kullanılır.|
|`finally`|[Özel durumlar: `try...finally` İfadesi](exception-handling/the-try-finally-expression.md)|İle birlikte kullanılan `try` olup özel bir durum oluştuğunda bağımsız olarak yürüten bir kod bloğunu dağıtır.|
|`fixed`|[düzeltildi](fixed.md)|"Yığındaki çöp olarak toplanacak olmasını engellemek için bir işaretçi sabitlemek için" kullanılır.|
|`for`|[Döngüler: `for...to` İfade](loops-for-to-expression.md)<br /><br />[Döngüler: for...in İfadesi](loops-for-in-expression.md)|Döngü yapıları kullanılır.|
|`fun`|[Lambda Expressions: `fun` Anahtar Sözcüğü](functions/lambda-expressions-the-fun-keyword.md)|Olarak da bilinen anonim İşlevler, lambda ifadeleri kullanılır.|
|`function`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Lambda Expressions: Fun anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md)|Daha kısa bir alternatif olarak kullanılan `fun` anahtar sözcüğü ve `match` ifade bir lambda ifadesinde tek bir bağımsız değişken desen vardır.|
|`global`|[Ad Alanları](namespaces.md)|Üst düzey .NET ad alanı başvurmak için kullanılır.|
|`if`|[Koşullu ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanma yapılarında kullanılır.|
|`in`|[Döngüler: for...in İfadesi](loops-for-in-expression.md)<br /><br />[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Sequence ifadeleri için ve ayrıntılı sözdizimi bağlamaları gelen ifadeleri ayırmak için kullanılır.|
|`inherit`|[Devralma](inheritance.md)|Bir temel sınıf veya temel arabirim belirtmek için kullanılır.|
|`inline`|[İşlevler](functions/index.md)<br /><br />[Satır İçi İşlevler](functions/inline-functions.md)|Arayanın koda doğrudan tümleştirilmiş bir işlev belirtmek için kullanılır.|
|`interface`|[Arabirimler](interfaces.md)|Arabirimi uygulayan ve bildirmek için kullanılır.|
|`internal`|[Erişim Denetimi](access-control.md)|Üye görünür olduğunu belirtmek için kullanılan bir derleme içinde ancak değil dışında.|
|`lazy`|[Geç Hesaplamalar](lazy-computations.md)|Bir sonuç yalnızca ihtiyacınız olduğunda gerçekleştirilecek olan hesaplamayı belirtmek için kullanılır.|
|`let`|[`let` Bağlamaları](functions/let-bindings.md)|Bağlama, bir değer veya işlevi için bir ad veya ilişkilendirmek için kullanılır.|
|`let!`|[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Zaman uyumsuz bir hesaplama sonucu için bir ad bağlamak için zaman uyumsuz iş akışları veya hesaplama türü olan bir sonuç için bir ad bağlamak için kullanılan diğer hesaplama ifadeleri kullanılır.|
|`match`|[Eşleşme İfadeleri](match-expressions.md)|Bir değer için bir desen karşılaştırarak dal için kullanılır.|
|`match!`|[Hesaplama İfadeleri](computation-expressions.md#match)|Satır içi sonucu üzerinde bir hesaplama ifadesi ve desen eşleştirme çağrısı kullanılır.|
|`member`|[Üyeler](members/index.md)|Bir özellik veya yöntemin bir nesne türü bildirmek için kullanılır.|
|`module`|[Modüller](modules.md)|Bir ad ilgili türleri, değerleri ve İşlevler, başka bir koddan mantıksal olarak birbirinden ayırmak için bir grubu ile ilişkilendirmek için kullanılır.|
|`mutable`|[let Bağlamaları](functions/let-bindings.md)|Diğer bir deyişle, değiştirilebilir bir değer bir değişken bildirmek için kullanılır.|
|`namespace`|[Ad Alanları](namespaces.md)|Bir ad ilgili türleri ve modüller, başka bir koddan mantıksal olarak birbirinden ayırmak için bir grup ile ilişkilendirmek için kullanılır.|
|`new`|[Oluşturucular](members/constructors.md)<br /><br />[Kısıtlamalar](generics/constraints.md)|Bildirmek için tanımlayın veya oluşturur veya bir nesne oluşturan bir oluşturucu çağırmak için kullanılır.<br /><br />Ayrıca genel parametre kısıtlamalarını bir türü belirli bir oluşturucusu olmalıdır belirtmek için kullanılır.|
|`not`|[Simge ve İşleç Başvurusu](symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](generics/constraints.md)|Aslında bir anahtar sözcük. Ancak, `not struct` birlikte genel parametre kısıtlama olarak kullanılır.|
|`null`|[Null Değerler](values/null-values.md)<br /><br />[Kısıtlamalar](generics/constraints.md)|Bir nesne olmaması gösterir.<br /><br />Ayrıca genel parametre kısıtlama kullanılan.|
|`of`|[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Temsilciler](delegates.md)<br /><br />[Özel Durum Türleri](exception-handling/exception-types.md)|Kategori değerlerinin türünü belirtmek için ayrılmış birleşimler ve temsilci ve özel durum bildirimleri kullanılır.|
|`open`|[Önemli Bildirimler: `open` Anahtar Sözcüğü](import-declarations-the-open-keyword.md)|Bir ad alanında veya modülde içeriğini nitelik olmadan kullanılabilir hale getirmek için kullanılır.|
|`or`|[Simge ve İşleç Başvurusu](symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](generics/constraints.md)|Bir Boolean olarak Boole koşullarla kullanılan `or` işleci. Eşdeğer '||`.<br /><br />Üye kısıtlamaları da kullanılır.|
|`override`|[Üyeler](members/index.md)|Bir sürümünü temel sürümden farklı bir Özet veya sanal yöntemi uygulamak için kullanılır.|
|`private`|[Erişim Denetimi](access-control.md)|Aynı typ nebo modul kodda üye erişimi kısıtlar.|
|`public`|[Erişim Denetimi](access-control.md)|Türü dışında bir üye erişim sağlar.|
|`rec`|[İşlevler](functions/index.md)|Bir işlev özyinelemeli olduğunu göstermek için kullanılır.|
|`return`|[Zaman Uyumsuz İş Akışları](Asynchronous-Workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Hesaplama ifadesi sonucu olarak sağlamak için bir değer belirtmek için kullanılır.|
|`return!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Hesaplama ifadesi göstermek için kullanılan, değerlendirildiğinde, içeren hesaplama ifadesi sonucu sağlar.|
|`select`|[Sorgu İfadeleri](query-expressions.md)|Sorgu ifadelerinde hangi alanları veya ayıklamak için sütunları belirtmek için kullanılır. Bu gerçekten ayrılmış bir sözcük değildir ve yalnızca uygun bağlamda bir anahtar sözcük gibi davranan bir bağlamsal anahtar sözcüğü, olduğunu unutmayın.|
|`static`|[Üyeler](members/index.md)|Bir yöntem veya bir tür örneği olmadan çağrılabilir özelliği veya bir türün tüm örnekleri arasında paylaşılan bir değer üyesi göstermek için kullanılır.|
|`struct`|[Yapılar](structures.md)<br /><br /> [Demetler](tuples.md)<br/><br/>[Kısıtlamalar](generics/constraints.md)|Bir yapı türü bildirmek için kullanılır.<br /><br/>Yapı tanımlama grubu belirtmek için kullanılır.<br/><br />Ayrıca genel parametre kısıtlama kullanılan.<br /><br />Modül tanımları OCaml uyumluluk için kullanılır.|
|`then`|[Koşullu ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Oluşturucular](members/constructors.md)|Koşullu ifadelerle birlikte kullanılır.<br /><br />Yan etkileri nesne oluşturmayı sonra gerçekleştirmek için de kullanılır.|
|`to`|[Döngüler: `for...to` İfade](loops-for-to-expression.md)|Kullanılan `for` döngüler aralık belirtmek için.|
|`true`|[İlkel Türler](primitive-types.md)|Bir Boolean değişmez değer olarak kullanılır.|
|`try`|[Özel durumlar: Try... with ifadesi](exception-handling/the-try-with-expression.md)<br /><br />[Özel durumlar: Try... finally ifadesi](exception-handling/the-try-finally-expression.md)|Bir özel durum oluşturabilecek bir kod bloğunu tanıtmak için kullanılır. İle birlikte kullanılan `with` veya `finally`.|
|`type`|[F# Türleri](fsharp-types.md)<br /><br />[Sınıflar](classes.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Yapılar](structures.md)<br /><br />[Sabit Listeleri](enumerations.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Tür Kısaltmaları](type-abbreviations.md)<br /><br />[Ölçü Birimleri](units-of-measure.md)|Bir sınıf, kayıt, yapısı, ayrılmış birleşim, numaralandırma türü, ölçü birimi bildirmek veya türü kısaltma için kullanılır.|
|`upcast`|[Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha yüksek bir türe dönüştürmek için kullanılır.|
|`use`|[Kaynak Yönetimi: `use` Anahtar Sözcüğü](resource-management-the-use-keyword.md)|Yerine kullanılan `let` gerekli değerler için `Dispose` kaynakları serbest bırakmak için çağrılabilir.|
|`use!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Yerine kullanılan `let!` zaman uyumsuz iş akışları ve gerekli değerler için diğer hesaplama ifadeleri `Dispose` kaynakları serbest bırakmak için çağrılabilir.|
|`val`|[Açık Alanlar: `val` Anahtar Sözcüğü](members/explicit-fields-the-val-keyword.md)<br /><br />[İmzalar](signatures.md)<br /><br />[Üyeler](members/index.md)|Bir değeri belirtmek için bir imza ya da bir tür sınırlı durumlarda bir üye bildirmek için kullanılır.|
|`void`|[İlkel Türler](primitive-types.md)|.NET gösterir `void` türü. Diğer .NET dilleri ile birlikte çalışırken kullanılır.|
|`when`|[Kısıtlamalar](generics/constraints.md)|Boole koşulları için kullanılan (*olduğunda cf*) desen ve bir genel tür parametresi için bir kısıtlama yan tümcesi dağıtır.|
|`while`|[Döngüler: `while...do` İfade](loops-while-do-expression.md)|Uvozuje konstruktor cyklu.|
|`with`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Nesne İfadeleri](object-expressions.md)<br /><br />[Kayıt İfadelerini Kopyalama ve Güncelleştirme](copy-and-update-record-expressions.md)<br /><br />[Tür Uzantıları](type-extensions.md)<br /><br />[Özel durumlar: `try...with` İfadesi](exception-handling/the-try-with-expression.md)|İle birlikte kullanılan `match` eşleştirme ifadesi deseninde anahtar sözcüğü. Ayrıca nesne ifadeleri, kayıt kopyalama ifadeleri ve tür uzantıları üye tanımları tanıtmak için ve özel durum işleyicileri tanıtmak için kullanılır.|
|`yield`|[Diziler](sequences.md)|Bir sıralama ifadesi bir dizi için bir değer üretmek için kullanılır.|
|`yield!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Verilen hesaplamayı ifadenin sonucu sonuçları içeren hesaplama ifadesi için bir koleksiyona eklenecek bir hesaplama ifadesinde kullanılır.|

Aşağıdaki belirteçler içinde ayrılmış F# OCaml dil anahtar sözcükleri oldukları için:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Kullanırsanız `--mlcompatibility` derleyici seçeneği, yukarıdaki anahtar sözcükler kullanılabilir tanımlayıcıları.

Aşağıdaki belirteçler gelecekteki genişleme için anahtar sözcükler olarak ayrılmış olan F# dil:

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

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Simge ve İşleç Başvurusu](symbol-and-operator-reference/index.md)
- [Derleyici Seçenekleri](compiler-options.md)
