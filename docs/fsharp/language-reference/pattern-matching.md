---
title: Desen Eşleştirme
description: 'Verileri mantıksal yapılara göre karşılaştırmak, verileri yapısal parçalar halinde çıkarmak veya verilerden bilgi ayıklamak için F # içinde desenlerin nasıl kullanıldığını öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 6d284b941824bc15a8e872a4e28e22c0e159191d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811515"
---
# <a name="pattern-matching"></a>Desen Eşleştirme

Desenler, giriş verilerini dönüştürmek için kurallardır. Verileri bir mantıksal yapı veya yapılarla karşılaştırmak, verileri yapısal parçalar halinde çıkarmak veya verileri çeşitli yollarla ayıklamak için F # dilinde kullanılır.

## <a name="remarks"></a>Açıklamalar

Desenler, ifadesi gibi birçok dil yapılarında kullanılır `match` . `let`Bağlamalar, lambda ifadeleri ve ifadeyle ilişkili özel durum işleyicilerde işlevler için bağımsız değişkenleri işlerken kullanılırlar `try...with` . Daha fazla bilgi için bkz. [Match ifadeleri](match-expressions.md), [Let bağlamaları](./functions/let-bindings.md), [lambda Ifadeleri: `fun` anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)ve [özel durumlar: `try...with` ifade](./exception-handling/the-try-with-expression.md).

Örneğin, `match` ifadesinde, *Düzen* kanal sembolünü izleyen şeydir.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Her bir model girişi bir şekilde dönüştürmek için bir kural işlevi görür. `match`İfadesinde, her bir model, giriş verilerinin örüntüle uyumlu olup olmadığını görmek için sırasıyla incelenir. Bir eşleşme bulunursa sonuç ifadesi yürütülür. Bir eşleşme bulunmazsa, sonraki model kuralı test edilir. *Koşul* bölümü [eşleşme ifadeleriyle](match-expressions.md)açıklandığında isteğe bağlı.

Desteklenen desenler aşağıdaki tabloda gösterilmiştir. Çalışma zamanında, giriş, tabloda listelenen sırada aşağıdaki desenlerden her birine karşı test edilir ve desenler yinelemeli olarak, kodunuzda göründükleri gibi ve her satırdaki desenler için soldan sağa uygulanır.

|Ad|Açıklama|Örnek|
|----|-----------|-------|
|Sabit model|Herhangi bir sayısal, karakter veya dize sabiti, bir numaralandırma sabiti veya tanımlanmış değişmez değer tanımlayıcısı|`1.0`, `"test"`, `30`, `Color.Red`|
|Tanımlayıcı stili|Ayrılmış birleşimin, özel durum etiketinin veya etkin bir model durumunun Case değeri|`Some(x)`<br /><br />`Failure(msg)`|
|Değişken model|*Tanımlayıcısını*|`a`|
|`as` kalıp|*tanımlayıcı* olarak *model*|`(a, b) as tuple1`|
|VEYA desenli|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|VE model|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Dezavantajla|*tanımlayıcı* :: *list-Identifier*|`h :: t`|
|Liste kalıbı|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Dizi düzeni|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Parantez içine alınmış desenler|( *model* )|`( a )`|
|Tanımlama grubu düzeni|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Kayıt stili|{ *Identifier1*  =  *pattern_1*; ... ; *identifier_n*  =  *pattern_n* }|`{ Name = name; }`|
|Joker karakter stili|_|`_`|
|Tür ek açıklaması ile birlikte desenler|*model* : *tür*|`a : int`|
|Test modelini yazın|:? *tür* [as *Identifier* ]|`:? System.DateTime as dt`|
|Null desenli|null|`null`|

## <a name="constant-patterns"></a>Sabit desenler

Sabit desenler sayısal, karakter ve dize değişmez değerleri, numaralandırma sabitleridir (numaralandırma türü adı dahil). `match`Yalnızca sabit desenleri olan bir ifade, diğer dillerdeki Case ifadesiyle karşılaştırılabilir. Giriş değişmez değerle karşılaştırılır ve Değerler eşitse, model eşleşir. Sabit değerin türü, girişin türüyle uyumlu olmalıdır.

Aşağıdaki örnek, değişmez değer desenlerinin kullanımını gösterir ve ayrıca bir değişken deseni ve ya da deseni kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Sabit değer deseninin başka bir örneği, numaralandırma sabitlerine dayanan bir modeldir. Sabit Listesi sabitleri kullandığınızda numaralandırma türü adını belirtmeniz gerekir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Tanımlayıcı desenleri

