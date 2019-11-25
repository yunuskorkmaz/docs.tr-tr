---
title: Diziler
description: Büyük, sıralı bir F# veri koleksiyonunuz olduğunda ancak tüm öğeleri kullanmak zorunda olmadığınız durumlarda dizileri nasıl kullanacağınızı öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 34e03f1cead0a9f678f637afcb6c8397ef7572bc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971441"
---
# <a name="sequences"></a>Diziler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

*Dizi* , tek bir türdeki öğelerin mantıksal bir dizisidir. Diziler özellikle büyük, sıralı bir veri koleksiyonunuz olduğunda ancak tüm öğeleri kullanmak zorunda olmadığında yararlıdır. Tek tek dizi öğeleri yalnızca gerekli olduğu gibi hesaplanır, bu nedenle bir sıra, tüm öğelerin kullanılmadığı durumlarda bir listeden daha iyi performans sağlayabilir. Diziler, <xref:System.Collections.Generic.IEnumerable%601>için bir diğer ad olan `seq<'T>` türü tarafından temsil edilir. Bu nedenle, <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan tüm .NET türleri bir dizi olarak kullanılabilir. [Seq modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) , diziler içeren düzenlemelere yönelik destek sağlar.

## <a name="sequence-expressions"></a>Dizi Ifadeleri

*Dizi ifadesi* bir diziyi değerlendiren bir ifadedir. Dizi ifadeleri bir dizi form alabilir. En basit form bir aralığı belirtir. Örneğin `seq { 1 .. 5 }`, uç noktalar 1 ve 5 dahil olmak üzere beş öğe içeren bir dizi oluşturur. İki çift nokta arasında bir artış (veya azalış) de belirtebilirsiniz. Örneğin, aşağıdaki kod 10 ' un katları dizisini oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Dizi ifadeleri, sıranın değerlerini üreten F# ifadelerden oluşur. Ayrıca, programlı olarak değerler oluşturabilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Önceki örnek, değeri dizinin bir parçası olacak bir ifade belirtmenize olanak sağlayan `->` işlecini kullanır. `->` yalnızca, izleyen kodun her bölümü bir değer döndürürse kullanabilirsiniz.

Alternatif olarak, aşağıdaki isteğe bağlı bir `yield` `do` anahtar sözcüğünü belirtebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Aşağıdaki kod, Grid 'i temsil eden bir dizi içindeki bir dizinle birlikte koordinat çiftlerinin bir listesini oluşturur. İlk `for` ifadesinin bir `do` belirtilmesini gerektirdiğini unutmayın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Bir dizide kullanılan `if` ifadesi bir filtredir. Örneğin, yalnızca asal sayıların bir dizisini oluşturmak için, `int -> bool`türünde bir işlev `isprime` olduğunu varsayarsak, diziyi aşağıdaki gibi oluşturun.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Daha önce belirtildiği gibi, `if`bir `else` dalı olmadığından, burada `do` gereklidir. `->`kullanmaya çalışırsanız, tüm dallar bir değer döndürmediğinden bir hata alırsınız.

## <a name="the-yield-keyword"></a>`yield!` anahtar sözcüğü

Bazen, bir dizi öğeyi başka bir diziye eklemek isteyebilirsiniz. Bir diziyi başka bir diziye dahil etmek için `yield!` anahtar sözcüğünü kullanmanız gerekir:

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

`yield!` düşünmenin bir diğer yolu da bir iç diziyi düzleştirir ve bunu kapsayan dizide içerir.

Bir ifadede `yield!` kullanıldığında, diğer tüm tek değerler `yield` anahtar sözcüğünü kullanmalıdır:

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

Önceki örnekte yalnızca `x` belirtmek, sıranın hiçbir değer üretmesine neden olur.

## <a name="examples"></a>Örnekler

İlk örnek, bir yineleme, filtre ve dizi oluşturmak için bir yield içeren bir dizi ifadesi kullanır. Bu kod, konsola 1 ile 100 arasında bir dizi asal sayı yazdırır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Aşağıdaki örnek, her biri iki etmenden ve üründen oluşan üç öğe tanımlama bilgisinden oluşan bir çarpma tablosu oluşturur:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Aşağıdaki örnek, tek bir diziyi tek bir son sırada birleştirmek için `yield!` kullanımını gösterir. Bu durumda, bir ikili ağaçtaki her bir alt ağacın sırası, son diziyi oluşturmak için özyinelemeli bir işlevde birleştirilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Dizileri kullanma

Diziler, [listelerle](lists.md)aynı işlevlerin birçoğunu destekler. Diziler, anahtar oluşturma işlevlerini kullanarak gruplandırma ve sayma gibi işlemleri de destekler. Diziler Ayrıca subsequences ayıklamak için daha farklı işlevleri destekler.

