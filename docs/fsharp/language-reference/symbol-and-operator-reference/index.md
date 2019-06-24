---
title: Simge ve İşleç Başvurusu
description: Simgeler ve kullanılan işleçleri hakkında F# programlama dilidir.
ms.date: 02/11/2019
ms.openlocfilehash: 14ea7a66f7e9a79d24b62a4aa0564eecb891ee1a
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306183"
---
# <a name="symbol-and-operator-reference"></a>Simge ve İşleç Başvurusu

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları için MSDN sürer.  Docs.microsoft.com API başvuru tamamlanmadı.

Bu konu, simgeler ve işleçler kullanılan bir tablo içerir F# dili.

## <a name="table-of-symbols-and-operators"></a>Simgeler ve İşleçler Tablosu

Aşağıdaki tabloda kullanılan simgeler açıklanmaktadır F# dil daha fazla bilgi sağlayan konulara bağlantılar sağlar ve bazı kullandığı simgenin kısa bir açıklamasını sağlar. Semboller ASCII karakter sıralama kümesini göre sıralanır.

|Sembol or işleci|Bağlantılar|Açıklama|
|------------------|-----|-----------|
|`!`|[Başvuru Hücreleri](../reference-cells.md)<br /><br />[Hesaplama İfadeleri](../computation-expressions.md)|<ul><li>Bir başvuru hücresi başvurusunu kaldırır.<br /></li><li>Sonra anahtar sözcüğü, bir iş akışı tarafından denetlenen anahtar sözcüğü'nın davranışı değiştirilmiş bir sürümünü gösterir.<br /></li></ul>|
|`!=`|Geçerli değildir.|<ul><li>İçinde kullanılmadı F#. Kullanım `<>` eşitsizlik işlemleri için.<br /></li></ul>|
|`"`|[Değişmez Değerler](../literals.md)<br /><br />[Dizeler](../strings.md)|<ul><li>Bir metin dizesi sınırlandırır.<br /></li></ul>|
|`"""`|[Dizeler](../strings.md)|Verbatim metin dizesi sınırlandırır. Farklıdır `@"..."` içeren bir tırnak işareti karakteri tek tırnak içinde dize kullanarak belirtebilirsiniz.|
|`#`|[Derleyici Yönergeleri](../compiler-directives.md)<br /><br />[Esnek Türler](../flexible-types.md)|<ul><li>Önişlemci veya derleyici yönergesi gibi ön ekleri `#light`.<br /></li><li>Bir türü ile kullanıldığında, gösterir bir *esnek türü*, bir tür veya türetilmiş türlerini birini gösterir.<br /></li></ul>|
|`$`|Daha fazla bilgi yok.|<ul><li>Belirli derleyici tarafından oluşturulan değişken ve işlev adları için dahili olarak kullanılır.<br /></li></ul>|
|`%`|[Aritmetik İşleçler](arithmetic-operators.md)<br /><br />[Kod Alıntıları](../code-quotations.md)|<ul><li>Tamsayı kalanı hesaplar.<br /></li><li>Yazılan kod tırnak işaretleri içine boşluklarına ayıran ifadeler için kullanılır.<br /></li></ul>|
|`%%`|[Kod Alıntıları](../code-quotations.md)|<ul><li>İfadeler türsüz kod tırnak işaretleri içine boşluklarına ayıran için kullanılır.<br /></li></ul>|
|`%?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda, tamsayı kalanı hesaplar.<br /></li></ul>|
|`&`|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Diğer dillerle birlikte çalışma sırasında kullanımınız değiştirilebilir bir değer adresini hesaplar.<br /></li><li>VE desenler kullanılır.<br /></li></ul>|
|`&&`|[Boole İşleçleri](boolean-operators.md)|<ul><li>Boole türü AND işlemi hesaplar.<br /></li></ul>|
|`&&&`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde AND işlemi hesaplar.<br /></li></ul>|
|`'`|[Değişmez Değerler](../literals.md)<br /><br />[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Bir tek karakterli sabit değer sınırlandırır.<br /></li><li>Genel tür parametresi gösterir.<br /></li></ul>|
|<code>&#96;&#96;...&#96;&#96;</code>|Daha fazla bilgi yok.|<ul><li>Dil anahtar sözcüğü gibi geçerli bir tanımlayıcı olmazdı tanımlayıcı sınırlandırır.<br /></li></ul>|
|`( )`|[Birim Türü](../unit-type.md)|<ul><li>Birim türü tek değerini temsil eder.<br /></li></ul>|
|`(...)`|[Demetler](../tuples.md)<br /><br />[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>İfadelerin değerlendirilme sırasını gösterir.<br /></li><li>Bir demet sınırlandırır.<br /></li><li>İşleç tanımlarında kullanılır.<br /></li></ul>|
|`(*...*)`||<ul><li>Birden fazla satırı kapsayabilir bir yorum sınırlandırır.<br /></li></ul>|
|<code>(&#124;...&#124;)</code>|[Etkin Desenler](../active-patterns.md)|<ul><li>Etkin desen sınırlandırır. Olarak da adlandırılan *Muz klipleri*.<br /></li></ul>|
|`*`|[Aritmetik İşleçler](arithmetic-operators.md)<br /><br />[Demetler](../tuples.md)<br /><br />[Ölçü Birimleri](../units-of-measure.md)|<ul><li>İkili işleç olarak kullanıldığında, sağ ve sol çarpar.<br /></li><li>Bir grup içinde eşleştirme türlerinde gösterir.<br /></li><li>Ölçü türlerine birimlerinde kullanılır.<br /></li></ul>|
|`*?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda ve sol tarafında çarpar.<br /></li></ul>|
|`**`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Üs işlem hesaplar (`x ** y` anlamına gelir `x` sayısının `y`).<br /></li></ul>|
|`+`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>İkili işleç olarak kullanıldığında, sağ ve sol ekler.<br /></li><li>Birli işleç kullanıldığında, pozitif bir miktar gösterir. (Resmi olarak, bu değerin değişmeden işaretiyle üretir.)<br /></li></ul>|
|`+?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda ve sol tarafında ekler.<br /></li></ul>|
|`,`|[Demetler](../tuples.md)|<ul><li>Bir tanımlama grubu ya da tür parametreleri öğelerini ayırır.<br /></li></ul>|
|`-`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>İkili işleç olarak kullanıldığında, sol tarafta sağından çıkarır.<br /></li><li>Birli işleç kullanıldığında, bir değilleme işlemi gerçekleştirir.<br /></li></ul>|
|`-?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda, sol taraftaki sağından çıkarır.<br /></li></ul>|
|`->`|[İşlevler](../functions/index.md)<br /><br />[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>İşlev türleri, bağımsız değişkenleri sınırlandırır ve dönüş değerleri.<br /></li><li>Bir ifade (sequence ifadeleri); verir eşdeğer `yield` anahtar sözcüğü.<br /></li><li>Eşleştirme ifadelerinde kullanılır<br /></li></ul>|
|`.`|[Üyeler](../members/index.md)<br /><br />[İlkel Türler](../primitive-types.md)|<ul><li>Üye erişir ve bir tam ad bireysel adlarını ayırır.<br /></li><li>Bir ondalık kayan nokta numaralarını belirtir.<br /></li></ul>|
|`..`|[Döngüler: `for...in` İfade](../loops-for-in-expression.md)|<ul><li>Bir aralığını belirtir.<br /></li></ul>|
|`.. ..`|[Döngüler: `for...in` İfade](../loops-for-in-expression.md)|<ul><li>Bir artış ile birlikte bir aralığını belirtir.<br /></li></ul>|
|`.[...]`|[Diziler](../arrays.md)|<ul><li>Bir dizi öğesine erişir.<br /></li></ul>|
|`/`|[Aritmetik İşleçler](arithmetic-operators.md)<br /><br />[Ölçü Birimleri](../units-of-measure.md)|<ul><li>Sol tarafındaki (pay) sağ tarafındaki (paydası) böler.<br /></li><li>Ölçü türlerine birimlerinde kullanılır.<br /></li></ul>|
|`/?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda sol tarafındaki sağ tarafını tarafından böler.<br /></li></ul>|
|`//`||<ul><li>Tek satırlı açıklama başlangıcını gösterir.<br /></li></ul>|
|`///`|[XML Belgeleri](../xml-documentation.md)|<ul><li>XML açıklaması gösterir.<br /></li></ul>|
|`:`|[İşlevler](../functions/index.md)|<ul><li>Bir tür ek açıklamasına kendi türünden bir parametre veya üye adı ayırır.<br /></li></ul>|
|`::`|[Listeler](../lists.md)<br /><br />[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Bir liste oluşturur. Öğe sol tarafındaki işlecin sağ tarafındaki listesine eklenir.<br /></li><li>Desen eşleştirme listenin bölümlerini ayırmak için kullanılır.<br /></li></ul>|
|`:=`|[Başvuru Hücreleri](../reference-cells.md)|<ul><li>Bir başvuru hücresine bir değer atar.<br /></li></ul>|
|`:>`|[Tür Değiştirme ve Dönüştürmeler](../casting-and-conversions.md)|<ul><li>İçin türü, hiyerarşinin üst düzeylerindeki dönüştürür.<br /></li></ul>|
|`:?`|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Döndürür `true` değeri belirtilen türe (alt ise dahil); eşleşiyorsa, aksi halde döndürür `false` (tür test işleci).<br /></li></ul>|
|`:?>`|[Tür Değiştirme ve Dönüştürmeler](../casting-and-conversions.md)|<ul><li>Bir tür hiyerarşide daha düşük bir türe dönüştürür.<br /></li></ul>|
|`;`|[Ayrıntılı Söz Dizimi](../verbose-syntax.md)<br /><br />[Listeler](../lists.md)<br /><br />[Kayıtlar](../records.md)|<ul><li>İfadeler (çoğunlukla ayrıntılı sözdiziminde kullanılır) ayırır.<br /></li><li>Bir liste öğelerini ayırır.<br /></li><li>Bir kaydın alanlarını ayırır.<br /></li></ul>|
|`<`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Daha az hesaplar-işlemi daha.<br /></li></ul>|
|`<?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|Sağ tarafında boş değer atanabilir bir tür olduğunda işlemi,'den az hesaplar.|
|`<<`|[İşlevler](../functions/index.md)|<ul><li>İki işlev ters sırada ölçeklemesini; İkincisi yürütülür ilk (geriye dönük birleşim işleci).<br /></li></ul>|
|`<<<`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>BITS miktar sol taraftaki sağ tarafta belirtilen bit sayısına göre Sola kaydırır.<br /></li></ul>|
|`<-`|[Değerler](../values/index.md)|<ul><li>Bir değeri bir değişkene atar.<br /></li></ul>|
|`<...>`|[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Tür parametreleri sınırlandırır.<br /></li></ul>|
|`<>`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafındaki sağ tarafı; eşit değilse, aksi takdirde false döndürür.<br /></li></ul>|
|`<>?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda "eşit değildir" işlemi hesaplar.<br /></li></ul>|
|`<=`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` ; sağ tarafındaki küçüktür veya eşittir sol tarafta ise, aksi halde döndürür `false`.<br /></li></ul>|
|`<=?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>"Az veya buna eşit" işlemi, sağ tarafında boş değer atanabilir bir tür olduğunda hesaplar.<br /></li></ul>|
|<code>&lt;&#124;</code>|[İşlevler](../functions/index.md)|<ul><li>İfadenin sonucu sağ tarafta (geriye dönük yöneltme işleci) sol taraftaki işlevine geçirir.<br /></li></ul>|
|<code>&lt;&#124;&#124;</code>|[İşleçler. &#40; &#60; &#124; &#124; &#41; &#60;' T1, 'T2' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>İki bağımsız değişken tanımlama grubu sağ tarafta sol taraftaki işlevine geçirir.<br /></li></ul>|
|<code>&lt;&#124;&#124;&#124;</code>|[İşleçler. &#40; &#60; &#124; &#124; &#124; &#41; &#60;'T1, 'T2' T3,' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Üç bağımsız değişken kayıt sağ tarafta sol taraftaki işlevine geçirir.<br /></li></ul>|
|`<@...@>`|[Kod Alıntıları](../code-quotations.md)|<ul><li>Yazılan kod tırnak sınırlandırır.<br /></li></ul>|
|`<@@...@@>`|[Kod Alıntıları](../code-quotations.md)|<ul><li>Kod yazılmamış tırnak sınırlandırır.<br /></li></ul>|
|`=`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sağ tarafı; sol tarafındaki eşitse, aksi takdirde döndürür `false`.<br /></li></ul>|
|`=?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>"Equal" işlemi, sağ tarafında boş değer atanabilir bir tür olduğunda hesaplar.<br /></li></ul>|
|`==`|Geçerli değildir.|<ul><li>İçinde kullanılmadı F#. Kullanım `=` eşitlik işlemleri için.<br /></li></ul>|
|`>`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafında, aksi takdirde sağ tarafındaki büyük döndürür `false`.<br /></li></ul>|
|`>?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda, "büyüktür" işlemi hesaplar.<br /></li></ul>|
|`>>`|[İşlevler](../functions/index.md)|<ul><li>İki işlev (İleri birleşim işleci) oluşturur.<br /></li></ul>|
|`>>>`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Kaydırmalar bit sayısı kadar sağa sol tarafındaki miktar sağ tarafta belirtilen yerleştirir.<br /></li></ul>|
|`>=`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafındaki büyük veya eşittir; sağ tarafta ise döndürür, aksi takdirde, `false`.<br /></li></ul>|
|`>=?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda, "büyüktür veya eşittir" işlemi hesaplar.<br /></li></ul>|
|`?`|[Parametreler ve Bağımsız Değişkenler](../parameters-and-arguments.md)|<ul><li>İsteğe bağlı bir bağımsız değişken belirtir.<br /></li><li>Operatör, dinamik yöntem ve özellik çağrıları için kullanılır. Kendi uygulamanız sağlamanız gerekir.<br /></li></ul>|
|`? ... <- ...`|Daha fazla bilgi yok.|<ul><li>Operatör, dinamik özelliklerini ayarlama kullanılır. Kendi uygulamanız sağlamanız gerekir.<br /></li></ul>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Karşılık gelen işleçleri eşdeğer? boş değer atanabilir bir tür soldaki olduğu önek.<br /></li></ul>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Karşılık gelen işleçleri eşdeğer? boş değer atanabilir bir tür sağ tarafta olduğu soneki.<br /></li></ul>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Her iki tarafında boş değer atanabilir türler nerede çevresindeki soru işaretleri olmadan karşılık gelen işleçleri ile eşdeğerdir.<br /></li></ul>|
|`@`|[Listeler](../lists.md)<br /><br />[Dizeler](../strings.md)|<ul><li>İki liste art arda ekler.<br /></li><li>Önce bir dize sabit değeri yerleştirildiğinde, dize aynen, kaçış karakterleri yok yorumu yorumlanacağını olduğunu gösterir.<br /></li></ul>|
|`[...]`|[Listeler](../lists.md)|<ul><li>Öğeleri listesini sınırlandırır.<br /></li></ul>|
|<code>[&#124;...&#124;]</code>|[Diziler](../arrays.md)|<ul><li>Bir dizinin öğeleri sınırlandırır.<br /></li></ul>|
|`[<...>]`|[Öznitelikler](../attributes.md)|<ul><li>Bir öznitelik sınırlandırır.<br /></li></ul>|
|`\`|[Dizeler](../strings.md)|<ul><li>Sonraki karakter çıkışları; ' deki karakter ve dize değişmez değerleri kullanılır.<br /></li></ul>|
|`^`|[Statik Olarak Çözümlenmiş Tür Parametreleri](../generics/statically-resolved-type-parameters.md)<br /><br />[Dizeler](../strings.md)|<ul><li>Çözümlenen gerekir çalışma zamanı değil, derleme zamanında tür parametreleri belirtir.<br /></li><li>Dizeleri birleştirir.<br /></li></ul>|
|`^^^`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde dışlamalı OR işleminde hesaplar.<br /></li></ul>|
|`_`|[Eşleşme İfadeleri](../match-expressions.md)<br /><br />[Genel Türler](../generics/index.md)|<ul><li>Joker karakter deseni gösterir.<br /></li><li>Anonim bir genel parametre belirler.<br /></li></ul>|
|<code>&#96;</code>|[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Genel tür parametresi belirtmek için dahili olarak kullanılır.<br /></li></ul>|
|`{...}`|[Diziler](../sequences.md)<br /><br />[Kayıtlar](../records.md)|<ul><li>Sequence ifadeleri ve hesaplama ifadeleri sınırlandırır.<br /></li><li>Kayıt tanımlarında kullanılır.<br /></li></ul>|
|<code>&#124;</code>|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Bireysel eşleşme örnekleri, tek tek ayrılmış birlik vakaları ve numaralandırma değerlerini sınırlandırır.<br /></li></ul>|
|<code>&#124;&#124;</code>|[Boole İşleçleri](boolean-operators.md)|<ul><li>Boole veya işlem hesaplar.<br /></li></ul>|
|<code>&#124;&#124;&#124;</code>|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde OR işleminde hesaplar.<br /></li></ul>|
|<code>&#124;></code>|[İşlevler](../functions/index.md)|<ul><li>Sol tarafta sonucunu (ileriye doğru kanalı işleci) sağ tarafta işleve geçirir.<br /></li></ul>|
|<code>&#124;&#124;></code>|[İşleçler. &#40; &#124; &#124; &#62; &#41; &#60;' T1, 'T2' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>İki bağımsız değişken tanımlama sol taraftaki işlecin sağ tarafındaki işlevine geçirir.<br /></li></ul>|
|<code>&#124;&#124;&#124;></code>|[İşleçler. &#40; &#124; &#124; &#124; &#62; &#41; &#60;'T1, 'T2' T3,' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Üç bağımsız değişken kayıt sol taraftaki işlecin sağ tarafındaki işlevine geçirir.<br /></li></ul>|
|`~~`|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>Tekli değilleme işleci için bir aşırı bildirmek için kullanılır.<br /></li></ul>|
|`~~~`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde hesaplar işlemi değil.<br /></li></ul>|
|`~-`|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>Aşırı yükleme birli eksi işleci için bildirmek için kullanılır.<br /></li></ul>|
|`~+`|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>Aşırı yükleme birli artı işleci için bildirmek için kullanılır.<br /></li></ul>|

## <a name="operator-precedence"></a>İşleç Önceliği

Aşağıdaki tabloda öncelik işleçleri ve diğer deyim anahtar sözcükleri sırasını gösterir F# en yüksek önceliği en düşük önceliğe kaliteden dili. Ayrıca listelenen birleşim geçerli olur.

|İşleç|İlişkilendirilebilirlik|
|--------|-------------|
|`as`|Sağ|
|`when`|Sağ|
|<code>&#124;</code> (kanal)|Sol|
|`;`|Sağ|
|`let`|Nonassociative|
|`function`, `fun`, `match`, `try`|Nonassociative|
|`if`|Nonassociative|
|`not`|Sağ|
|`->`|Sağ|
|`:=`|Sağ|
|`,`|Nonassociative|
|`or`, <code>&#124;&#124;</code>|Sol|
|`&`, `&&`|Sol|
|`:>`, `:?>`|Sağ|
|`<`*OP*, `>` *op*, `=`, <code>&#124;</code> *op*, `&` *op*, `&`<br /><br />(dahil olmak üzere `<<<`, `>>>`, <code>&#124;&#124;&#124;</code>, `&&&`)|Sol|
|`^`*OP*<br /><br />(dahil olmak üzere `^^^`)|Sağ|
|`::`|Sağ|
|`:?`|İlişkili değil|
|`-`*OP*, `+` *Aç*|Bu simge kullanan infix için geçerlidir|
|`*`*OP*, `/` *op*, `%` *Aç*|Sol|
|`**`*OP*|Sağ|
|`f x` (işlev uygulaması)|Sol|
|<code>&#124;</code> (desen eşleme)|Sağ|
|önek işleçleri (`+`*op*, `-` *op*, `%`, `%%`, `&`, `&&`, `!` *op*, `~` *op*)|Sol|
|`.`|Sol|
|`f(x)`|Sol|
|`f<`*Türleri*`>`|Sol|

F#Özel İşleç aşırı yüklemesi destekler. Başka bir deyişle, kendi işleçleri tanımlayabilirsiniz. Önceki tabloda *op* (büyük olasılıkla boş) geçerli dizi işleci karakter, yerleşik veya kullanıcı tanımlı olabilir. Bu nedenle, hangi istediğiniz öncelik düzeyini elde etmek için özel bir işleç için kullanılacak karakter sırasını belirlemek için bu tabloyu kullanın. Önde gelen `.` derleyici öncelik belirlediğinde karakterler yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](../index.md)
- [İşleç Aşırı Yüklemesi](../operator-overloading.md)
