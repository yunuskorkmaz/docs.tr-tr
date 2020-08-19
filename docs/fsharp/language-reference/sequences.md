---
title: Diziler
description: 'Büyük, sıralı bir veri koleksiyonunuz olduğunda ancak tüm öğeleri kullanmak zorunda olmadığınız durumlarda F # dizilerini nasıl kullanacağınızı öğrenin.'
ms.date: 08/13/2020
ms.openlocfilehash: c84e0aebcc79a595c0ae3b9075648fb629bdd65c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559043"
---
# <a name="sequences"></a>Diziler

*Dizi* , tek bir türdeki öğelerin mantıksal bir dizisidir. Diziler özellikle büyük, sıralı bir veri koleksiyonunuz olduğunda ancak tüm öğeleri kullanmak zorunda olmadığında yararlıdır. Tek tek dizi öğeleri yalnızca gerekli olduğu gibi hesaplanır, bu nedenle bir sıra, tüm öğelerin kullanılmadığı durumlarda bir listeden daha iyi performans sağlayabilir. Diziler, `seq<'T>` için bir diğer ad olan türü tarafından temsil edilir <xref:System.Collections.Generic.IEnumerable%601> . Bu nedenle, arabirimini uygulayan tüm .NET türleri <xref:System.Collections.Generic.IEnumerable%601> bir dizi olarak kullanılabilir. [Seq modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) , diziler içeren düzenlemelere yönelik destek sağlar.

## <a name="sequence-expressions"></a>Dizi Ifadeleri

*Dizi ifadesi* bir diziyi değerlendiren bir ifadedir. Dizi ifadeleri bir dizi form alabilir. En basit form bir aralığı belirtir. Örneğin, `seq { 1 .. 5 }` 1 ve 5 uç noktaları da dahil olmak üzere beş öğe içeren bir dizi oluşturur. İki çift nokta arasında bir artış (veya azalış) de belirtebilirsiniz. Örneğin, aşağıdaki kod 10 ' un katları dizisini oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Dizi ifadeleri, sıranın değerlerini üreten F # ifadelerinden oluşur. Ayrıca, programlı olarak değerler oluşturabilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Önceki örnek `->` işlecini kullanır, bu da değeri dizinin bir parçası olacak bir ifade belirtmenize olanak tanır. Yalnızca `->` kodu izleyen kodun her bölümü bir değer döndürürse kullanabilirsiniz.

Alternatif olarak, `do` aşağıdaki isteğe bağlı olarak anahtar sözcüğünü belirtebilirsiniz `yield` :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Aşağıdaki kod, Grid 'i temsil eden bir dizi içindeki bir dizinle birlikte koordinat çiftlerinin bir listesini oluşturur. İlk `for` ifadenin belirtilmesini gerektirdiğini unutmayın `do` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if`Bir dizide kullanılan bir ifade bir filtredir. Örneğin, yalnızca asal sayıların bir dizisini oluşturmak için, türünde bir işleviniz olduğunu varsayarak `isprime` `int -> bool` diziyi aşağıdaki gibi oluşturun.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Daha önce belirtildiği gibi, `do` `else` ile birlikte gelen bir dal bulunmadığından burada gereklidir `if` . Kullanmayı denerseniz `->` , tüm dallar bir değer döndürmediğinden bir hata alırsınız.

## <a name="the-yield-keyword"></a>`yield!` anahtar sözcüğü

Bazen, bir dizi öğeyi başka bir diziye eklemek isteyebilirsiniz. Başka bir diziye bir sıra eklemek için `yield!` anahtar sözcüğünü kullanmanız gerekir:

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

Farklı bir şekilde düşünmek `yield!` , bir iç diziyi düzleştirir ve bunu kapsayan dizide içerir.

`yield!`Bir ifadede kullanıldığında, diğer tüm tek değerler `yield` anahtar sözcüğünü kullanmalıdır:

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