Listeler, diziler, kümeler ve haritalar gibi birçok veri türü, sıralanabilir koleksiyonlar olduklarından örtük dizilerdir. Bağımsız değişken olarak bir sıra alan bir işlev, `System.Collections.Generic.IEnumerable<'T>`uygulayan tüm .NET veri türlerine F# ek olarak, ortak veri türleriyle birlikte çalışır. Bu, yalnızca listeler alabilen bir bağımsız değişken olarak liste alan bir işleve kontrast sağlar. `seq<'T>` türü `IEnumerable<'T>`için bir tür kısaltmadır. Bu, ' de F#diziler, listeler, kümeler ve haritalar içeren genel `System.Collections.Generic.IEnumerable<'T>`uygulayan tüm türler ve ayrıca çoğu .net koleksiyon türü, `seq` türüyle uyumludur ve bir sıranın beklendiği her yerde kullanılabilir.

## <a name="module-functions"></a>Modül Işlevleri

[Microsoft. FSharp. Collections ad alanındaki](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) [Seq modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) , dizileriyle çalışma işlevlerini içerir. Bu işlevler listeler, diziler, haritalar ve kümeler ile birlikte çalışarak, bu türlerin hepsi numaralandırılabilir olduğundan ve bu nedenle dizi olarak kabul edilebilir.

## <a name="creating-sequences"></a>Sıralar oluşturma

Dizileri, daha önce açıklandığı gibi veya belirli işlevleri kullanarak sıra ifadeleri kullanarak oluşturabilirsiniz.

[Seq. Empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)kullanarak boş bir sıra oluşturabilir veya [Seq. Singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)kullanarak yalnızca bir belirtilen öğenin dizisini oluşturabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

Sağladığınız bir işlev kullanılarak öğelerin oluşturulduğu bir sıra oluşturmak için [Seq. Init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) ' i kullanabilirsiniz. Ayrıca sıra için bir boyut da sağlarsınız. Bu işlev, dizi boyunca yineleme yapana kadar öğelerin oluşturulmadığından, [List. init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)gibi. Aşağıdaki kod `Seq.init`kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

Çıktı

```console
0 10 20 30 40
```

[Seq. ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) ve [Seq. ofList&#60;&#62; 't işlevini](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)kullanarak diziler ve listelerden sıralar oluşturabilirsiniz. Ancak, bir atama işleci kullanarak dizileri ve listeleri dizilere de dönüştürebilirsiniz. Her iki teknik de aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

[Seq. Cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)kullanarak, `System.Collections`tanımlananlar gibi, Zayıf yazılmış bir koleksiyondan bir dizi oluşturabilirsiniz. Bu tür zayıf türsüz koleksiyonlar öğe türüne sahiptir `System.Object` ve genel olmayan `System.Collections.Generic.IEnumerable&#96;1` türü kullanılarak numaralandırılır. Aşağıdaki kod, bir `System.Collections.ArrayList` bir diziye dönüştürmek için `Seq.cast` kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

[Sıra. initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) işlevini kullanarak sonsuz sıralar tanımlayabilirsiniz. Böyle bir sıra için, öğe dizininden her bir öğeyi oluşturan bir işlev sağlarsınız. Geç değerlendirme nedeniyle sonsuz sıralar mümkündür; öğeler, belirttiğiniz işlevi çağırarak gerektiği şekilde oluşturulur. Aşağıdaki kod örneği, bir kayan noktalı sayı dizisi oluşturur, bu durumda ardışık tamsayıların karelerinin geçişli serisi.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq. unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) , bir durum alan hesaplama işlevinden bir dizi oluşturur ve sıradaki her bir öğeyi oluşturmak için bunu dönüştürür. Durum yalnızca her bir öğeyi hesaplamak için kullanılan bir değerdir ve her öğe hesaplandıktan sonra değiştirilebilir. `Seq.unfold` ikinci bağımsız değişkeni, diziyi başlatmak için kullanılan ilk değerdir. `Seq.unfold`, durum için bir seçenek türü kullanır ve bu, `None` değerini döndürerek diziyi sonlandırabilmenizi sağlar. Aşağıdaki kod, bir `unfold` işlemi tarafından oluşturulan `seq1` ve `fib`dizilerinin iki örneğini gösterir. Birincisi `seq1`, yalnızca 20 ' ye kadar olan sayıları içeren basit bir sıralamadır. İkinci `fib`, Fibonaccı sırasını hesaplamak için `unfold` kullanır. Fibonaccı sırasındaki her öğe önceki iki Fibonaccı numaralarının toplamı olduğundan, durum değeri dizideki önceki iki sayıdan oluşan bir kayıt dizisidir. İlk değer `(1,1)`, dizideki ilk iki sayı.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

