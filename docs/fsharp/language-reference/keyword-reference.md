---
title: Klavye Başvurusu
description: Tüm F# dil anahtar kelimeleri hakkındaki bilgilerin bağlantılarını bulun.
ms.date: 05/16/2016
ms.openlocfilehash: 8c2df9d081caae48489e3e316ca158f3b9106efb
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107034"
---
# <a name="keyword-reference"></a>Klavye Başvurusu

Bu konu, tüm F# dil anahtar kelimeleri hakkında bilgi bağlantıları içerir.

## <a name="f-keyword-table"></a>F#Anahtar sözcük tablosu

Aşağıdaki tabloda, kısa açıklamalarla F# birlikte tüm anahtar sözcükler ve daha fazla bilgi içeren ilgili konuların bağlantıları gösterilmektedir.

|Anahtar sözcüğü|Bağlantı|Açıklama|
|-------|----|-----------|
|`abstract`|[Üyeler](./members/index.md)<br /><br />[Soyut Sınıflar](abstract-classes.md)|İçinde, bildirildiği veya sanal olan ve varsayılan bir uygulamaya sahip olan türde hiçbir uygulamaya sahip olmayan bir yöntemi gösterir.|
|`and`|[`let`Lara](./functions/let-bindings.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Üyeler](./members/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Karşılıklı özyinelemeli bağlamalar ve kayıtlarda, özellik bildirimlerinde ve genel parametrelerde birden çok kısıtlama ile kullanılır.|
|`as`|[Sınıflar](classes.md)<br /><br />[Desen Eşleştirme](Pattern-Matching.md)|Geçerli sınıf nesnesine bir nesne adı vermek için kullanılır. Ayrıca, bir model eşleşmesi içindeki tam bir düzene bir ad vermek için kullanılır.|
|`assert`|[Onaylamalar](assertions.md)|Hata ayıklama sırasında kodu doğrulamak için kullanılır.|
|`base`|[Sınıflar](classes.md)<br /><br />[Devralma](inheritance.md)|Temel sınıf nesnesinin adı olarak kullanılır.|
|`begin`|[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Ayrıntılı söz diziminde kod bloğunun başlangıcını gösterir.|
|`class`|[Sınıflar](classes.md)|Ayrıntılı söz diziminde, bir sınıf tanımının başlangıcını gösterir.|
|`default`|[Üyeler](./members/index.md)|Soyut yöntemin bir uygulamasını belirtir; bir sanal yöntem oluşturmak için soyut Yöntem bildirimiyle birlikte kullanılır.|
|`delegate`|[Temsilciler](delegates.md)|Bir temsilciyi bildirmek için kullanılır.|
|`do`|[do Bağlamaları](./functions/do-bindings.md)<br /><br />[Lerin `for...to`İfadesini](loops-for-to-expression.md)<br /><br />[Lerin `for...in`İfadesini](loops-for-in-expression.md)<br /><br />[Lerin `while...do`İfadesini](loops-while-do-expression.md)|Döngü yapıları içinde veya kesinlik temelli kodu yürütmek için kullanılır.|
|`done`|[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Ayrıntılı söz diziminde, bir döngü ifadesinde bir kod bloğunun sonunu gösterir.|
|`downcast`|[Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha düşük olan bir türe dönüştürmek için kullanılır.|
|`downto`|[Lerin `for...to`İfadesini](loops-for-to-expression.md)|Bir `for` ifadede, ters sayım sırasında kullanılır.|
|`elif`|[Koşullu Ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallandırma içinde kullanılır. Kısa bir biçimi `else if`.|
|`else`|[Koşullu Ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallandırma içinde kullanılır.|
|`end`|[Yapılar](structures.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Tür Uzantıları](type-extensions.md)<br /><br />[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Tür tanımlarında ve tür uzantılarında, üye tanımlarının bir bölümünün sonunu belirtir.<br /><br />Ayrıntılı söz diziminde, `begin` anahtar sözcüğüyle başlayan bir kod bloğunun sonunu belirtmek için kullanılır.|
|`exception`|[Özel Durum İşleme](./exception-handling/index.md)<br /><br />[Özel Durum Türleri](./exception-handling/exception-types.md)|Bir özel durum türü bildirmek için kullanılır.|
|`extern`|[Dış İşlevler](./functions/external-functions.md)|Belirtilen bir program öğesinin başka bir ikili veya derlemede tanımlandığını gösterir.|
|`false`|[İlkel Türler](primitive-types.md)|Boolean sabit değeri olarak kullanılır.|
|`finally`|[Özel Durumlar: `try...finally` İfade](./exception-handling/the-try-finally-expression.md)|Bir özel durumun `try` gerçekleşmediğine bakılmaksızın yürütülen bir kod bloğunu tanıtmak için ile birlikte kullanılır.|
|`fixed`|[Düzenle](fixed.md)|Atık olarak toplanmasını engellemek için yığında bir işaretçiyi "sabitlemek" için kullanılır.|
|`for`|[Lerin `for...to`İfadesini](loops-for-to-expression.md)<br /><br />[Döngüler: for...in İfadesi](loops-for-in-expression.md)|Döngü yapılarında kullanılır.|
|`fun`|[Lambda Ifadeleri: `fun` Anahtar Sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)|Anonim işlevler olarak da bilinen Lambda ifadelerinde kullanılır.|
|`function`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Lambda Ifadeleri: Eğlenceli anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)|`fun` Anahtar kelimesine daha kısa bir alternatif olarak ve tek `match` bir bağımsız değişkende kalıp eşleşmesi olan bir lambda ifadesinde bir ifadeye kullanılır.|
|`global`|[Ad Alanları](namespaces.md)|Üst düzey .NET ad alanına başvurmak için kullanılır.|
|`if`|[Koşullu Ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Koşullu dallanma yapılarında kullanılır.|
|`in`|[Döngüler: for...in İfadesi](loops-for-in-expression.md)<br /><br />[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Deyimleri bağlamalardan ayırmak için dizi ifadeleri ve ayrıntılı sözdiziminde kullanılır.|
|`inherit`|[Devralma](inheritance.md)|Temel sınıf veya temel arabirim belirtmek için kullanılır.|
|`inline`|[İşlevler](./functions/index.md)<br /><br />[Satır İçi İşlevler](./functions/inline-functions.md)|Doğrudan çağıranın koduna tümleştirilmesi gereken bir işlevi göstermek için kullanılır.|
|`interface`|[Arabirimler](interfaces.md)|Arabirimleri bildirmek ve uygulamak için kullanılır.|
|`internal`|[Erişim Denetimi](access-control.md)|Bir üyenin bir derlemenin içinde görünür olduğunu ancak dışarıda olduğunu belirtmek için kullanılır.|
|`lazy`|[Gecikmeli İfadeler](lazy-expressions.md)|Yalnızca bir sonuç gerektiğinde gerçekleştirilecek bir ifade belirtmek için kullanılır.|
|`let`|[`let`Lara](./functions/let-bindings.md)|Bir adı bir değer veya işleve ilişkilendirmek veya bağlamak için kullanılır.|
|`let!`|[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Bir adı zaman uyumsuz bir hesaplamanın sonucuna bağlamak için zaman uyumsuz iş akışlarında veya bir adı, hesaplama türü olan bir sonuca bağlamak için kullanılan diğer hesaplama ifadelerinde kullanılır.|
|`match`|[Eşleşme İfadeleri](match-expressions.md)|Bir değeri bir düzeniyle karşılaştırarak dallandırma için kullanılır.|
|`match!`|[Hesaplama İfadeleri](computation-expressions.md#match)|Bir hesaplama ifadesine çağrı ve sonuç olarak bir model eşleşmesi için kullanılır.|
|`member`|[Üyeler](./members/index.md)|Bir nesne türünde bir özelliği veya yöntemi bildirmek için kullanılır.|
|`module`|[Modüller](modules.md)|Bir adı ilgili türler, değerler ve işlevler grubuyla ilişkilendirmek için kullanılır, bu da diğer koddan mantıksal olarak ayrılır.|
|`mutable`|[let Bağlamaları](./functions/let-bindings.md)|Değişken, yani değiştirilebilen bir değer bildirmek için kullanılır.|
|`namespace`|[Ad Alanları](namespaces.md)|Bir adı ilgili türler ve modüller grubuyla ilişkilendirmek için kullanılır, diğer koddan mantıksal olarak ayırın.|
|`new`|[Oluşturucular](./members/constructors.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Bir nesnesi oluşturan ya da oluşturabileceğiniz bir oluşturucuyu bildirmek, tanımlamak veya çağırmak için kullanılır.<br /><br />Ayrıca, bir türün belirli bir oluşturucuya sahip olması gerektiğini göstermek için genel parametre kısıtlamalarında de kullanılır.|
|`not`|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Gerçekte bir anahtar sözcük değil. Ancak, `not struct` içinde genel parametre kısıtlaması olarak kullanılır.|
|`null`|[Null Değerler](./values/null-values.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Bir nesnenin yokluğunu gösterir.<br /><br />Genel parametre kısıtlamalarında de kullanılır.|
|`of`|[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Temsilciler](delegates.md)<br /><br />[Özel Durum Türleri](./exception-handling/exception-types.md)|Değer kategorilerinin türünü ve temsilci ve özel durum bildirimlerini göstermek için ayrılmış birleşimlerde kullanılır.|
|`open`|[Önemli Bildirimler: `open` Anahtar Sözcüğü](import-declarations-the-open-keyword.md)|Bir ad alanının veya modülün içeriğini nitelemeden kullanılabilir hale getirmek için kullanılır.|
|`or`|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)<br /><br />[Kısıtlamalar](./generics/constraints.md)|Boole koşulları ile Boolean `or` işleci olarak kullanılır. İle `||`eşdeğerdir.<br /><br />Üye kısıtlamalarında da kullanılır.|
|`override`|[Üyeler](./members/index.md)|Temel sürümden farklı bir soyut veya sanal yöntemin sürümünü uygulamak için kullanılır.|
|`private`|[Erişim Denetimi](access-control.md)|Aynı türdeki veya modüldeki bir üyeye erişimi bir koda kısıtlar.|
|`public`|[Erişim Denetimi](access-control.md)|Tür dışından bir üyeye erişime izin verir.|
|`rec`|[İşlevler](./functions/index.md)|Bir işlevin özyinelemeli olduğunu göstermek için kullanılır.|
|`return`|[Zaman Uyumsuz İş Akışları](Asynchronous-Workflows.md)<br /><br />[Hesaplama İfadeleri](computation-expressions.md)|Hesaplama ifadesinin sonucu olarak sağlanacak bir değeri belirtmek için kullanılır.|
|`return!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Değerlendirildiğinde, kapsayan hesaplama ifadesinin sonucunu sağlayan bir hesaplama ifadesi belirtmek için kullanılır.|
|`select`|[Sorgu İfadeleri](query-expressions.md)|Ayıklanacak alanları veya sütunları belirtmek için sorgu ifadelerinde kullanılır. Bu, aslında ayrılmış bir sözcük değil ve yalnızca uygun bağlamda anahtar sözcük gibi davranan bir bağlamsal anahtar sözcüktür.|
|`static`|[Üyeler](./members/index.md)|Bir türün örneği olmadan çağrılabilecek bir yöntemi veya özelliği ya da bir türün tüm örnekleri arasında paylaşılan bir değer üyesini göstermek için kullanılır.|
|`struct`|[Yapılar](structures.md)<br /><br /> [Demetler](tuples.md)<br/><br/>[Kısıtlamalar](./generics/constraints.md)|Bir yapı türünü bildirmek için kullanılır.<br /><br/>Yapı tanımlama grubu belirtmek için kullanılır.<br/><br />Genel parametre kısıtlamalarında de kullanılır.<br /><br />Modül tanımlarında OCaml uyumluluğu için kullanılır.|
|`then`|[Koşullu Ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Oluşturucular](./members/constructors.md)|Koşullu ifadelerde kullanılır.<br /><br />Nesne oluşturulduktan sonra yan etkileri gerçekleştirmek için de kullanılır.|
|`to`|[Lerin `for...to`İfadesini](loops-for-to-expression.md)|Bir aralığı göstermek için Döngülerdekullanılır.`for`|
|`true`|[İlkel Türler](primitive-types.md)|Boolean sabit değeri olarak kullanılır.|
|`try`|[Özel Durumlar: TRY... with Ifadesi](./exception-handling/the-try-with-expression.md)<br /><br />[Özel Durumlar: TRY... finally Ifadesi](./exception-handling/the-try-finally-expression.md)|Özel durum oluşturabilen bir kod bloğunu tanıtmak için kullanılır. `with` Veya`finally`ile birlikte kullanılır.|
|`type`|[F# Türleri](fsharp-types.md)<br /><br />[Sınıflar](classes.md)<br /><br />[Kayıtlar](records.md)<br /><br />[Yapılar](structures.md)<br /><br />[Sabit Listeleri](enumerations.md)<br /><br />[Ayrılmış Birleşimler](discriminated-unions.md)<br /><br />[Tür Kısaltmaları](type-abbreviations.md)<br /><br />[Ölçü Birimleri](units-of-measure.md)|Bir sınıf, kayıt, yapı, ayırt edici birleşim, numaralandırma türü, ölçü birimi veya tür kısaltması bildirmek için kullanılır.|
|`upcast`|[Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)|Devralma zincirinde daha üst bir türe dönüştürmek için kullanılır.|
|`use`|[Kaynak yönetimi: `use` Anahtar Sözcüğü](resource-management-the-use-keyword.md)|Serbest kaynaklar için `let` çağrılması gereken değerler `Dispose` için yerine kullanılır.|
|`use!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Zaman uyumsuz iş `let!` akışları ve boş kaynaklar için çağrılması `Dispose` gereken değerler için diğer hesaplama ifadeleri yerine kullanılır.|
|`val`|[Açık Alanlar: `val` Anahtar Sözcüğü](./members/explicit-fields-the-val-keyword.md)<br /><br />[İmzalar](signatures.md)<br /><br />[Üyeler](./members/index.md)|Bir değeri belirtmek için bir imzada veya bir üyeyi bildirmek için bir tür içinde, sınırlı durumlarda kullanılır.|
|`void`|[İlkel Türler](primitive-types.md)|.Net `void` türünü gösterir. Diğer .NET dilleri ile birlikte çalışırken kullanılır.|
|`when`|[Kısıtlamalar](./generics/constraints.md)|Bir genel tür parametresi için bir kısıtlama yan tümcesi tanıtmak üzere, desenli Boole koşulları (*korumaları olduğunda*) için kullanılır.|
|`while`|[Lerin `while...do`İfadesini](loops-while-do-expression.md)|Bir döngü yapısı tanıtır.|
|`with`|[Eşleşme İfadeleri](match-expressions.md)<br /><br />[Nesne İfadeleri](object-expressions.md)<br /><br />[Kayıt İfadelerini Kopyalama ve Güncelleştirme](copy-and-update-record-expressions.md)<br /><br />[Tür Uzantıları](type-extensions.md)<br /><br />[Özel Durumlar: `try...with` İfade](./exception-handling/the-try-with-expression.md)|Model eşleştirme ifadelerinde `match` anahtar sözcüğü ile birlikte kullanılır. Ayrıca, nesne ifadelerinde, üye tanımlarını tanıtmak ve özel durum işleyicilerini tanıtmak için tür uzantıları kaydetmek için kullanılır.|
|`yield`|[Diziler](sequences.md)|Bir dizi için değer üretmek üzere bir dizi ifadesinde kullanılır.|
|`yield!`|[Hesaplama İfadeleri](computation-expressions.md)<br /><br />[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Belirli bir hesaplama ifadesinin sonucunu, kapsayan hesaplama ifadesi için bir sonuç koleksiyonuna eklemek üzere bir hesaplama ifadesinde kullanılır.|

Aşağıdaki belirteçler, OCaml dilinde F# anahtar sözcükler olduklarından ' de ayrılmıştır:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

`--mlcompatibility` Derleyici seçeneğini kullanırsanız yukarıdaki anahtar sözcükler tanımlayıcı olarak kullanılabilir.

Aşağıdaki belirteçler, F# dilin daha sonra genişletilmesi için anahtar sözcük olarak ayrılmıştır:

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

- [F# Dili Başvurusu](index.md)
- [Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)
- [Derleyici Seçenekleri](compiler-options.md)