Önceki örnek, her bir için değerine kadar olan `x` tüm değerlere ek olarak değerini `1` oluşturacaktır `x` `x` .

## <a name="examples"></a>Örnekler

İlk örnek, bir yineleme, filtre ve dizi oluşturmak için bir yield içeren bir dizi ifadesi kullanır. Bu kod, konsola 1 ile 100 arasında bir dizi asal sayı yazdırır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Aşağıdaki örnek, her biri iki etmenden ve üründen oluşan üç öğe tanımlama bilgisinden oluşan bir çarpma tablosu oluşturur:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Aşağıdaki örnek, tek `yield!` bir diziyi tek bir son sırada birleştirmek için öğesinin kullanımını gösterir. Bu durumda, bir ikili ağaçtaki her bir alt ağacın sırası, son diziyi oluşturmak için özyinelemeli bir işlevde birleştirilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Dizileri kullanma

Diziler, [listelerle](lists.md)aynı işlevlerin birçoğunu destekler. Diziler, anahtar oluşturma işlevlerini kullanarak gruplandırma ve sayma gibi işlemleri de destekler. Diziler Ayrıca subsequences ayıklamak için daha farklı işlevleri destekler.

Listeler, diziler, kümeler ve haritalar gibi birçok veri türü, sıralanabilir koleksiyonlar olduklarından örtük dizilerdir. Bağımsız değişken olarak bir sıra alan bir işlev, uygulayan tüm .NET veri türlerine ek olarak ortak F # veri türleriyle çalışır `System.Collections.Generic.IEnumerable<'T>` . Bu, yalnızca listeler alabilen bir bağımsız değişken olarak liste alan bir işleve kontrast sağlar. Türü `seq<'T>` için bir tür kısaltması `IEnumerable<'T>` . Bu, `System.Collections.Generic.IEnumerable<'T>` F # ' de diziler, listeler, kümeler ve haritalar içeren genel ' i uygulayan herhangi bir türün ve ayrıca birçok .net koleksiyon türünün türüyle uyumlu olduğu `seq` ve bir sıranın beklenildiği her yerde kullanılabileceği anlamına gelir.

## <a name="module-functions"></a>Modül Işlevleri

[FSharp. Collections ad alanındaki](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections.html) [Seq modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) , dizileriyle çalışma işlevlerini içerir. Bu işlevler listeler, diziler, haritalar ve kümeler ile birlikte çalışarak, bu türlerin hepsi numaralandırılabilir olduğundan ve bu nedenle dizi olarak kabul edilebilir.

## <a name="creating-sequences"></a>Sıralar oluşturma

Dizileri, daha önce açıklandığı gibi veya belirli işlevleri kullanarak sıra ifadeleri kullanarak oluşturabilirsiniz.