Desenler, geçerli bir tanımlayıcı oluşturan karakterlerden oluşan bir dizeyse tanımlayıcı formu, düzenin nasıl eşleştirileceği belirler. Tanımlayıcı tek bir karakterden uzunsa ve büyük harfli bir karakterle başlıyorsa, derleyici tanımlayıcı düzeniyle bir eşleşme yapmayı dener. Bu düzenin tanımlayıcısı, değişmez değer özniteliğiyle, ayırt edici birleşim durumuyla, özel durum tanımlayıcısıyla veya etkin bir model durumuyla işaretlenmiş bir değer olabilir. Eşleşen bir tanımlayıcı bulunamazsa, eşleşme başarısız olur ve sonraki model kuralı, değişken deseninin girişi ile karşılaştırılır.

Ayırt edici bileşim desenleri basit adlandırılmış durumlar olabilir veya bir değer ya da birden çok değer içeren bir tanımlama grubu olabilir. Bir değer varsa, değer için bir tanımlayıcı belirtmeniz gerekir. Bir tanımlama grubu söz konusu olduğunda, bir veya daha fazla adlandırılmış UNION alanı için, kayıt düzeninin her öğesi için tanımlayıcı veya bir alan adı olan bir tanımlayıcı içeren bir tanımlama grubu düzeni sağlamanız gerekir. Örnekler için bu bölümdeki kod örneklerine bakın.

`option`Türü, iki durum ve içeren ayrılmış bir birleşimdir `Some` `None` . Bir Case ( `Some` ) bir değere sahiptir, ancak diğeri ( `None` ) yalnızca adlandırılmış bir durumdur. Bu nedenle, `Some` servis talebiyle ilişkili değer için bir değişkene sahip olması gerekir `Some` , ancak `None` kendisi tarafından görünmelidir. Aşağıdaki kodda değişkenine, `var1` servis talebiyle eşleştirerek elde edilen değer verilir `Some` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

Aşağıdaki örnekte, `PersonName` ayırt edici bileşim, olası ad biçimlerini temsil eden dizelerin ve karakterlerin bir karışımını içerir. Ayırt edici birleşimin durumları, ve ' dir `FirstOnly` `LastOnly` `FirstLast` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Adlandırılmış alanları olan ayrılmış birleşimler için, adlandırılmış bir alanın değerini çıkarmak için eşittir işaretini (=) kullanın. Örneğin, aşağıdaki gibi bir bildirime sahip ayrılmış bir birleşim düşünün.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Bir model eşleştirme ifadesinde adlandırılmış alanları aşağıdaki gibi kullanabilirsiniz.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Adlandırılmış alanın kullanımı isteğe bağlıdır, bu nedenle önceki örnekte, her ikisi de `Circle(r)` `Circle(radius = r)` aynı etkiye sahiptir.

Birden çok alan belirttiğinizde, noktalı virgül kullanın (;) ayırıcı olarak.

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Etkin desenler, daha karmaşık özel desen eşleştirmeyi tanımlamanızı sağlar. Etkin desenler hakkında daha fazla bilgi için bkz. [Etkin desenler](active-patterns.md).

Tanımlayıcının özel durum olduğu durum, özel durum işleyicileri bağlamında model eşleştirme içinde kullanılır. Özel durum işlemede model eşleştirme hakkında daha fazla bilgi için bkz. [özel durumlar: `try...with` ifade](./exception-handling/the-try-with-expression.md).

## <a name="variable-patterns"></a>Değişken desenleri

Değişken stili, bir değişken adıyla eşleştirildiği değeri atar ve bu daha sonra simgenin sağ tarafındaki yürütme ifadesinde kullanıma sunulmuştur `->` . Bir değişken deseni her türlü girişle eşleşir, ancak değişken desenleri genellikle diğer desenlerde görünür, bu nedenle, değişkenlere ve dizilere gibi daha karmaşık yapıların bağımsız değişkenlere çıkarılması mümkün olur.

Aşağıdaki örnek, bir demet deseninin içindeki değişken bir düzeni gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>as model

`as`Bu model, kendisine eklenmiş bir yan tümcesine sahip bir modeldir `as` . `as`Yan tümcesi, eşleşen değeri bir ifadenin yürütme ifadesinde kullanılabilecek bir ada bağlar `match` veya bu düzenin bir bağlamada kullanıldığı durumda `let` , ad yerel kapsama bir bağlama olarak eklenir.

Aşağıdaki örnek bir model kullanır `as` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>VEYA desenli

OR deseni, giriş verileri birden çok desenle eşleşiyorsa ve sonuç olarak aynı kodu yürütmek istiyorsanız kullanılır. YA da deseninin her iki tarafının türleri uyumlu olmalıdır.

