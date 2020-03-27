---
title: Klavye Başvurusu
description: Tüm F# dil anahtar kelimeleri hakkında bilgi bağlantıları bulun.
f1_keywords:
- new_FS
- use_FS
- end_FS
- lsl_FS
- exception_FS
- asr_FS
- if_FS
- internal_FS
- default_FS
- in_FS
- lsr_FS
- open_FS
- static_FS
- assert_FS
- match_FS
- land_FS
- with_FS
- inherit_FS
- mutable_FS
- downto_FS
- false_FS
- sig_FS
- and_FS
- true_FS
- namespace_FS
- public_FS
- lxor_FS
- val_FS
- void_FS
- downcast_FS
- function_FS
- while_FS
- for_FS
- class_FS
- done_FS
- to_FS
- module_FS
- let_FS
- delegate_FS
- abstract_FS
- then_FS
- when_FS
- lazy_FS
- try_FS
- inline_FS
- do_FS
- upcast_FS
- begin_FS
- base_FS
- fun_FS
- struct_FS
- as_FS
- extern_FS
- null_FS
- lor_FS
- return_FS
- mod_FS
- private_FS
- of_FS
- or_FS
- member_FS
- type_FS
- rec_FS
- elif_FS
- override_FS
- interface_FS
- yield_FS
- else_FS
- finally_FS
- global_FS
- select_FS
- use!_FS
dev_langs:
- FSharp
ms.date: 11/04/2019
ms.openlocfilehash: 34959f471406643e85990c2c80a38a684759a7f9
ms.sourcegitcommit: b16eacb6f94a5b601882a861ad17cc5470a8d5d5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80352317"
---
# <a name="keyword-reference"></a>Klavye Başvurusu

Bu konu, tüm F# dil anahtar kelimeleri hakkında bilgi bağlantıları içerir.

## <a name="f-keyword-table"></a>F# Anahtar Kelime Tablosu

Aşağıdaki tabloda, tüm F# anahtar kelimeleri alfabetik sırayla, kısa açıklamalar ve daha fazla bilgi içeren ilgili konulara bağlantılar gösterilmektedir.

