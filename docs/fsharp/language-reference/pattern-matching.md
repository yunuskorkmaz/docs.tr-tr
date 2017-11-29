---
title: "Desen Eşleştirme (F#)"
description: "Desenleri F #'de mantıksal yapıları verilerle karşılaştırmak, veri bağlı parçalarına ya da verilerden bilgi ayıklamak için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5562ee98-e2f1-4dcd-8e2f-16ae27baaade
ms.openlocfilehash: 7c7a3110a8f34c0c96c12d4584010a9ac4b485fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="pattern-matching"></a>Desen Eşleştirme

Desenleri giriş verileri dönüştürme kurallarını alır. F # dili bunlar bir mantıksal yapısını veya yapıları ile karşılaştırmak, veri bağlı parçalarına ya da verileri çeşitli yollarla bilgi ayıklamak için kullanılır.


## <a name="remarks"></a>Açıklamalar
Desenler kullanılan birçok dil yapıları gibi `match` ifade. İşlevlerde bağımsız değişkenleri işlerken kullanıldıkları `let` lambda ifadeleri, bağlamaları ve ilişkili özel durum işleyiciler `try...with` ifade. Daha fazla bilgi için bkz: [eşleşme ifadeleri](match-expressions.md), [let bağlamaları](functions/let-bindings.md), [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md), ve [özel durumlar: `try...with` İfade](exception-handling/the-try-with-expression.md).

Örneğin, `match` ifadesi *düzeni* kanal simgenin aşağıda olduğu.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Her desen girdi şekilde dönüştürme için bir kural olarak görev yapar. İçinde `match` ifadesi, her düzeni incelenir sırayla giriş verilerini deseni ile uyumlu olup olmadığını görmek için. Bir eşleşme bulunamazsa, sonuç ifadesi yürütülür. Bir eşleşme bulunmazsa, sonraki düzeni kural test edilir. İsteğe bağlı olduğunda *koşulu* bölümü içinde açıklanan [eşleşme ifadeleri](match-expressions.md).

Desteklenen desenleri aşağıdaki tabloda gösterilmiştir. Çalışma zamanında giriş her tabloda listelenen sırayla aşağıdaki desenleri karşı test ve kodunuzda ve soldan sağa desenler için her satırda göründükleri gibi desenleri uygulanan yinelemeli olarak ilk son arasındadır.