Aşağıdaki örnek, veya modelini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>VE model

VE deseni, girişin iki desenle eşleşmesini gerektirir. VE deseninin her iki tarafının türleri uyumlu olmalıdır.

Aşağıdaki örnek, `detectZeroTuple` Bu konunun ilerleyen kısımlarında yer aldığı, ancak her ikisi de ve `var1` `var2` düzeni kullanılarak değer olarak elde edilen demet düzeni bölümünde gösteriliyor.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Dezavantajla

Cons stili, bir listeyi ilk öğe, *baş*ve geri kalan öğeleri içeren bir liste, *tail*ve bir liste için bir liste oluşturmak için kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Liste kalıbı

Liste deseninin, listelerin bir dizi öğe halinde çıkarılması sağlanır. Liste deseninin kendisi yalnızca belirli sayıdaki öğelerin listeleriyle eşleşir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Dizi düzeni

Dizi düzeni liste düzenine benzer ve belirli uzunluktaki dizileri ayırmak için kullanılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Parantez içine alınmış desenler

Parantezler, istenen ilişkilendirilebilirliği elde etmek için desenlerin etrafında gruplandırılabilir. Aşağıdaki örnekte, parantez ve bir dezavantajla arasındaki ilişkilendirilebilirlik denetlemek için parantezler kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Tanımlama grubu düzeni

Tanımlama grubu düzeni, kayıt düzeni formundaki giriş ile eşleşir ve kayıt düzeninin her bir konum için model eşleme değişkenlerini kullanarak kendi bileşen öğelerine parçalanmak üzere etkin hale gelir.

Aşağıdaki örnek demet desenini gösterir ve aynı zamanda değişmez desenleri, değişken desenleri ve joker karakter desenini kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Kayıt stili

Kayıt stili, alanların değerlerini ayıklamak için kayıt oluşturmak için kullanılır. Düzenin kaydın tüm alanlarına başvurması gerekmez; Atlanan tüm alanlar yalnızca eşleştirmeye katılmaz ve ayıklanmaz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Joker karakter stili

Joker karakter stili, alt çizgi ( `_` ) karakteriyle temsil edilir ve tıpkı değişken düzeniyle benzer şekilde, girişin bir değişkene atanması yerine atılmasının dışında herhangi bir girişle eşleşir. Joker karakter deseni genellikle diğer desenlerin içinde, simgenin sağındaki ifadede gerekli olmayan değerler için yer tutucu olarak kullanılır `->` . Joker karakter deseni, eşleşmeyen herhangi bir girişi eşleştirmek için bir desen listesinin sonunda da sık kullanılır. Bu konudaki çok sayıda kod örneğinde joker karakter deseninin gösterildiği gösterilmektedir. Bir örnek için yukarıdaki koda bakın.

## <a name="patterns-that-have-type-annotations"></a>Tür ek açıklamalarına sahip desenler

Desenlerin tür ek açıklamaları olabilir. Bunlar diğer tür ek açıklamaları ve diğer tür ek açıklamaları gibi kılavuz çıkarımı gibi davranır. Desenlerdeki tür ek açıklamaları etrafında parantezler gereklidir. Aşağıdaki kod, tür ek açıklamasına sahip bir model gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Test modelini yazın

Tür Test deseninin girişi bir türle eşleştirmek için kullanılır. Giriş türü, düzende belirtilen tür ile bir eşleşmedir (veya türetilmiş bir tür), eşleşme başarılı olur.

Aşağıdaki örnek, tür testi modelini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

Yalnızca bir tanımlayıcının belirli bir türetilmiş türde olup olmadığını denetyorsanız, `as identifier` Aşağıdaki örnekte gösterildiği gibi, düzenin bir bölümüne ihtiyacınız yoktur:

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a>Null desenli

Null değer, null değere izin veren türlerle çalışırken görünebilen null değeriyle eşleşir. .NET Framework kodla birlikte çalışırken genellikle null desenler kullanılır. Örneğin, bir .NET API 'nin dönüş değeri bir ifadenin girdisi olabilir `match` . Program akışını, dönüş değerinin null ve ayrıca döndürülen değerin diğer özelliklerine göre kontrol edebilirsiniz. Null değerlerin programınızın geri kalanına yayılmasını engellemek için null kalıbı kullanabilirsiniz.

Aşağıdaki örnek, null ve değişken düzenlerini kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Eşleşme İfadeleri](match-expressions.md)
- [Etkin Desenler](active-patterns.md)
- [F # dil başvurusu](index.md)
