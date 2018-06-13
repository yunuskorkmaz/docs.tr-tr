---
title: Simge ve İşleç Başvurusu (F#)
description: 'Simgeler ve F # programlama dili kullanılan işleçler hakkında bilgi edinin.'
ms.date: 04/04/2018
ms.openlocfilehash: 79518b990f3a5c794f7658490bdadc2d5b985504
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566710"
---
# <a name="symbol-and-operator-reference"></a>Simge ve İşleç Başvurusu

> [!NOTE]
Bu makalede API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu konu F # dilinde tablosu simgeleri ve kullanılan işleçleri içerir.

## <a name="table-of-symbols-and-operators"></a>Simgeler ve İşleçler Tablosu
Aşağıdaki tabloda F # dilinde kullanılan simgeler açıklar, daha fazla bilgi sağlayan konulara bağlantılar sağlar ve bazı kullandığı simgenin kısa bir açıklamasını sağlar. Simgeler ASCII karakter sıralama kümesini göre sıralanır.

|Simge veya işleci|Bağlantılar|Açıklama|
|------------------|-----|-----------|
|`!`|[Başvuru Hücreleri](../reference-cells.md)<br /><br />[Hesaplama İfadeleri](../computation-expressions.md)|<ul><li>Bir başvuru hücresi dereferences.<br /></li><li>Bir anahtar sözcük sonra bir iş akışı tarafından denetlenen anahtar sözcüğü'nin davranışını değiştirilmiş bir sürümünü gösterir.<br /></li><ul/>|
|`!=`|Yok.|<ul><li>F #'ta kullanılmaz. Kullanım `<>` eşitsizlik işlemleri için.<br /></li><ul/>|
|`"`|[Değişmez Değerler](../literals.md)<br /><br />[Dizeler](../strings.md)|<ul><li>Bir metin dizesi sınırlandırır.<br /></li><ul/>|
|`"""`|[Dizeler](../strings.md)|Harfi harfine metin dizesini sınırlandırır. Farklı `@"..."` içeren bir tırnak işareti karakteri dizede tek tırnak işareti kullanarak belirtebilirsiniz.|
|`#`|[Derleyici Yönergeleri](../compiler-directives.md)<br /><br />[Esnek Türler](../flexible-types.md)|<ul><li>Önişlemci veya derleyici yönergesi gibi önekleri `#light`.<br /></li><li>Bir türü ile kullanıldığında, gösteren bir *esnek türü*, bir tür veya türetilmiş türlerinden birini başvuruyor.<br /></li><ul/>|
|`$`|Daha fazla bilgi yok.|<ul><li>Belirli derleyicinin ürettiği değişken ve işlev adları için dahili olarak kullanılır.<br /></li><ul/>|
|`%`|[Aritmetik İşleçler](arithmetic-operators.md)<br /><br />[Kod Alıntıları](../code-quotations.md)|<ul><li>Tamsayı kalanı hesaplar.<br /></li><li>Yazılan kod tırnak işaretleri boşluklarına ayıran ifadelere için kullanılır.<br /></li><ul/>|
|`%%`|[Kod Alıntıları](../code-quotations.md)|<ul><li>İfadeler türsüz kod tırnak işaretleri içine boşluklarına ayıran için kullanılır.<br /></li><ul/>|
|`%?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda tamsayı kalanı hesaplar.<br /></li><ul/>|
|`&`|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Diğer dilleri ile birlikte çalışırken kullanmak için bir değişken değeri adresini hesaplar.<br /></li><li>VE düzenleri kullanılır.<br /></li><ul/>|
|`&&`|[Boole İşleçleri](boolean-operators.md)|<ul><li>Boolean ve işlem hesaplar.<br /></li><ul/>|
|`&&&`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde AND işlemi hesaplar.<br /></li><ul/>|
|`'`|[Değişmez Değerler](../literals.md)<br /><br />[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Bir tek karakter sabit değeri sınırlandırır.<br /></li><li>Genel tür parametresi gösterir.<br /></li><ul/>|
|<code>&#96;&#96;...&#96;&#96;</code>|Daha fazla bilgi yok.|<ul><li>Dil anahtar sözcüğü gibi yasal bir tanımlayıcı olmayacaktır bir tanımlayıcı sınırlandırır.<br /></li><ul/>|
|`( )`|[Birim Türü](../unit-type.md)|<ul><li>Unit türü tek değerini temsil eder.<br /></li><ul/>|
|`(...)`|[Demetler](../tuples.md)<br /><br />[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>İçinde ifadeleri değerlendirilme sırasını belirtir.<br /></li><li>Bir tanımlama grubu sınırlandırır.<br /></li><li>İşleç tanımları kullanılır.<br /></li><ul/>|
|`(*...*)`||<ul><li>Birden çok satıra yayılmış bir yorum sınırlandırır.<br /></li><ul/>|
|<code>(&#124;...&#124;)</code>|[Etkin Desenler](../active-patterns.md)|<ul><li>Etkin desen sınırlandırır. Olarak da bilinir *Muz klipleri*.<br /></li><ul/>|
|`*`|[Aritmetik İşleçler](arithmetic-operators.md)<br /><br />[Demetler](../tuples.md)<br /><br />[Ölçü Birimleri](../units-of-measure.md)|<ul><li>İkili işleç olarak kullanıldığında, sol ve sağ tarafa çarpar.<br /></li><li>Türlerinde, bir dizi çifti gösterir.<br /></li><li>Ölçü türlerine birimlerinde kullanılır.<br /></li><ul/>|
|`*?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda ve sol tarafında çarpar.<br /></li><ul/>|
|`**`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Üs işlemi hesaplar (`x ** y` anlamına gelir `x` değerini `y`).<br /></li><ul/>|
|`+`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>İkili işleç olarak kullanıldığında, sol ve sağ tarafa ekler.<br /></li><li>Birli işleç olarak kullanıldığında, pozitif bir miktar gösterir. (Resmi olarak, bu değerin değişmeden işaretiyle üretir.)<br /></li><ul/>|
|`+?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda ve sol tarafında ekler.<br /></li><ul/>|
|`,`|[Demetler](../tuples.md)|<ul><li>Bir tanımlama grubu ya da tür parametreleri öğelerini ayırır.<br /></li><ul/>|
|`-`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>İkili işleç olarak kullanıldığında, sol taraftaki sağ tarafında çıkarır.<br /></li><li>Birli işleç olarak kullanıldığında, değilleme işlemi gerçekleştirir.<br /></li><ul/>|
|`-`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda sol tarafındaki sağından çıkarır.<br /></li><ul/>|
|`->`|[İşlevler](../functions/index.md)<br /><br />[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>İşlev türleri, bağımsız değişkenler sınırlandırır ve dönüş değerleri.<br /></li><li>Bir ifadeyi (sıralı ifadeler); verir eşdeğer `yield` anahtar sözcüğü.<br /></li><li>Eşleşme ifadeleri kullanılır<br /></li><ul/>|
|`.`|[Üyeler](../members/index.md)<br /><br />[İlkel Türler](../primitive-types.md)|<ul><li>Üye erişir ve tek tek bir tam ad adlarında ayırır.<br /></li><li>Kayan nokta sayıları ondalık belirtir.<br /></li><ul/>|
|`..`|[Döngüler: `for...in` ifade](../loops-for-in-expression.md)|<ul><li>Bir aralığı belirtir.<br /></li><ul/>|
|`.. ..`|[Döngüler: `for...in` ifade](../loops-for-in-expression.md)|<ul><li>Bir artış birlikte bir aralığı belirtir.<br /></li><ul/>|
|`.[...]`|[Diziler](../arrays.md)|<ul><li>Bir dizi öğesine erişir.<br /></li><ul/>|
|`/`|[Aritmetik İşleçler](arithmetic-operators.md)<br /><br />[Ölçü Birimleri](../units-of-measure.md)|<ul><li>Sol tarafındaki (pay) sağ tarafında (payda) böler.<br /></li><li>Ölçü türlerine birimlerinde kullanılır.<br /></li><ul/>|
|`/?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda sol tarafındaki sağ tarafında tarafından böler.<br /></li><ul/>|
|`//`||<ul><li>Tek satırlı açıklama başlangıcını gösterir.<br /></li><ul/>|
|`///`|[XML Belgeleri](../xml-documentation.md)|<ul><li>Bir XML açıklama gösterir.<br /></li><ul/>|
|`:`|[İşlevler](../functions/index.md)|<ul><li>Bir tür ek açıklamasını kendi türünden bir parametre veya üye adı ayırır.<br /></li><ul/>|
|`::`|[Listeler](../lists.md)<br /><br />[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Bir liste oluşturur. Öğe sol tarafındaki sağ tarafında listesine eklenir.<br /></li><li>Desen eşleştirme listesini bölümlerini ayırmak için kullanılır.<br /></li><ul/>|
|`:=`|[Başvuru Hücreleri](../reference-cells.md)|<ul><li>Bir değer için bir başvuru hücre atar.<br /></li><ul/>|
|`:>`|[Tür Değiştirme ve Dönüştürmeler](../casting-and-conversions.md)|<ul><li>İçin türü hiyerarşide daha yüksek olan dönüştürür.<br /></li><ul/>|
|`:?`|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Döndürür `true` değeri belirtilen türe; eşleşiyorsa, aksi takdirde, döndürür `false` (tür test işleci).<br /></li><ul/>|
|`:?>`|[Tür Değiştirme ve Dönüştürmeler](../casting-and-conversions.md)|<ul><li>Bir tür hiyerarşisinde daha düşük bir türe dönüştürür.<br /></li><ul/>|
|`;`|[Ayrıntılı Söz Dizimi](../verbose-syntax.md)<br /><br />[Listeler](../lists.md)<br /><br />[Kayıtlar](../records.md)|<ul><li>Deyimler (çoğunlukla ayrıntılı sözdiziminde kullanılır) ayırır.<br /></li><li>Liste öğeleri ayırır.<br /></li><li>Kaydının alanlarını ayırır.<br /></li><ul/>|
|`<`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Daha az hesaplar-işlemi daha.<br /></li><ul/>|
|`<?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|Sağ tarafında boş değer atanabilir bir tür olduğunda işlemi,'den az hesaplar.|
|`<<`|[İşlevler](../functions/index.md)|<ul><li>İki işlevleri ters sırada oluşturur; İkincisi yürütülen ilk (geriye dönük birleşim işleci).<br /></li><ul/>|
|`<<<`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>BITS miktar sol tarafta sağ tarafta belirtilen bit sayısı tarafından Sola kaydırır.<br /></li><ul/>|
|`<-`|[Değerler](../values/index.md)|<ul><li>Bir değeri bir değişkene atar.<br /></li><ul/>|
|`<...>`|[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Tür parametreleri sınırlandırır.<br /></li><ul/>|
|`<>`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafındaki sağ tarafı; eşit değilse, aksi takdirde yanlış değerini döndürür.<br /></li><ul/>|
|`<>?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda "eşit değil" işlemi hesaplar.<br /></li><ul/>|
|`<=`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafındaki sağ tarafında; eşit veya daha az ise, aksi takdirde döndürür `false`.<br /></li><ul/>|
|`<=?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda "değerinden küçük veya eşit" işlemi hesaplar.<br /></li><ul/>|
|<code>&lt;&#124;</code>|[İşlevler](../functions/index.md)|<ul><li>İfadenin sonucu sağ tarafta işlevi (geriye dönük kanal işleci) sol tarafındaki geçirir.<br /></li><ul/>|
|<code>&lt;&#124;&#124;</code>|[İşleçler. &#40; &#60; &#124; &#124; &#41; &#60;' T1, 'T2' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>İki bağımsız değişken tuple sağ tarafta sol tarafında işlevi geçirir.<br /></li><ul/>|
|<code>&lt;&#124;&#124;&#124;</code>|[İşleçler. &#40; &#60; &#124; &#124; &#124; &#41; &#60;'T1, 'T2,' T3,' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Üç bağımsız değişken tuple sağ tarafta sol tarafında işlevi geçirir.<br /></li><ul/>|
|`<@...@>`|[Kod Alıntıları](../code-quotations.md)|<ul><li>Yazılan kod tırnak sınırlandırır.<br /></li><ul/>|
|`<@@...@@>`|[Kod Alıntıları](../code-quotations.md)|<ul><li>Türsüz kod tırnak sınırlandırır.<br /></li><ul/>|
|`=`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafındaki sağ tarafı; eşitse, aksi takdirde, döndürür `false`.<br /></li><ul/>|
|`=?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda "eşit" işlemi hesaplar.<br /></li><ul/>|
|`==`|Yok.|<ul><li>F #'ta kullanılmaz. Kullanım `=` eşitlik işlemleri için.<br /></li><ul/>|
|`>`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafındaki sağ tarafında büyük; Aksi takdirde, verir `false`.<br /></li><ul/>|
|`>?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda "ondan" işlemi hesaplar.<br /></li><ul/>|
|`>>`|[İşlevler](../functions/index.md)|<ul><li>İki işlevleri (iletme birleşim işleci) oluşturur.<br /></li><ul/>|
|`>>>`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Miktar sol tarafındaki sayısı kadar sağa kaydırmalar BITS sağ tarafta belirtilen yerleştirir.<br /></li><ul/>|
|`>=`|[Aritmetik İşleçler](arithmetic-operators.md)|<ul><li>Döndürür `true` sol tarafındaki değerinden büyük veya eşit sağ tarafında; Aksi halde, döndürür `false`.<br /></li><ul/>|
|`>=?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ tarafında boş değer atanabilir bir tür olduğunda "büyük veya ona eşit" işlemi hesaplar.<br /></li><ul/>|
|`?`|[Parametreler ve Bağımsız Değişkenler](../parameters-and-arguments.md)|<ul><li>İsteğe bağlı bir bağımsız değişken belirtir.<br /></li><li>Bir operatör olarak dinamik yöntem ve özellik çağrıları için kullanılır. Kendi uygulama sağlaması gerekir.<br /></li><ul/>|
|`? ... <- ...`|Daha fazla bilgi yok.|<ul><li>Bir operatör olarak dinamik özelliklerini ayarlama kullanılır. Kendi uygulama sağlaması gerekir.<br /></li><ul/>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Karşılık gelen işleçleri eşdeğer? Soldaki null atanabilir bir tür olduğu önek.<br /></li><ul/>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Karşılık gelen işleçleri eşdeğer? boş değer atanabilir bir tür sağda olduğu soneki.<br /></li><ul/>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Null Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Her iki tarafında boş değer atanabilir türler nerede çevresindeki soru işaretleri olmadan karşılık gelen işleçleri eşdeğerdir.<br /></li><ul/>|
|`@`|[Listeler](../lists.md)<br /><br />[Dizeler](../strings.md)|<ul><li>Listelerini birleştirir.<br /></li><li>Önce bir dize sabit değeri yerleştirildiğinde, dize kaçış karakterleri hiçbir yorumu aynen, yorumlanacağını olduğunu gösterir.<br /></li><ul/>|
|`[...]`|[Listeler](../lists.md)|<ul><li>Öğeleri listesini sınırlandırır.<br /></li><ul/>|
|<code>[&#124;...&#124;]</code>|[Diziler](../arrays.md)|<ul><li>Dizi öğelerini sınırlandırır.<br /></li><ul/>|
|`[<...>]`|[Öznitelikler](../attributes.md)|<ul><li>Bir öznitelik sınırlandırır.<br /></li><ul/>|
|`\`|[Dizeler](../strings.md)|<ul><li>Sonraki karakter çıkışları; karakter ve dize değişmez değerleri kullanılır.<br /></li><ul/>|
|`^`|[Statik Olarak Çözümlenmiş Tür Parametreleri](../generics/statically-resolved-type-parameters.md)<br /><br />[Dizeler](../strings.md)|<ul><li>Çözümlenmelidir derleme zamanında, çalışma zamanında tür parametreleri belirtir.<br /></li><li>Dizeleri art arda ekler.<br /></li><ul/>|
|`^^^`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde özel OR işlemi hesaplar.<br /></li><ul/>|
|`_`|[Eşleşme İfadeleri](../match-expressions.md)<br /><br />[Genel Türler](../generics/index.md)|<ul><li>Joker karakter deseni gösterir.<br /></li><li>Anonim bir genel parametre belirtir.<br /></li><ul/>|
|<code>&#96;</code>|[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Genel tür parametresi belirtmek için dahili olarak kullanılır.<br /></li><ul/>|
|`{...}`|[Diziler](../sequences.md)<br /><br />[Kayıtlar](../records.md)|<ul><li>Sequence ifadeleri ve hesaplama ifadeleri sınırlandırır.<br /></li><li>Kayıt tanımlarında kullanılır.<br /></li><ul/>|
|<code>&#124;</code>|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Tek tek eşleşme durumlarda, tek tek ayrılmış birleşim durumları ve numaralandırma değerlerinin sınırlandırır.<br /></li><ul/>|
|<code>&#124;&#124;</code>|[Boole İşleçleri](boolean-operators.md)|<ul><li>Boole değeri veya işlemi hesaplar.<br /></li><ul/>|
|<code>&#124;&#124;&#124;</code>|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde OR işlemi hesaplar.<br /></li><ul/>|
|<code>&#124;></code>|[İşlevler](../functions/index.md)|<ul><li>Sol tarafındaki sonucunu işlev için sağ tarafta (iletme kanal işleci) iletir.<br /></li><ul/>|
|<code>&#124;&#124;></code>|[İşleçler. &#40; &#124; &#124; &#62; &#41; &#60;' T1, 'T2' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>İki bağımsız değişken tuple sağ tarafında işlevi sol taraftaki geçirir.<br /></li><ul/>|
|<code>&#124;&#124;&#124;></code>|[İşleçler. &#40; &#124; &#124; &#124; &#62; &#41; &#60;'T1, 'T2,' T3,' U&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Üç bağımsız değişken tuple sağ tarafında işlevi sol taraftaki geçirir.<br /></li><ul/>|
|`~~`|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>Tekli değilleme işleci için bir aşırı bildirmek için kullanılır.<br /></li><ul/>|
|`~~~`|[Bit Düzeyinde İşleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde hesaplar değil işlemi.<br /></li><ul/>|
|`~-`|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>Birli işleç eksi için bir aşırı bildirmek için kullanılır.<br /></li><ul/>|
|`~+`|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|<ul><li>Birli artı işleci için bir aşırı bildirmek için kullanılır.<br /></li><ul/>|

## <a name="operator-precedence"></a>İşleç Önceliği
Aşağıdaki tabloda en düşük önceliğe siparişe en yüksek önceliğe F # dili, işleçler ve diğer deyim anahtar sözcükleri öncelik sırasını gösterir. Ayrıca listelenen birleşim geçerli olur.

|İşleç|İlişkilendirilebilirlik|
|--------|-------------|
|`as`|Sağ|
|`when`|Sağ|
|<code>&#124;</code> (kanal)|Sol|
|`;`|Sağ|
|`let`|Nonassociative|
|`function`, `fun`, `match`, `try`|Nonassociative|
|`if`|Nonassociative|
|`->`|Sağ|
|`:=`|Sağ|
|`,`|Nonassociative|
|`or`, <code>&#124;&#124;</code>|Sol|
|`&`, `&&`|Sol|
|`:>`, `:?>`|Sağ|
|`!=`*OP*, `<` *op*, `>` *op*, `=`, <code>&#124;</code> *op*, `&` *op* , `&`<br /><br />(de dahil olmak üzere `<<<`, `>>>`, <code>&#124;&#124;&#124;</code>, `&&&`)|Sol|
|`^`*OP*<br /><br />(de dahil olmak üzere `^^^`)|Sağ|
|`::`|Sağ|
|`:?`|Değil ilişkilendirilebilir|
|`-`*OP*, `+` *op*|Bu simgeleri kullanımlarını infix uygular|
|`*`*OP*, `/` *op*, `%` *op*|Sol|
|`**`*OP*|Sağ|
|`f x` (işlev uygulaması)|Sol|
|<code>&#124;</code> (Desen eşleştirmesi)|Sağ|
|önek işleçleri (`+`*op*, `-` *op*, `%`, `%%`, `&`, `&&`, `!` *op*, `~` *op*)|Sol|
|`.`|Sol|
|`f(x)`|Sol|
|`f<`*Türler*`>`|Sol|
F # özel İşleç aşırı yüklemesi destekler. Başka bir deyişle, kendi işleçleri tanımlayabilirsiniz. Önceki tabloda *op* tüm geçerli (büyük olasılıkla boş) karakterlerin sırasının yerleşimini işleci, yerleşik veya kullanıcı tanımlı olabilir. Bu nedenle, hangi karakterlerin sırasının yerleşimini öncelik istenen düzeyine ulaşmak için özel bir işleç kullanılacağını belirlemek için bu tabloyu kullanın. Önde gelen `.` karakter derleyici öncelik belirlediğinde yoksayılır.

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](../index.md)

[İşleç Aşırı Yüklemesi](../operator-overloading.md)