|Ad|Açıklama|Örnek|
|----|-----------|-------|
|Sabit düzeni|Tüm sayısal, karakter veya dize sabit değeri, bir numaralandırma sabiti veya tanımlı bir değişmez değer tanımlayıcısı|`1.0`, `"test"`, `30`, `Color.Red`|
|Tanımlayıcı deseni|Servis talebi değerini ayrılmış UNION, bir özel durum etiketi veya bir etkin desen örneği|`Some(x)`<br /><br />`Failure(msg)`|
|Değişken deseni|*tanımlayıcı*|`a`|
|`as`düzeni|*Desen* olarak *tanımlayıcısı*|`(a, b) as tuple1`|
|VEYA deseni|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|VE düzeni|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Cons deseni|*tanımlayıcı* :: *liste tanımlayıcısı*|`h :: t`|
|Liste deseni|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Dizi deseni|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Parantez içine alınmış desen|( *düzeni* )|`( a )`|
|Demet deseni|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Kayıt deseni|{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Joker karakter deseni|_|`_`|
|Türü ek açıklama birlikte düzeni|*Desen* : *türü*|`a : int`|
|Tür test deseni|:? *tür* [olarak *tanımlayıcısı* ]|`:? System.DateTime as dt`|
|Null deseni|null|`null`|

## <a name="constant-patterns"></a>Sabit desenleri
Sabit desenleri sayısal karakter ve dize değişmez değerleri, numaralandırma Sabitleri (ile numaralandırma türü adı dahil) alır. A `match` yalnızca sabit deseni yok ifadesi, başka dillerde case deyimi için karşılaştırılabilir. Giriş değişmez değerle karşılaştırılır ve değerleri aynıysa eşleştirir. Sabit değer türü giriş türü ile uyumlu olması gerekir.

Aşağıdaki örnek değişmez değer desenleri kullanımını gösterir ve ayrıca bir değişken deseni ve OR deseni kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Değişmez değer deseni başka bir örneği üzerinde numaralandırması sabitleri dayalı bir desen bulunmaktadır. Numaralandırma sabitleri kullandığınızda numaralandırma türü adı belirtmeniz gerekir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Tanımlayıcı desenleri
Desen geçerli bir tanımlayıcı forms bir karakter dizesi, formun tanımlayıcı deseni nasıl eşleştirildiği belirler. Tanımlayıcı tek bir karakterden uzun ve bir büyük harf karakter ile başlar, derleyici tanımlayıcı deseni bir eşleştirme yapmaya çalışır. Bu desen tanımlayıcısı değişmez değer özniteliği, ayrılmış bir bileşim durumu, bir özel durum tanımlayıcı veya etkin desen servis talebi ile işaretli bir değer olabilir. Eşleşen hiçbir tanımlayıcı bulunursa, eşleşmesi başarısız ve sonraki düzeni kural değişken deseni girdisi karşılaştırılır.

Ayrılmış birleşim desenleri durumlarda adlı basit olabilir veya bir değer veya birden çok değer içeren bir tanımlama grubu sağlayabilirsiniz. Bir değer ise, değer için bir tanımlayıcı belirtmeniz gerekir. Bir tanımlama grubu söz konusu olduğunda kayıt her öğe için bir tanımlayıcı veya bir tanımlayıcı ile bir alan adı için bir tanımlama grubu desenle sağlamanız gerekir veya daha fazla birleşim alanları adlı. Örnekler için bu bölümdeki kod örnekleri bakın.

`option` Türüdür iki durumda sahip ayrılmış bir birleşim `Some` ve `None`. Bir örnek (`Some`) bir değer, ancak diğer sahiptir (`None`) yalnızca bir adlandırılmış bir durumdur. Bu nedenle, `Some` ile ilişkili değer için bir değişken olmalıdır `Some` durumda, ancak `None` tek başına görünmesi gerekir. Aşağıdaki kodda, değişkeni `var1` eşleştirerek elde değeri verildiğinde `Some` durumda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

Aşağıdaki örnekte, `PersonName` ayrılmış birleşim dizelerini ve olası form adlarının temsil karakterleri karışımını içerir. Ayrılmış birleşim örnekleri `FirstOnly`, `LastOnly`, ve `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Alanları adlı ayrılmış birleşimler için adlandırılmış bir alanın değerini ayıklamak için eşittir işareti (=) kullanın. Örneğin, bir bildirimi aşağıdaki gibi ayrılmış bir birleşim göz önünde bulundurun.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Desen eşleştirme ifadesi adlandırılmış alanları gibi kullanabilirsiniz.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Adlandırılmış alan kullanımı isteğe bağlıdır, bu nedenle önceki örnekte, her ikisi de `Circle(r)` ve `Circle(radius = r)` aynı etkiye sahiptir.

Birden çok alan belirttiğinizde, noktalı virgül (;) kullanın ayırıcı olarak.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Etkin desenler daha karmaşık özel desen eşleştirme tanımlamanızı sağlar. Etkin desenler hakkında daha fazla bilgi için bkz: [Etkin desenler](active-patterns.md).

Tanımlayıcı bir özel durum olması durumunda, özel durum işleyicileri bağlamında eşleşen kalıbı kullanılır. Desen eşleştirme, özel durum işleme hakkında daha fazla bilgi için bkz: [özel durumlar: `try...with` ifade](exception-handling/the-try-with-expression.md).


## <a name="variable-patterns"></a>Değişken desenleri
Değişken deseni sağındaki yürütme ifade için kullanılabilir bir değişken adı için eşleşen değeri atar `->` simgesi. Herhangi bir giriş tek başına bir değişken desenle eşleşen ancak değişken desenleri genellikle bu nedenle tanımlama grupları ve değişkenlere ayrılmış dizi gibi daha karmaşık yapıları etkinleştirme diğer desenleri içinde görüntülenir.

Aşağıdaki örnek, bir değişken deseni demet deseni içinde gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>as deseni
`as` Düzeni olan bir desen olan bir `as` eklenmiş yan tümcesi. `as` Yan tümcesi yürütme ifadesinde kullanılabilir bir adla eşleşen değeri bağlar bir `match` ifadesi veya burada bu deseni kullanılıyor durumda bir `let` bağlama, ad yerel kapsam için bir bağlama olarak eklenir.

Aşağıdaki örnek kullanan bir `as` düzeni.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>VEYA deseni
OR deseni giriş verileri birden çok desenleri eşleşebilir ve sonuç olarak aynı kod yürütmek istediğinizde kullanılır. OR deseni her iki tarafının türleri uyumlu olması gerekir.

Aşağıdaki örnek, OR deseni gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>VE düzeni
AND deseni giriş iki desen eşleşmesini gerektirir. Her iki tarafında ve desen türleri uyumlu olmalıdır.

Aşağıdaki örnek benzer `detectZeroTuple` gösterilen [demet deseni](https://msdn.microsoft.com/library/#tuple) bölümünde daha sonra bu konuda, ancak burada hem `var1` ve `var2` değerler ve desen kullanılarak elde edilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Cons deseni
Cons deseni listesini ilk öğesine parçalayın kullanılacak *head*ve kalan öğeleri içeren bir liste *tail*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Liste deseni
Liste deseni öğelerinin bir sayıya ayrılmış listelerin sağlar. Liste deseni yalnızca belirli sayıda öğe listelerini eşleştirebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Dizi deseni
Dizi deseni liste deseni benzer ve belirli bir uzunlukta diziler parçalayın için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Parantez içine alınmış desen
Parantez istenen birleşim elde etmek için desenleri gruplandırılabilir. Aşağıdaki örnekte, parantez birleşim ve düzeni ve dezavantajlarını düzeni arasında denetlemek için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Demet deseni
Demet deseni tanımlama grubu formundaki girişi ile eşleşen ve bağlı elemanlara değişkenleri tanımlama grubundaki her konum için eşleşen kalıbı kullanarak ayrılmış tanımlama grubu sağlar.

Aşağıdaki örnek demet deseni gösterir ve ayrıca değişmez değer desenleri, değişken desenleri ve joker karakter deseni kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Kayıt deseni
Kayıt deseni alanların değerlerini ayıklamak için kayıtları parçalayın için kullanılır. Desen kaydının tüm alanlar başvurusu gerekmez; Atlanan tüm alanlar yalnızca eşleşen içinde yer almayan ve değil ayıklanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Joker karakter deseni
Joker karakter deseni çizgiyle gösterilir (`_`) karakter ve eşleştiğini değişken deseni gibi herhangi bir giriş giriş yerine bir değişkenine atanan atılır dışında. Joker karakter deseni genellikle diğer desenleri içinde yer tutucu olarak sağındaki ifadesinde gerekli olmayan değerleri için kullanılan `->` simgesi. Joker karakter deseni eşleşmeyen herhangi bir giriş eşleşecek şekilde desenlerinin bir listesi sonunda Ayrıca sık kullanılır. Joker karakter deseni birçok kod örnekleri bu konuda gösterilmiştir. Önceki kod bir örnek için bkz.


## <a name="patterns-that-have-type-annotations"></a>Tür ek açıklamaları sahip desenleri
Desenler tür ek açıklamaları olabilir. Bu diğer tür ek açıklamaları gibi davranır ve diğer tür ek açıklamaları gibi çıkarım Kılavuzu. Parantez desenleri türü ek açıklamalar geçici gereklidir. Aşağıdaki kod türü ek açıklama olan bir desen gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Tür Test deseni
Tür test deseni giriş türü karşı eşleştirmek için kullanılır. Giriş türü için bir eşleşme (veya türetilmiş bir tür) ise deseni, eşleşme belirtilen tür başarılı olur.

Aşağıdaki örnek, tür test deseni gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Null deseni
Null deseni bir null değere izin türleri ile çalışırken, görünen null değerle eşleşir. Null desenleri, .NET Framework kod ile birlikte çalışırken sık kullanılır. Örneğin, bir .NET API dönüş değeri girdisi olabilir bir `match` ifade. Program akışı dönüş değeri null olup olmadığını ve aynı zamanda döndürülen değerin diğer özelliklere göre kontrol edebilirsiniz. Null deseni null değerler programınızı geri kalanı için yayılmasını önlemek için kullanabilirsiniz.

Aşağıdaki örnek, null deseni ve değişken deseni kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Ayrıca Bkz.
[Eşleşme ifadeleri](match-expressions.md)

[Etkin desenler](active-patterns.md)

[F # dili başvurusu](index.md)
