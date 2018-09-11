---
title: Desen Eşleştirme (F#)
description: "Desenler F #'de mantıksal yapıları ile verileri karşılaştırmak, verileri bileşenlerine ayırmak veya verilerden bilgi ayıklamak için nasıl kullanılacağını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5ad3d3e1a78246afdfa2948fd0fb84fa04686d30
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269379"
---
# <a name="pattern-matching"></a>Desen Eşleştirme

Desenler, dönüştürme giriş verileri kurallardır. Bunlar, verileri mantıksal bir yapıyla veya yapılarla karşılaştırmak, verileri bileşenlerine ayırmak veya çeşitli şekillerde verilerden bilgi ayıklamak için F # dilinde kullanılır.

## <a name="remarks"></a>Açıklamalar

Desenler kullanılan birçok dil yapılarında gibi `match` ifade. İşlevler için bağımsız değişkenler işlenirken kullanılır `let` bağlarında, lambda ifadeleri ve ilişkili özel durum işleyicileri `try...with` ifade. Daha fazla bilgi için [eşleşme ifadeleri](match-expressions.md), [let bağlamaları](functions/let-bindings.md), [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md), ve [özel durumlar: `try...with` İfade](exception-handling/the-try-with-expression.md).

Örneğin, `match` ifade *deseni* ne kanal simgesini izleyen şeydir.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Her desen bir şekilde girişi dönüştürme için bir kural görür. İçinde `match` ifadesinde her desen incelenene sırayla giriş veri girişinin desen ile uyumlu olup olmadığını görmek için. Bir eşleşme bulunursa sonuç ifade yürütülür. Bir eşleşme bulunmazsa sonraki desen kuralı test edilir. İsteğe bağlı *koşul* bölümü içinde açıklanan [eşleşme ifadeleri](match-expressions.md).

Desteklenen desenler aşağıdaki tabloda gösterilmektedir. Çalışma zamanında giriş her biri aşağıdaki tabloda listelenen sırayla desenleri karşı test edilir ve kodunuzda ve soldan sağa doğru desenleri için her satırında göründükleri gibi desenler yinelemeli olarak uygulandığından, öncelikle son arasındadır.

|Ad|Açıklama|Örnek|
|----|-----------|-------|
|Sabit desen|Herhangi bir sayısal, karakter veya dize sabit değeri, numaralandırma sabiti veya tanımlı bir değişmez değer tanımlayıcısı|`1.0`, `"test"`, `30`, `Color.Red`|
|Tanımlayıcı desen|Büyük/küçük harf değeri ayrılmış bir birleşim, özel durum etiketi veya etkin desen çalışması|`Some(x)`<br /><br />`Failure(msg)`|
|Değişken deseni|*tanımlayıcı*|`a`|
|`as` Düzeni|*Desen* olarak *tanımlayıcısı*|`(a, b) as tuple1`|
|OR deseni|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|VE deseni|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Olumsuz desen|*tanımlayıcı* :: *liste tanımlayıcısı*|`h :: t`|
|Liste deseni|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Dizi deseni|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Parantezlenmiş desen|( *deseni* )|`( a )`|
|Tanımlama grubu düzeni|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Kayıt düzeni|{ *ıdentifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Joker karakter deseni|_|`_`|
|Tür ek açıklaması ile birlikte desenleyin|*Desen* : *türü*|`a : int`|
|Test desenini yazın|:? *tür* [olarak *tanımlayıcı* ]|`:? System.DateTime as dt`|
|Null desen|null|`null`|

## <a name="constant-patterns"></a>Sabit desenler

Sabit desenler sayısal, karakter ve dize değişmez değerleri, numaralandırma sabitidir (numaralandırma türü adı dahil) var. A `match` yalnızca sabit desenlere sahip ifadesi, başka dillerdeki case ifadesinden karşılaştırılabilir. Girdi değişmez değerle karşılaştırılır ve değerleri aynıysa desen eşleşir. Değişmez değerin türü giriş türü ile uyumlu olması gerekir.

Aşağıdaki örnek, değişmez değer desenlerinin kullanımını gösterir ve ayrıca bir değişken desen ve bir veya deseni kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Değişmez değer deseninin başka bir örneği, numaralandırma sabitlerini temel alan bir desendir. Numaralandırma sabitlerini kullandığınızda, numaralandırma türü adı belirtmeniz gerekir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Tanımlayıcı desenler

Desen, geçerli bir tanımlayıcı oluşturan karakter dizesi ise tanımlayıcının biçimi desen eşleştirilmesini belirler. Tanımlayıcı tek bir karakterden daha uzunsa ve büyük harfli bir karakterle başlayan, derleyici tanımlayıcı desen bir eşleştirme yapmaya çalışır. Bu düzen tanımlayıcısı değişmez değer özniteliği, ayrılmış bir birleşim durumu, bir özel durum tanımlayıcısı veya etkin desen çalışması ile işaretlenmiş bir değer olabilir. Eşleşen hiçbir tanımlayıcı bulunmazsa, eşleştirme başarısız olur ve sonraki desen kuralı, değişken desen girdiyle karşılaştırılır.

Adlandırılmış çalışmalar ayrılmış birleşim desenleri basit olabilir veya bir değer ya da birden çok değer içeren bir tanımlama grubu olabilir. Bir değer varsa değer için bir tanımlayıcı belirtmeniz gerekir. Bir demet söz konusu olduğunda bir kayıt düzeni deseni kayıt düzeninin her öğe için bir tanımlayıcı veya bir alan adı olan bir tanımlayıcı sağlamanız gerekir veya birkaç adlandırılmış birlik alanı. Kod örnekleri için bu bölümdeki örneklere bakın.

`option` Türüdür iki duruma sahip ayrılmış bir birleşim `Some` ve `None`. Bir harf (`Some`) bir değer, ancak diğer sahiptir (`None`) sadece adlı bir durumdur. Bu nedenle, `Some` ilişkili değer için bir değişken olmalıdır `Some` büyük/küçük harf, ancak `None` tek başına görünmelidir. Aşağıdaki kodda, değişken `var1` için elde edilen değeri verilir `Some` çalışması.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

Aşağıdaki örnekte, `PersonName` birleşimdir dizeleri ve olası ad formlarını temsil eden karakterler bir karışımını içerir. Ayrılmış birleşimin durumları olan `FirstOnly`, `LastOnly`, ve `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Alanları adlı ayrılmış birleşimler, eşittir işareti (=) adlı bir alanın değerini ayıklamak için kullanın. Örneğin, aşağıdaki gibi bir bildirim ile ayrılmış bir birleşim göz önünde bulundurun.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

İfadeyle eşleşen desendeki adlandırılmış alanları aşağıdaki gibi kullanabilirsiniz.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Adlandırılmış alan kullanımı isteğe bağlıdır, dolayısıyla önceki örnekte, her ikisi de `Circle(r)` ve `Circle(radius = r)` aynı etkiye sahiptir.

Noktalı virgül (;) kullanın, birden çok alan belirtirken, ayırıcı olarak.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Etkin desenler daha karmaşık özel desen eşleştirmeleri tanımlamanıza olanak sağlar. Etkin desenler hakkında daha fazla bilgi için bkz: [Etkin desenler](active-patterns.md).

Tanımlayıcı bir özel durum olduğu durumda, özel durum işleyicilerinin bağlamında eşleşen desende kullanılır. Özel Durum İşlemede desen hakkında daha fazla bilgi için bkz. [özel durumlar: `try...with` ifade](exception-handling/the-try-with-expression.md).

## <a name="variable-patterns"></a>Değişken desenleri

Değişken desen ardından sağındaki yürütme ifadesinde kullanılabilecek bir değişken adı, eşleştirilen değeri atar `->` simgesi. Değişken desen tek başına herhangi bir girdiyle eşleşir ancak değişken desenler genellikle bu nedenle diziler ve değişkenlere ayrıştırılacak diziler gibi daha karmaşık yapıları etkinleştirme, diğer desenlerle görünür.

Aşağıdaki örnek, bir kayıt düzeni desen içinde değişken bir desen gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>Deseni olarak

`as` Desendir sahip bir deseni bir `as` eklenmiş yan tümcesi. `as` Yan tümcesi eşleşen değeri yürütme ifadesinde kullanılabilecek bir ada bağlar bir `match` ifade veya durumda, bu düzen kullanıldığı bir `let` bağlama, ad yerel kapsama bir bağlama olarak eklenir.

Aşağıdaki örnekte bir `as` deseni.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>OR deseni

OR deseni, giriş verilerinin birden çok desen eşleştiğinde ve sonuç olarak aynı kodu yürütmek istediğiniz kullanılır. VEYA deseninin her iki tarafının türleri uyumlu olmalıdır.

Aşağıdaki örnek OR desenini gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>VE deseni

VE deseni girişin iki deseni eşleştirmesini gerektirir. VE deseninin her iki tarafının türleri uyumlu olmalıdır.

Aşağıdaki örnek gibi `detectZeroTuple` gösterilen [kayıt düzeni deseni](https://msdn.microsoft.com/library/#tuple) bölümde daha sonra bu konuda, ancak burada her iki `var1` ve `var2` değerler ve deseni kullanılarak elde edilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Olumsuz desen

Olumsuz desen, bir listeyi ilk öğeye ayırmak için kullanılan *baş*ve kalan öğeleri içeren bir liste *tail*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Liste deseni

Liste deseni listelerin çeşitli öğelere ayrıştırılmasını sağlar. Liste deseninin kendisi yalnızca belirli sayıda öğelerin listesini eşleşebilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Dizi deseni

Dizi deseni liste desenine benzer ve belirli uzunlukta diziler ayırmak için kullanılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Parantezlenmiş desen

Parantez, istenen birleşimi elde etmek için desenler etrafında gruplandırılabilir. Aşağıdaki örnekte, parantezler bir AND deseni ve bir olumsuz desen arasındaki ilişkiyi denetlemek için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Tanımlama grubu düzeni

Kayıt düzeni deseni kayıt düzeni formunda bir girdiyle eşleşir ve kayıt düzenindeki her konum için değişken desen kullanarak bileşen öğelerine ayrılmasına olanak tanır.

Aşağıdaki örnek, kayıt düzeni desenini gösterir ve ayrıca değişmez değer desenleri, değişken desenler ve joker karakter deseni kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Kayıt düzeni

Kayıt düzeni, alanların değerlerini ayıklamak üzere kayıtları ayırmak için kullanılır. Desen, kaydın tüm alanlarını başvurmak yok; Atlanan tüm alanlar yalnızca eşleşen katılmaz ve ayıklanmaz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Joker karakter deseni

Joker karakter deseni alt çizgi ile temsil edilir (`_`) karakteri ve giriş yerine bir değişkene atandığında atılır dışında tıpkı değişken desen gibi herhangi bir girişle eşleşir. Joker karakter deseni genellikle diğer desenler içinde yer tutucu olarak sağındaki ifadede gerekmeyen değerler için kullanılan `->` simgesi. Joker karakter deseni, eşleşmeyen herhangi bir girişi eşleştirmek için Desen listesinin sonunda da sık sık kullanılır. Joker karakter deseni, bu konudaki pek çok kod örneğinde gösterilmiştir. Bir örnek için önceki koda bakın.

## <a name="patterns-that-have-type-annotations"></a>Tür ek açıklamaları olan desenler

Desenler, tür ek açıklamaları olabilir. Bunlar diğer türden ek açıklamalar gibi davranır ve diğer türden ek açıklamalar gibi çıkarım Kılavuzu. Bulunan tür ek açıklamaları etrafına parantez gereklidir. Aşağıdaki kod, bir tür ek açıklamasına sahip bir deseni gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Test desenini yazın

Tür sınama deseni, girişi bir türle eşleştirmek için kullanılır. Giriş türü için bir eşleşme (veya türetilmiş bir tür) ise belirtilen desen, eşleşme başarılı olur.

Aşağıdaki örnek tür testi desenini gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Null desen

Null desen, null değere izin türleriyle çalışırken görünebilen null değer eşleşir. Null desenler, .NET Framework kodu ile birlikte çalışırken sıkça kullanılır. Örneğin, bir .NET API dönüş değerini giriş olabilir bir `match` ifade. Dönüş değerinin null olup olmadığını ve aynı zamanda döndürülen değerin diğer özelliklerini temel alan program akışını denetleyebilirsiniz. Null değerler, programınızın kalanına yayılmasını önlemek için null desenini kullanabilirsiniz.

Aşağıdaki örnek boş desen ve değişken deseni kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Eşleşme İfadeleri](match-expressions.md)
- [Etkin Desenler](active-patterns.md)
- [F# Dili Başvurusu](index.md)