[Seq. Empty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#empty)kullanarak boş bir sıra oluşturabilir veya [Seq. Singleton](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#singleton)kullanarak yalnızca bir belirtilen öğenin dizisini oluşturabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

Sağladığınız bir işlev kullanılarak öğelerin oluşturulduğu bir sıra oluşturmak için [Seq.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#init) kullanabilirsiniz. Ayrıca sıra için bir boyut da sağlarsınız. Bu işlev, dizi boyunca yineleme yapana kadar öğelerin oluşturulmasının dışında [List.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#init)gibi. Aşağıdaki kod öğesinin kullanımını gösterir `Seq.init` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

Çıktı

```console
0 10 20 30 40
```

[Seq. ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofArray) ve [Seq. ofList&#60; 't&#62; işlevini](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofList)kullanarak diziler ve listelerden sıralar oluşturabilirsiniz. Ancak, bir atama işleci kullanarak dizileri ve listeleri dizilere de dönüştürebilirsiniz. Her iki teknik de aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

[Seq. Cast](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cast)kullanarak, içinde tanımlananlar gibi, Zayıf yazılmış bir koleksiyondan bir dizi oluşturabilirsiniz `System.Collections` . Bu tür zayıf türsüz koleksiyonlar öğe türüne sahiptir `System.Object` ve genel olmayan tür kullanılarak numaralandırılır `System.Collections.Generic.IEnumerable&#96;1` . Aşağıdaki kod, `Seq.cast` bir diziye dönüştürmek için kullanımını gösterir `System.Collections.ArrayList` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

Sonsuz dizileri [Seq.iniTinsonlu](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#initInfinite) işlevini kullanarak tanımlayabilirsiniz. Böyle bir sıra için, öğe dizininden her bir öğeyi oluşturan bir işlev sağlarsınız. Geç değerlendirme nedeniyle sonsuz sıralar mümkündür; öğeler, belirttiğiniz işlevi çağırarak gerektiği şekilde oluşturulur. Aşağıdaki kod örneği, bir kayan noktalı sayı dizisi oluşturur, bu durumda ardışık tamsayıların karelerinin geçişli serisi.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq. unfold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#unfold) , bir durum alan hesaplama işlevinden bir dizi oluşturur ve sıradaki her bir öğeyi oluşturmak için bunu dönüştürür. Durum yalnızca her bir öğeyi hesaplamak için kullanılan bir değerdir ve her öğe hesaplandıktan sonra değiştirilebilir. İkinci bağımsız değişkeni, `Seq.unfold` diziyi başlatmak için kullanılan ilk değerdir. `Seq.unfold` , değeri döndürerek diziyi sonlandırabilmenizi sağlayan durum için bir seçenek türü kullanır `None` . Aşağıdaki kod, `seq1` `fib` bir işlem tarafından oluşturulan ve için iki dizi örneği gösterir `unfold` . Birincisi, `seq1` yalnızca 20 ' ye kadar olan sayıları içeren basit bir sıralamadır. İkincisi, `fib` `unfold` Fibonaccı sırasını hesaplamak için kullanır. Fibonaccı sırasındaki her öğe önceki iki Fibonaccı numaralarının toplamı olduğundan, durum değeri dizideki önceki iki sayıdan oluşan bir kayıt dizisidir. İlk değer `(1,1)` , dizideki ilk iki sayı.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Aşağıdaki kod, sonsuz sıraların değerlerini oluşturmak ve hesaplamak için burada açıklanan dizi modülü işlevlerinin birçoğunu kullanan bir örnektir. Kodun çalışması birkaç dakika sürebilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Öğeleri arama ve bulma

Sıralar desteği işlevleri listelerle kullanılabilir: [Seq. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq. exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#find), [Seq. FindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#findIndex), [Seq. Pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pick), [Seq. tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFind)ve [Seq. tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex). Diziler için kullanılabilen bu işlevlerin sürümleri, yalnızca aranmakta olan öğeye kadar olan sırayı değerlendirir. Örnekler için bkz. [listeler](lists.md).

## <a name="obtaining-subsequences"></a>Subsequences edinme

[Seq. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#filter) ve [Seq. Choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#choose) , listeler için kullanılabilen işlevlere benzer, ancak sıralama öğeleri değerlendirilene kadar filtreleme ve seçme gerçekleşmeyecektir.

[Seq. Truncate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#truncate) , başka bir dizideki bir sıra oluşturur, ancak diziyi belirtilen sayıda öğe ile sınırlandırır. [Seq. take](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#take) , sıranın başından yalnızca belirtilen sayıda öğeyi içeren yeni bir dizi oluşturur. Dizide, almak için belirtenden daha az öğe varsa, `Seq.take` bir oluşturur `System.InvalidOperationException` . Ve arasındaki fark `Seq.take` , `Seq.truncate` `Seq.truncate` öğe sayısı belirttiğiniz sayıdan daha az olursa hata oluşturmaz.

Aşağıdaki kod, ve arasındaki farklılıkları gösterir `Seq.truncate` `Seq.take` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

Çıkış, hata gerçekleşmeden önce aşağıdaki gibidir.

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

[Seq. takeWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#takeWhile)kullanarak, bir koşul Işlevi (Boolean işlevi) belirtebilir ve bu öğelerden biri koşulun olduğu `true` , ancak koşulun döndürdüğü ilk öğeden önce durulabileceğiniz bir sıra oluşturabilirsiniz `false` . [Seq. Skip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skip) , başka bir dizinin ilk öğelerinin belirtilen sayısını atlayan ve kalan öğeleri döndüren bir sıra döndürür. [Seq. skipWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skipWhile) , koşulun döndürdüğü sürece başka bir dizinin ilk öğelerini atlayan bir dizi döndürür `true` ve sonra koşulun döndürdüğü ilk öğeden başlayarak kalan öğeleri döndürür `false` .

Aşağıdaki kod örneği, ve arasındaki farklılıkları gösterir `Seq.takeWhile` `Seq.skip` `Seq.skipWhile` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

Çıktı aşağıdaki gibidir:

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Dizileri dönüştürme

[Seq. ikili](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pairwise) , giriş dizisinin ardışık öğelerinin diziler halinde gruplandırıldığı yeni bir dizi oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq. pencereli](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#windowed) gibidir `Seq.pairwise` , ancak bir dizi tanımlama dizisi üretmek yerine, dizideki bitişik öğelerin (bir *pencere*) kopyalarını içeren diziler dizisi oluşturur. Her dizide istediğiniz bitişik öğe sayısını belirtirsiniz.

Aşağıdaki kod örneği öğesinin kullanımını gösterir `Seq.windowed` . Bu durumda, penceredeki öğelerin sayısı 3 ' dir. Örnek `printSeq` , önceki kod örneğinde tanımlanan kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

Çıktı aşağıdaki gibidir:

İlk sıra:

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Birden çok dizileri olan işlemler

[Seq.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip) ve [Seq.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip3) iki veya üç sıra alır ve bir dizi tanımlama grubu oluşturur. Bu işlevler, [listelerde](lists.md)kullanılabilen ilgili işlevlere benzer. Bir diziyi iki veya daha fazla diziye ayırmak için karşılık gelen bir işlev yoktur. Bu işlevselliğe bir sıra için ihtiyacınız varsa, diziyi bir listeye dönüştürün ve [List. unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip)öğesini kullanın.

## <a name="sorting-comparing-and-grouping"></a>Sıralama, karşılaştırma ve gruplama

Listeler için desteklenen sıralama işlevleri de dizileriyle birlikte çalışır. Buna [Seq. Sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sort) ve [Seq. sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sortBy)dahildir. Bu işlevler, tüm sıra boyunca yinelenir.

[Seq. compareWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#compareWith) işlevini kullanarak iki diziyi karşılaştırırsınız. İşlev birbirini izleyen öğeleri sırayla karşılaştırır ve ilk eşit olmayan çifle karşılaştığında duraklar. Ek öğeler karşılaştırmaya katkıda bulunamaz.

Aşağıdaki kod öğesinin kullanımını gösterir `Seq.compareWith` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

Önceki kodda yalnızca ilk öğe hesaplanır ve incelenir ve sonuç-1 ' dir.

[Seq. countBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#countBy) her öğe için *anahtar* olarak adlandırılan bir değer üreten bir işlevi alır. Her öğe için bu işlevi çağırarak her öğe için bir anahtar oluşturulur. `Seq.countBy` sonra anahtar değerlerini içeren bir dizi ve anahtarın her bir değerini oluşturan öğe sayısı sayısını döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

Çıktı aşağıdaki gibidir:

```console
(1, 34) (2, 33) (0, 33)
```

Önceki çıktı, anahtar 1, 33 anahtar 2 üreten değerleri ve 0 anahtarını üreten 33 değerlerini üreten orijinal sıranın 34 öğe olduğunu gösterir.

[Seq. GroupBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#groupBy)öğesini çağırarak bir sıranın öğelerini gruplandırabilirsiniz. `Seq.groupBy` bir dizi ve bir öğeden anahtar üreten bir işlev alır. İşlev dizideki her öğe üzerinde yürütülür. `Seq.groupBy` Her bir kayıt düzeninin ilk öğesi anahtar, ikincisi ise bu anahtarı üreten öğelerin bir dizisi olduğunda, bir dizi tanımlama grubu döndürür.

Aşağıdaki kod örneği, `Seq.groupBy` 1 ile 100 arasındaki sayıların sırasını 0, 1 ve 2 farklı anahtar değerlerine sahip üç gruba bölümlemek için kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

Çıktı aşağıdaki gibidir:

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

[Seq. Distinct](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinct)öğesini çağırarak yinelenen öğeleri ortadan kaldıran bir dizi oluşturabilirsiniz. Ya da her öğe üzerinde çağrılacak bir anahtar oluşturma işlevi alan [Seq. dıstınt](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinctBy)'i de kullanabilirsiniz. Elde edilen sıra, özgün sıranın benzersiz anahtarlara sahip öğelerini içerir; daha önceki bir öğeye yinelenen bir anahtar üreten daha sonraki öğeler atılır.

Aşağıdaki kod örneği öğesinin kullanımını gösterir `Seq.distinct` . `Seq.distinct` ikili sayıları temsil eden diziler oluşturarak ve sonra yalnızca ayrı öğelerin 0 ve 1 olduğunu gösteren sıralar oluşturarak gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

Aşağıdaki kod, `Seq.distinctBy` negatif ve pozitif sayılar içeren bir dizi ile başlayıp anahtar oluşturma işlevi olarak mutlak değer işlevini kullanarak gösterir. Negatif sayılar dizide daha önce göründüğünden ve bu nedenle aynı mutlak değere veya anahtara sahip pozitif sayılar yerine seçildiğinden, sonuçta ortaya çıkan dizide, dizideki negatif sayılara karşılık gelen pozitif sayıların hepsi eksiktir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Salt okunur ve önbelleğe alınmış sıralar

[Seq. ReadOnly](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#readonly) sıranın salt okunur bir kopyasını oluşturur. `Seq.readonly` dizi gibi bir okuma-yazma koleksiyonunuz olduğunda ve özgün koleksiyonu değiştirmek istemediğinizde yararlıdır. Bu işlev, veri kapsüllemesini korumak için kullanılabilir. Aşağıdaki kod örneğinde, bir dizi içeren bir tür oluşturulur. Bir özellik diziyi kullanıma sunar, ancak bir diziyi döndürmek yerine, kullanarak diziden oluşturulan bir diziyi döndürür `Seq.readonly` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq. Cache](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cache) bir sıranın saklı bir sürümünü oluşturur. `Seq.cache`Bir dizinin yeniden değerlendirilmesini önlemek için veya bir sıra kullanan birden çok iş parçacığına sahip olduğunuzda, ancak her bir öğenin yalnızca bir kez işlem yapabileceği halde olduğundan emin olmanız gerekir. Birden çok iş parçacığı tarafından kullanılan bir diziniz varsa, özgün sıranın değerlerini numaralandırır ve hesaplayan bir iş parçacığına sahip olabilirsiniz ve kalan iş parçacıkları önbelleğe alınmış sırayı kullanabilir.

## <a name="performing-computations-on-sequences"></a>Diziler üzerinde hesaplamalar gerçekleştirme

Basit aritmetik işlemler, [Seq. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#average), [Seq. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sum), [Seq. averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#averageBy), [Seq. sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sumBy)vb. gibi listelerden birine benzer.

[Seq. Fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#fold), [Seq. küçültme](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#reduce)ve [Seq. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#scan) , listeler için kullanılabilen ilgili işlevlere benzer. Diziler, bu işlevlerin desteğini listeleyen tam çeşitlerinin bir alt kümesini destekler. Daha fazla bilgi ve örnek için bkz. [listeler](lists.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