|Anahtar kelime|Bağlantı|Açıklama|
|-------|----|-----------|
|`abstract`|[Üyeler](./members/index.md)<br /><br />[Soyut Sınıflar](abstract-classes.md)|Beyan edildiği türde uygulama olmayan veya sanal olan ve varsayılan bir uygulaması olan bir yöntemi gösterir.|
|`and`|[`let`Bağlama](./functions/let-bindings.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Üyeler](./members/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Karşılıklı özyinelemeli bağlamalarda ve kayıtlarda, özellik bildirimlerinde ve genel parametrelerüzerinde birden çok kısıtlamayla kullanılır.|
|`as`|[Sınıflar](classes.md)<br /><br />[Desen Eşleştirme](Pattern-Matching.md)|Geçerli sınıf nesnesine bir nesne adı vermek için kullanılır. Ayrıca bir desen maç içinde bütün bir desen için bir ad vermek için kullanılır.|
|`assert`|[Onaylamalar](assertions.md)|Hata ayıklama sırasında kodu doğrulamak için kullanılır.|
|`base`|[Sınıflar](classes.md)<br /><br />[Devralma](inheritance.md)|Taban sınıf nesnesinin adı olarak kullanılır.|
|`begin`|[Ayrıntılı Sözdizimi](verbose-syntax.md)|Ayrıntılı sözdiziminde, kod bloğunun başlangıcını gösterir.|
|`class`|[Sınıflar](classes.md)|Ayrıntılı sözdiziminde, sınıf tanımının başlangıcını gösterir.|
|`default`|[Üyeler](./members/index.md)|Soyut bir yöntemin uygulanmasını gösterir; sanal bir yöntem oluşturmak için soyut bir yöntem bildirimi ile birlikte kullanılır.|
|`delegate`|[Temsilciler](delegates.md)|Bir temsilci ilan etmek için kullanılır.|
|`do`|[do Bağlamaları](./functions/do-bindings.md)<br /><br />[Döngüler: `for...to` İfade](loops-for-to-expression.md)<br /><br />[Döngüler: `for...in` İfade](loops-for-in-expression.md)<br /><br />[Döngüler: `while...do` İfade](loops-while-do-expression.md)|Döngü yapıları veya zorunlu kod yürütmek için kullanılır.|
|`done`|[Ayrıntılı Sözdizimi](verbose-syntax.md)|Ayrıntılı sözdiziminde, döngü ifadesinde bir kod bloğunun sonunu gösterir.|
|`downcast`|[Atama ve Dönüştürmeler](casting-and-conversions.md)|Kalıtım zincirinde daha düşük bir türe dönüştürmek için kullanılır.|
|`downto`|[Döngüler: `for...to` İfade](loops-for-to-expression.md)|Ters `for` sayma kullanılırken kullanılan bir ifadede.|
|`elif`|[Koşullu İfadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanmada kullanılır. Kısa bir `else if`form .|
|`else`|[Koşullu İfadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanmada kullanılır.|
|`end`|[Yapılar](structures.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Tür Genişletmeleri](type-extensions.md)<br /><br />[Ayrıntılı Sözdizimi](verbose-syntax.md)|Tür tanımlarında ve tür uzantılarında, üye tanımlarının bir bölümünün sonunu gösterir.<br /><br />Verbose sözdiziminde, `begin` anahtar kelimeyle başlayan bir kod bloğunun sonunu belirtmek için kullanılır.|
|`exception`|[Özel Durum İşleme](./exception-handling/index.md)<br /><br />[Özel Durum Türleri](./exception-handling/exception-types.md)|Özel durum türünü bildirmek için kullanılır.|
|`extern`|[Dış İşlevler](./functions/external-functions.md)|Bildirilen program öğesinin başka bir ikili veya derlemede tanımlandığını gösterir.|
|`false`|[İlkel Türler](basic-types.md)|Boolean edebi olarak kullanılır.|
|`finally`|[Özel Durumlar: `try...finally` İfade](./exception-handling/the-try-finally-expression.md)|Özel durum `try` oluşup oluşmadığına bakılmaksızın çalıştıran bir kod bloğu tanıtmak için birlikte kullanılır.|
|`fixed`|[Sabit](fixed.md)|Çöp toplanmasını önlemek için yığındaki bir işaretçiyi "sabitlemek" için kullanılır.|
|`for`|[Döngüler: `for...to` İfade](loops-for-to-expression.md)<br /><br />[Döngüler: for...in İfadesi](loops-for-in-expression.md)|Döngü yapılarda kullanılır.|
|`fun`|[Lambda İfadeler: `fun` Anahtar Kelime](./functions/lambda-expressions-the-fun-keyword.md)|Anonim işlevler olarak da bilinen lambda ifadelerinde kullanılır.|
|`function`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Lambda İfadeleri: fun Anahtar Sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)|`fun` Tek bir bağımsız değişkende desen `match` eşleşen bir lambda ifadesinde anahtar kelimeye ve ifadeye daha kısa bir alternatif olarak kullanılır.|
|`global`|[Ad Alanları](namespaces.md)|Üst düzey .NET ad alanına başvurmak için kullanılır.|
|`if`|[Koşullu İfadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanma yapılarında kullanılır.|
|`in`|[Döngüler: for...in İfadesi](loops-for-in-expression.md)<br /><br />[Ayrıntılı Sözdizimi](verbose-syntax.md)|Sıra ifadeleri ve ayrıntılı sözdiziminde ifadeleri bağlamalardan ayırmak için kullanılır.|
|`inherit`|[Devralma](inheritance.md)|Taban sınıf veya taban arabirimi belirtmek için kullanılır.|
|`inline`|[Işlev](./functions/index.md)<br /><br />[Satır İçi İşlevler](./functions/inline-functions.md)|Doğrudan arayanın koduna entegre edilmesi gereken bir işlevi belirtmek için kullanılır.|
|`interface`|[Arabirimler](interfaces.md)|Arabirimleri bildirmek ve uygulamak için kullanılır.|
|`internal`|[Erişim Denetimi](access-control.md)|Bir üyenin bir derlemenin içinde görünür olduğunu, ancak dışında olmadığını belirtmek için kullanılır.|
|`lazy`|[Gecikmeli İfadeler](lazy-expressions.md)|Yalnızca bir sonuç gerektiğinde gerçekleştirilecek bir ifadeyi belirtmek için kullanılır.|
|`let`|[`let`Bağlama](./functions/let-bindings.md)|Bir adı bir değere veya işleve ilişkilendirmek veya bağlamak için kullanılır.|
|`let!`|[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Bir adı asenkron hesaplama nın sonucuna bağlamak için asenkron iş akışlarında veya diğer hesaplama ifadelerinde, bir adı bir sonuca bağlamak için kullanılan ve hesaplama türünden olan bir sonuca bağlamak için kullanılır.|
|`match`|[Eşleşme İfadeleri](match-expressions.md)|Bir değeri bir desenle karşılaştırarak dallandırmak için kullanılır.|
|`match!`|[Hesaplama İfadeleri](computation-expressions.md#match)|Bir hesaplama ifadesive sonucuyla eşleşen desen için bir çağrının satır satırını almak için kullanılır.|
|`member`|[Üyeler](./members/index.md)|Nesne türünde bir özelliği veya yöntemi bildirmek için kullanılır.|
|`module`|[Modules](modules.md)|Bir adı mantıksal olarak diğer kodlardan ayırmak için ilgili türler, değerler ve işlevler grubuyla ilişkilendirmek için kullanılır.|
|`mutable`|[let Bağlamaları](./functions/let-bindings.md)|Bir değişkeni, yani değiştirilebilen bir değeri bildirmek için kullanılır.|
|`namespace`|[Ad Alanları](namespaces.md)|Bir adı mantıksal olarak diğer kodlardan ayırmak için ilgili tür ve modüllerden oluşan bir grupla ilişkilendirmek için kullanılır.|
|`new`|[Oluşturucular](./members/constructors.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Bir nesne oluşturan veya oluşturabilen bir oluşturucusu bildirmek, tanımlamak veya çağırmak için kullanılır.<br /><br />Ayrıca, bir türün belirli bir oluşturucuya sahip olması gerektiğini belirtmek için genel parametre kısıtlamalarında da kullanılır.|
|`not`|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Aslında bir anahtar kelime değil. Ancak, `not struct` birlikte genel bir parametre kısıtlaması olarak kullanılır.|
|`null`|[Boş Değerler](./values/null-values.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Nesnenin yokluğunu gösterir.<br /><br />Ayrıca genel parametre kısıtlamaları kullanılır.|
|`of`|[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Temsilciler](delegates.md)<br /><br />[Özel Durum Türleri](./exception-handling/exception-types.md)|Değer kategorilerinin türünü belirtmek için ayrımcı birliş ve temsilci ve özel durum bildirimlerinde kullanılır.|
|`open`|[İthalat Bildirimleri: `open` Anahtar Kelime](import-declarations-the-open-keyword.md)|Bir ad alanının veya modülün içeriğini niteliksiz olarak kullanılabilir hale getirmek için kullanılır.|
|`or`|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Boolean operatörleri olarak boolean `or` koşullarında kullanılır. `||`Eşdeğeri .<br /><br />Üye kısıtlamalarında da kullanılır.|
|`override`|[Üyeler](./members/index.md)|Temel sürümden farklı soyut veya sanal bir yöntemin sürümünü uygulamak için kullanılır.|
|`private`|[Erişim Denetimi](access-control.md)|Bir üyeye erişimi aynı türde veya modülde kodla sınırlandıran.|
|`public`|[Erişim Denetimi](access-control.md)|Bir üyeye dışarıdan giriş izni verir.|
|`rec`|[Işlev](./functions/index.md)|Bir işlevin özyinelemeli olduğunu belirtmek için kullanılır.|
|`return`|[Zaman Uyumsuz İş Akışları](Asynchronous-Workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Bir hesaplama ifadesinin sonucu olarak sağlamak için bir değer belirtmek için kullanılır.|
|`return!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Değerlendirildiğinde, içeren hesaplama ifadesinin sonucunu sağlayan bir hesaplama ifadesini belirtmek için kullanılır.|
|`select`|[Sorgu İfadeleri](query-expressions.md)|Sorgu ifadelerinde hangi alanların veya sütunların ayıklanması gerektiğini belirtmek için kullanılır. Bunun bağlamsal bir anahtar kelime olduğunu, bunun da aslında ayrılmış bir sözcük olmadığı ve yalnızca uygun bağlamda bir anahtar kelime gibi davrandığı anlamına geldiğini unutmayın.|
|`static`|[Üyeler](./members/index.md)|Bir tür örneği olmadan çağrılabilen bir yöntem veya özelliği veya bir türün tüm örnekleri arasında paylaşılan bir değer üyesini belirtmek için kullanılır.|
|`struct`|[Yapılar](structures.md)<br /><br /> [Demetler](tuples.md)<br/><br/>[Kısıtlamalar](./generics/constraints.md)|Yapı türünü bildirmek için kullanılır.<br /><br/>Bir yapı tuple belirtmek için kullanılır.<br/><br />Ayrıca genel parametre kısıtlamaları kullanılır.<br /><br />Modül tanımlarında OCaml uyumluluğu için kullanılır.|
|`then`|[Koşullu İfadeler:`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Oluşturucular](./members/constructors.md)|Koşullu ifadelerde kullanılır.<br /><br />Ayrıca nesne yapımından sonra yan etkileri gerçekleştirmek için kullanılır.|
|`to`|[Döngüler: `for...to` İfade](loops-for-to-expression.md)|Bir `for` aralığı belirtmek için döngüler halinde kullanılır.|
|`true`|[İlkel Türler](basic-types.md)|Boolean edebi olarak kullanılır.|
|`try`|[Özel Durumlar: try...with İfadesi](./exception-handling/the-try-with-expression.md)<br /><br />[Özel Durumlar: try...finally İfadesi](./exception-handling/the-try-finally-expression.md)|Özel durum oluşturabilecek bir kod bloğu tanıtmak için kullanılır. Birlikte kullanılır `with` `finally`veya .|
|`type`|[F# Türleri](fsharp-types.md)<br /><br />[Sınıflar](classes.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Yapılar](structures.md)<br /><br />[Numaralandırma](enumerations.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Tür Kısaltmaları](type-abbreviations.md)<br /><br />[Ölçü Birimleri](units-of-measure.md)|Bir sınıf, kayıt, yapı, ayrımcı birleşim, numaralandırma türü, ölçü birimi veya tür kısaltması bildirmek için kullanılır.|
|`upcast`|[Atama ve Dönüştürmeler](casting-and-conversions.md)|Kalıtım zincirinde daha yüksek bir türe dönüştürmek için kullanılır.|
|`use`|[Kaynak Yönetimi: `use` Anahtar Kelime](resource-management-the-use-keyword.md)|Özgür kaynaklariçin çağrılması gereken `let` `Dispose` değerler yerine kullanılır.|
|`use!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Serbest kaynaklara `let!` çağrılması gereken `Dispose` değerler için eşzamanlı iş akışları ve diğer hesaplama ifadeleri yerine kullanılır.|
|`val`|[Belirtik Alanlar: `val` Anahtar Sözcüğü](./members/explicit-fields-the-val-keyword.md)<br /><br />[İmzalar](signature-files.md)<br /><br />[Üyeler](./members/index.md)|Bir değeri belirtmek için imzada veya bir üyeyi sınırlı durumlarda beyan etmek için bir türde kullanılır.|
|`void`|[İlkel Türler](basic-types.md)|.NET `void` türünü gösterir. Diğer .NET dilleriyle çalışırken kullanılır.|
|`when`|[Kısıtlamalar](./generics/constraints.md)|Desen eşleşmelerinde Boolean koşulları *(korumaları)* için ve genel bir tür parametresi için bir kısıtlama yan tümcesi tanıtmak için kullanılır.|
|`while`|[Döngüler: `while...do` İfade](loops-while-do-expression.md)|Bir döngü yapısı tanıttı.|
|`with`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Nesne İfadeleri](object-expressions.md)<br /><br />[Kayıt İfadelerini Kopyalama ve Güncelleştirme](copy-and-update-record-expressions.md)<br /><br />[Tür Genişletmeleri](type-extensions.md)<br /><br />[Özel Durumlar: `try...with` İfade](./exception-handling/the-try-with-expression.md)|Desen eşleştirme `match` ifadelerinde anahtar kelimeyle birlikte kullanılır. Ayrıca nesne ifadeleri, kayıt kopyalama ifadeleri ve üye tanımları tanıtmak ve özel durum işleyicileri tanıtmak için uzantıları yazın kullanılır.|
|`yield`|[Listeler](lists.md), [Diziler](arrays.md), [Diziler](sequences.md)|Bir dizi için değer üretmek için liste, dizi veya sıra lı ifadede kullanılır. Çoğu durumda örtülü olduğu gibi genellikle atlanabilir.|
|`yield!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Belirli bir hesaplama ifadesinin sonucunu içeren hesaplama ifadesi için sonuç koleksiyonuna eklemek için bir hesaplama ifadesinde kullanılır.|

OCaml dilinde anahtar kelimeler olduğundan aşağıdaki belirteçler F# olarak ayrılmıştır:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

`--mlcompatibility` Derleyici seçeneğini kullanıyorsanız, yukarıdaki anahtar kelimeler tanımlayıcı olarak kullanılabilir.

Aşağıdaki belirteçler, F# dilinin gelecekteki genişlemesi için anahtar kelime olarak ayrılmıştır:

- `atomic`
- `break`
- `checked`
- `component`
- `const`
- `constraint`
- `constructor`
- `continue`
- `eager`
- `event`
- `external`
- `functor`
- `include`
- `method`
- `mixin`
- `object`
- `parallel`
- `process`
- `protected`
- `pure`
- `sealed`
- `tailcall`
- `trait`
- `virtual`
- `volatile`

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dil Referansı](index.md)
- [Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)
- [Derleyici Seçenekleri](compiler-options.md)