Çıktı aşağıdaki gibidir:

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Aşağıdaki kod, sonsuz sıraların değerlerini oluşturmak ve hesaplamak için burada açıklanan dizi modülü işlevlerinin birçoğunu kullanan bir örnektir. Kodun çalışması birkaç dakika sürebilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Öğeleri arama ve bulma

Sıralar desteği işlevleri listelerle kullanılabilir: [Seq. Exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq. exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq. Find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq. FindIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq. Pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq. tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)ve [Seq. tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Diziler için kullanılabilen bu işlevlerin sürümleri, yalnızca aranmakta olan öğeye kadar olan sırayı değerlendirir. Örnekler için bkz. [listeler](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Subsequences edinme

[Seq. Filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) ve [Seq. Choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) , listeler için kullanılabilen işlevlere benzer, ancak sıralama öğeleri değerlendirilene kadar filtreleme ve seçme gerçekleşmeyecektir.

[Seq. Truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) , başka bir dizideki bir sıra oluşturur, ancak diziyi belirtilen sayıda öğe ile sınırlandırır. [Seq. take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) , sıranın başından yalnızca belirtilen sayıda öğeyi içeren yeni bir dizi oluşturur. Dizide, almak için belirtenden daha az öğe varsa, `Seq.take` bir `System.InvalidOperationException`oluşturur. `Seq.take` ve `Seq.truncate` arasındaki fark, öğe sayısı belirttiğiniz sayıdan daha az olursa `Seq.truncate` bir hata üretmez.

Aşağıdaki kod `Seq.truncate` ve `Seq.take`arasındaki davranışı ve farklılıkları gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

Çıkış, hata gerçekleşmeden önce aşağıdaki gibidir.

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

[Seq. takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)kullanarak, bir koşul Işlevi (Boolean işlevi) belirtebilir ve koşulun `true`olduğu orijinal sıranın bu öğelerinden bir sıra oluşturabilirsiniz, ancak için ilk öğeden önce durursunuz. koşulun `false`döndürdüğü değer. [Seq. Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) , başka bir dizinin ilk öğelerinin belirtilen sayısını atlayan ve kalan öğeleri döndüren bir sıra döndürür. [Seq. skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) , koşulun `true`döndürdüğü sürece başka bir dizinin ilk öğelerini atlayan bir dizi döndürür ve sonra koşulun `false`döndürdüğü ilk öğeden başlayarak kalan öğeleri döndürür.

Aşağıdaki kod örneği, `Seq.takeWhile`, `Seq.skip`ve `Seq.skipWhile`arasındaki davranışı ve farklılıkları gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

Çıktı aşağıdaki gibidir:

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Dizileri dönüştürme

[Seq. ikili](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) , giriş dizisinin ardışık öğelerinin diziler halinde gruplandırıldığı yeni bir dizi oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq. pencereli](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) `Seq.pairwise`benzer, ancak bir tanımlama grubu dizisi üretmek yerine, dizideki bitişik öğelerin (bir *pencere*) kopyalarını içeren diziler dizisi oluşturur. Her dizide istediğiniz bitişik öğe sayısını belirtirsiniz.

Aşağıdaki kod örneği `Seq.windowed`kullanımını gösterir. Bu durumda, penceredeki öğelerin sayısı 3 ' dir. Örnek, önceki kod örneğinde tanımlanan `printSeq`kullanır.

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

[Seq. zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) ve [Seq. zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) iki veya üç sıra alır ve bir dizi tanımlama grubu oluşturur. Bu işlevler, [listelerde](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)kullanılabilen ilgili işlevlere benzer. Bir diziyi iki veya daha fazla diziye ayırmak için karşılık gelen bir işlev yoktur. Bu işlevselliğe bir sıra için ihtiyacınız varsa, diziyi bir listeye dönüştürün ve [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)öğesini kullanın.

## <a name="sorting-comparing-and-grouping"></a>Sıralama, karşılaştırma ve gruplama

Listeler için desteklenen sıralama işlevleri de dizileriyle birlikte çalışır. Buna [Seq. Sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) ve [Seq. sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)dahildir. Bu işlevler, tüm sıra boyunca yinelenir.

[Seq. compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) işlevini kullanarak iki diziyi karşılaştırırsınız. İşlev birbirini izleyen öğeleri sırayla karşılaştırır ve ilk eşit olmayan çifle karşılaştığında duraklar. Ek öğeler karşılaştırmaya katkıda bulunamaz.

Aşağıdaki kod `Seq.compareWith`kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

Önceki kodda yalnızca ilk öğe hesaplanır ve incelenir ve sonuç-1 ' dir.

[Seq. countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) her öğe için *anahtar* olarak adlandırılan bir değer üreten bir işlevi alır. Her öğe için bu işlevi çağırarak her öğe için bir anahtar oluşturulur. `Seq.countBy`, anahtar değerlerini içeren bir diziyi ve anahtarın her bir değerini oluşturan öğe sayısı sayısını döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

Çıktı aşağıdaki gibidir:

```console
(1, 34) (2, 33) (0, 33)
```

Önceki çıktı, anahtar 1, 33 anahtar 2 üreten değerleri ve 0 anahtarını üreten 33 değerlerini üreten orijinal sıranın 34 öğe olduğunu gösterir.

[Seq. GroupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)öğesini çağırarak bir sıranın öğelerini gruplandırabilirsiniz. `Seq.groupBy` bir dizi ve bir öğeden anahtar üreten bir işlev alır. İşlev dizideki her öğe üzerinde yürütülür. `Seq.groupBy`, her bir kayıt düzeninin ilk öğesinin anahtar olduğu ve ikincisi bu anahtarı üreten öğelerin bir dizisi olduğu bir dizi tanımlama grubu döndürür.

Aşağıdaki kod örneği, 1 ' den 100 ' e kadar olan sayıların sırasını benzersiz anahtar değerleri 0, 1 ve 2 olan üç gruba bölümlemek için `Seq.groupBy` kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

Çıktı aşağıdaki gibidir:

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

[Seq. Distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)öğesini çağırarak yinelenen öğeleri ortadan kaldıran bir dizi oluşturabilirsiniz. Ya da her öğe üzerinde çağrılacak bir anahtar oluşturma işlevi alan [Seq. dıstınt](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)'i de kullanabilirsiniz. Elde edilen sıra, özgün sıranın benzersiz anahtarlara sahip öğelerini içerir; daha önceki bir öğeye yinelenen bir anahtar üreten daha sonraki öğeler atılır.

Aşağıdaki kod örneği `Seq.distinct`kullanımını gösterir. `Seq.distinct`, ikili sayıları temsil eden diziler oluşturarak ve sonra yalnızca ayrı öğelerin 0 ve 1 olduğunu göstererek gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

Aşağıdaki kod, negatif ve pozitif sayılar içeren bir dizi ile başlayıp anahtar oluşturma işlevi olarak mutlak değer işlevini kullanarak `Seq.distinctBy` gösterir. Negatif sayılar dizide daha önce göründüğünden ve bu nedenle aynı mutlak olan pozitif sayılar yerine seçildiği için ortaya çıkan dizide, dizideki negatif sayılara karşılık gelen tüm pozitif sayıların eksik olması gerekir değer veya anahtar.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Salt okunur ve önbelleğe alınmış sıralar

[Seq. ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) sıranın salt okunur bir kopyasını oluşturur. `Seq.readonly`, dizi gibi bir okuma-yazma koleksiyonunuz olduğunda ve orijinal koleksiyonu değiştirmek istemediğinizde yararlıdır. Bu işlev, veri kapsüllemesini korumak için kullanılabilir. Aşağıdaki kod örneğinde, bir dizi içeren bir tür oluşturulur. Bir özellik diziyi kullanıma sunar, ancak bir diziyi döndürmek yerine, `Seq.readonly`kullanarak diziden oluşturulan bir diziyi döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq. Cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) bir sıranın saklı bir sürümünü oluşturur. Bir dizinin yeniden değerlemeyi önlemek için `Seq.cache` kullanın veya bir sıra kullanan birden fazla iş parçacığına sahip olduğunuzda, ancak her bir öğenin yalnızca bir kez işlem yapabileceği emin olmanız gerekir. Birden çok iş parçacığı tarafından kullanılan bir diziniz varsa, özgün sıranın değerlerini numaralandırır ve hesaplayan bir iş parçacığına sahip olabilirsiniz ve kalan iş parçacıkları önbelleğe alınmış sırayı kullanabilir.

## <a name="performing-computations-on-sequences"></a>Diziler üzerinde hesaplamalar gerçekleştirme

Basit aritmetik işlemler, [Seq. Average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq. Sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq. averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq. sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)vb. gibi listelerden birine benzer.

[Seq. Fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq. küçültme](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)ve [Seq. Scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) , listeler için kullanılabilen ilgili işlevlere benzer. Diziler, bu işlevlerin desteğini listeleyen tam çeşitlerinin bir alt kümesini destekler. Daha fazla bilgi ve örnek için bkz. [listeler](lists.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
