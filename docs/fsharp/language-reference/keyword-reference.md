---
title: Klavye Başvurusu
description: 'Tüm F # dil anahtar kelimeleri hakkındaki bilgilerin bağlantılarını bulun.'
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
- const_FS
dev_langs:
- FSharp
ms.date: 08/15/2020
ms.openlocfilehash: 15505c123dd0d6497fbc80c8fc9f0910018911ea
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558107"
---
# <a name="keyword-reference"></a>Klavye Başvurusu

Bu konu, tüm F # dil anahtar kelimeleri hakkında bilgi bağlantıları içerir.

## <a name="f-keyword-table"></a>F # anahtar sözcük tablosu

Aşağıdaki tablo, tüm F # anahtar sözcüklerini kısa açıklamalarla ve daha fazla bilgi içeren ilgili konuların bağlantılarıyla birlikte alfabetik sırayla gösterir.

|Sözcükle|Bağlantı|Açıklama|
|-------|----|-----------|
|`abstract`|[Üyeler](./members/index.md)<br /><br />[Soyut sınıflar](abstract-classes.md)|İçinde, bildirildiği veya sanal olan ve varsayılan bir uygulamaya sahip olan türde hiçbir uygulamaya sahip olmayan bir yöntemi gösterir.|
|`and`|[`let` Lara](./functions/let-bindings.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Üyeler](./members/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Karşılıklı özyinelemeli bağlamalar ve kayıtlarda, özellik bildirimlerinde ve genel parametrelerde birden çok kısıtlama ile kullanılır.|
|`as`|[Sınıflar](classes.md)<br /><br />[Model eşleştirme](Pattern-Matching.md)|Geçerli sınıf nesnesine bir nesne adı vermek için kullanılır. Ayrıca, bir model eşleşmesi içindeki tam bir düzene bir ad vermek için kullanılır.|
|`assert`|[Onaylamalar](assertions.md)|Hata ayıklama sırasında kodu doğrulamak için kullanılır.|
|`base`|[Sınıflar](classes.md)<br /><br />[Devralma](inheritance.md)|Temel sınıf nesnesinin adı olarak kullanılır.|
|`begin`|[Ayrıntılı Sözdizimi](verbose-syntax.md)|Ayrıntılı söz diziminde kod bloğunun başlangıcını gösterir.|
|`class`|[Sınıflar](classes.md)|Ayrıntılı söz diziminde, bir sınıf tanımının başlangıcını gösterir.|
|`default`|[Üyeler](./members/index.md)|Soyut yöntemin bir uygulamasını belirtir; bir sanal yöntem oluşturmak için soyut Yöntem bildirimiyle birlikte kullanılır.|
|`delegate`|[Temsilciler](delegates.md)|Bir temsilciyi bildirmek için kullanılır.|
|`do`|[do Bağlamaları](./functions/do-bindings.md)<br /><br />[Döngüler: `for...to` ifade](loops-for-to-expression.md)<br /><br />[Döngüler: `for...in` ifade](loops-for-in-expression.md)<br /><br />[Döngüler: `while...do` ifade](loops-while-do-expression.md)|Döngü yapıları içinde veya kesinlik temelli kodu yürütmek için kullanılır.|
|`done`|[Ayrıntılı Sözdizimi](verbose-syntax.md)|Ayrıntılı söz diziminde, bir döngü ifadesinde bir kod bloğunun sonunu gösterir.|
|`downcast`|[Atama ve Dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha düşük olan bir türe dönüştürmek için kullanılır.|
|`downto`|[Döngüler: `for...to` ifade](loops-for-to-expression.md)|Bir `for` ifadede, ters sayım sırasında kullanılır.|
|`elif`|[Koşullu Ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallandırma içinde kullanılır. Kısa bir biçimi `else if` .|
|`else`|[Koşullu Ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallandırma içinde kullanılır.|
|`end`|[Yapılar](structures.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Tür Genişletmeleri](type-extensions.md)<br /><br />[Ayrıntılı Sözdizimi](verbose-syntax.md)|Tür tanımlarında ve tür uzantılarında, üye tanımlarının bir bölümünün sonunu belirtir.<br /><br />Ayrıntılı söz diziminde, anahtar sözcüğüyle başlayan bir kod bloğunun sonunu belirtmek için kullanılır `begin` .|
|`exception`|[Özel Durum İşleme](./exception-handling/index.md)<br /><br />[Özel Durum Türleri](./exception-handling/exception-types.md)|Bir özel durum türü bildirmek için kullanılır.|
|`extern`|[Dış İşlevler](./functions/external-functions.md)|Belirtilen bir program öğesinin başka bir ikili veya derlemede tanımlandığını gösterir.|
|`false`|[İlkel Türler](basic-types.md)|Boolean sabit değeri olarak kullanılır.|
|`finally`|[Özel durumlar: `try...finally` ifade](./exception-handling/the-try-finally-expression.md)|`try`Bir özel durumun gerçekleşmediğine bakılmaksızın yürütülen bir kod bloğunu tanıtmak için ile birlikte kullanılır.|
|`fixed`|[Düzenle](fixed.md)|Atık olarak toplanmasını engellemek için yığında bir işaretçiyi "sabitlemek" için kullanılır.|
|`for`|[Döngüler: `for...to` ifade](loops-for-to-expression.md)<br /><br />[Döngüler: for...in İfadesi](loops-for-in-expression.md)|Döngü yapılarında kullanılır.|
|`fun`|[Lambda Ifadeleri: `fun` anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)|Anonim işlevler olarak da bilinen Lambda ifadelerinde kullanılır.|
|`function`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Lambda Ifadeleri: Fun anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)|Anahtar kelimesine daha kısa bir alternatif olarak `fun` ve `match` tek bir bağımsız değişkende kalıp eşleşmesi olan bir lambda ifadesinde bir ifadeye kullanılır.|
|`global`|[Ad alanları](namespaces.md)|Üst düzey .NET ad alanına başvurmak için kullanılır.|
|`if`|[Koşullu Ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanma yapılarında kullanılır.|
|`in`|[Döngüler: for...in İfadesi](loops-for-in-expression.md)<br /><br />[Ayrıntılı Sözdizimi](verbose-syntax.md)|Deyimleri bağlamalardan ayırmak için dizi ifadeleri ve ayrıntılı sözdiziminde kullanılır.|
|`inherit`|[Devralma](inheritance.md)|Temel sınıf veya temel arabirim belirtmek için kullanılır.|
|`inline`|[İşlevler](./functions/index.md)<br /><br />[Satır İçi İşlevler](./functions/inline-functions.md)|Doğrudan çağıranın koduna tümleştirilmesi gereken bir işlevi göstermek için kullanılır.|
|`interface`|[Arabirimler](interfaces.md)|Arabirimleri bildirmek ve uygulamak için kullanılır.|
|`internal`|[Access Control](access-control.md)|Bir üyenin bir derlemenin içinde görünür olduğunu ancak dışarıda olduğunu belirtmek için kullanılır.|
|`lazy`|[Gecikmeli İfadeler](lazy-expressions.md)|Yalnızca bir sonuç gerektiğinde gerçekleştirilecek bir ifade belirtmek için kullanılır.|
|`let`|[`let` Lara](./functions/let-bindings.md)|Bir adı bir değer veya işleve ilişkilendirmek veya bağlamak için kullanılır.|
|`let!`|[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Bir adı zaman uyumsuz bir hesaplamanın sonucuna bağlamak için zaman uyumsuz iş akışlarında veya bir adı, hesaplama türü olan bir sonuca bağlamak için kullanılan diğer hesaplama ifadelerinde kullanılır.|
|`match`|[Eşleşme İfadeleri](match-expressions.md)|Bir değeri bir düzeniyle karşılaştırarak dallandırma için kullanılır.|
|`match!`|[Hesaplama İfadeleri](computation-expressions.md#match)|Bir hesaplama ifadesine çağrı ve sonuç olarak bir model eşleşmesi için kullanılır.|
|`member`|[Üyeler](./members/index.md)|Bir nesne türünde bir özelliği veya yöntemi bildirmek için kullanılır.|
|`module`|[Modül](modules.md)|Bir adı ilgili türler, değerler ve işlevler grubuyla ilişkilendirmek için kullanılır, bu da diğer koddan mantıksal olarak ayrılır.|
|`mutable`|[let Bağlamaları](./functions/let-bindings.md)|Değişken, yani değiştirilebilen bir değer bildirmek için kullanılır.|
|`namespace`|[Ad alanları](namespaces.md)|Bir adı ilgili türler ve modüller grubuyla ilişkilendirmek için kullanılır, diğer koddan mantıksal olarak ayırın.|
|`new`|[Oluşturucular](./members/constructors.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Bir nesnesi oluşturan ya da oluşturabileceğiniz bir oluşturucuyu bildirmek, tanımlamak veya çağırmak için kullanılır.<br /><br />Ayrıca, bir türün belirli bir oluşturucuya sahip olması gerektiğini göstermek için genel parametre kısıtlamalarında de kullanılır.|
|`not`|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Gerçekte bir anahtar sözcük değil. Ancak, `not struct` içinde genel parametre kısıtlaması olarak kullanılır.|
|`null`|[Null değerler](./values/null-values.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Bir nesnenin yokluğunu gösterir.<br /><br />Genel parametre kısıtlamalarında de kullanılır.|
|`of`|[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Temsilciler](delegates.md)<br /><br />[Özel Durum Türleri](./exception-handling/exception-types.md)|Değer kategorilerinin türünü ve temsilci ve özel durum bildirimlerini göstermek için ayrılmış birleşimlerde kullanılır.|
|`open`|[İçeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md)|Bir ad alanının veya modülün içeriğini nitelemeden kullanılabilir hale getirmek için kullanılır.|
|`or`|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Boole koşulları ile Boolean işleci olarak kullanılır `or` . İle eşdeğerdir `||` .<br /><br />Üye kısıtlamalarında da kullanılır.|
|`override`|[Üyeler](./members/index.md)|Temel sürümden farklı bir soyut veya sanal yöntemin sürümünü uygulamak için kullanılır.|
|`private`|[Access Control](access-control.md)|Aynı türdeki veya modüldeki bir üyeye erişimi bir koda kısıtlar.|
|`public`|[Access Control](access-control.md)|Tür dışından bir üyeye erişime izin verir.|
|`rec`|[İşlevler](./functions/index.md)|Bir işlevin özyinelemeli olduğunu göstermek için kullanılır.|
|`return`|[Zaman Uyumsuz İş Akışları](Asynchronous-Workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Hesaplama ifadesinin sonucu olarak sağlanacak bir değeri belirtmek için kullanılır.|
|`return!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Değerlendirildiğinde, kapsayan hesaplama ifadesinin sonucunu sağlayan bir hesaplama ifadesi belirtmek için kullanılır.|
|`select`|[Sorgu İfadeleri](query-expressions.md)|Ayıklanacak alanları veya sütunları belirtmek için sorgu ifadelerinde kullanılır. Bu, aslında ayrılmış bir sözcük değil ve yalnızca uygun bağlamda anahtar sözcük gibi davranan bir bağlamsal anahtar sözcüktür.|
|`static`|[Üyeler](./members/index.md)|Bir türün örneği olmadan çağrılabilecek bir yöntemi veya özelliği ya da bir türün tüm örnekleri arasında paylaşılan bir değer üyesini göstermek için kullanılır.|
|`struct`|[Yapılar](structures.md)<br /><br /> [Demetler](tuples.md)<br/><br/>[Kısıtlamalar](./generics/constraints.md)|Bir yapı türünü bildirmek için kullanılır.<br /><br/>Yapı tanımlama grubu belirtmek için kullanılır.<br/><br />Genel parametre kısıtlamalarında de kullanılır.<br /><br />Modül tanımlarında OCaml uyumluluğu için kullanılır.|
|`then`|[Koşullu Ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Oluşturucular](./members/constructors.md)|Koşullu ifadelerde kullanılır.<br /><br />Nesne oluşturulduktan sonra yan etkileri gerçekleştirmek için de kullanılır.|
|`to`|[Döngüler: `for...to` ifade](loops-for-to-expression.md)|`for`Bir aralığı göstermek için Döngülerde kullanılır.|
|`true`|[İlkel Türler](basic-types.md)|Boolean sabit değeri olarak kullanılır.|
|`try`|[Özel Durumlar: try...with İfadesi](./exception-handling/the-try-with-expression.md)<br /><br />[Özel Durumlar: try...finally İfadesi](./exception-handling/the-try-finally-expression.md)|Özel durum oluşturabilen bir kod bloğunu tanıtmak için kullanılır. Veya ile birlikte `with` kullanılır `finally` .|
|`type`|[F# Türleri](fsharp-types.md)<br /><br />[Sınıflar](classes.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Yapılar](structures.md)<br /><br />[Numaralandırmalar](enumerations.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Tür Kısaltmaları](type-abbreviations.md)<br /><br />[Ölçü Birimleri](units-of-measure.md)|Bir sınıf, kayıt, yapı, ayırt edici birleşim, numaralandırma türü, ölçü birimi veya tür kısaltması bildirmek için kullanılır.|
|`upcast`|[Atama ve Dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha üst bir türe dönüştürmek için kullanılır.|
|`use`|[Kaynak yönetimi: `use` anahtar sözcüğü](resource-management-the-use-keyword.md)|`let`Serbest kaynaklar için çağrılması gereken değerler için yerine kullanılır `Dispose` .|
|`use!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|`let!`Zaman uyumsuz iş akışları ve `Dispose` boş kaynaklar için çağrılması gereken değerler için diğer hesaplama ifadeleri yerine kullanılır.|
|`val`|[Açık alanlar: `val` anahtar sözcük](./members/explicit-fields-the-val-keyword.md)<br /><br />[İmzalar](signature-files.md)<br /><br />[Üyeler](./members/index.md)|Bir değeri belirtmek için bir imzada veya bir üyeyi bildirmek için bir tür içinde, sınırlı durumlarda kullanılır.|
|`void`|[İlkel Türler](basic-types.md)|.NET türünü gösterir `void` . Diğer .NET dilleri ile birlikte çalışırken kullanılır.|
|`when`|[Kısıtlamalar](./generics/constraints.md)|Bir genel tür parametresi için bir kısıtlama yan tümcesi tanıtmak üzere, desenli Boole koşulları (*korumaları olduğunda*) için kullanılır.|
|`while`|[Döngüler: `while...do` ifade](loops-while-do-expression.md)|Bir döngü yapısı tanıtır.|
|`with`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Nesne İfadeleri](object-expressions.md)<br /><br />[Kayıt İfadelerini Kopyalama ve Güncelleştirme](copy-and-update-record-expressions.md)<br /><br />[Tür Genişletmeleri](type-extensions.md)<br /><br />[Özel durumlar: `try...with` ifade](./exception-handling/the-try-with-expression.md)|`match`Model eşleştirme ifadelerinde anahtar sözcüğü ile birlikte kullanılır. Ayrıca, nesne ifadelerinde, üye tanımlarını tanıtmak ve özel durum işleyicilerini tanıtmak için tür uzantıları kaydetmek için kullanılır.|
|`yield`|[Listeler](lists.md), [diziler](arrays.md), [diziler](sequences.md)|Bir dizi için değer üretmek üzere bir liste, dizi veya dizi ifadesinde kullanılır. Genellikle, çoğu durumda örtük olduğu için atlanabilir.|
|`yield!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Belirli bir hesaplama ifadesinin sonucunu, kapsayan hesaplama ifadesi için bir sonuç koleksiyonuna eklemek üzere bir hesaplama ifadesinde kullanılır.|
|`const`|[Tür Sağlayıcıları](../tutorials/type-providers/index.md)| Tür sağlayıcıları `const` tür parametresi bağımsız değişkeni olarak sabit bir sabit değer belirtmek için anahtar sözcük olarak kullanılmasına izin verir.|

OCaml dilinde anahtar sözcükler olduklarından aşağıdaki belirteçler F # içinde ayrılmıştır:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

`--mlcompatibility`Derleyici seçeneğini kullanırsanız yukarıdaki anahtar sözcükler tanımlayıcı olarak kullanılabilir.

Aşağıdaki belirteçler F # dilinin gelecek genişletmesi için anahtar sözcük olarak ayrılmıştır:

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

- [F # dil başvurusu](index.md)
- [Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)
- [Derleyici seçenekleri](compiler-options.md)
