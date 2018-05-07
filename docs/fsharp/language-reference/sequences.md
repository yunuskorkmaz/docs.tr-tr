---
title: Diziler (F#)
description: 'Veri koleksiyonunu sıralı büyük, varsa ancak mutlaka tüm öğeleri kullanılacak beklemeyen F # dizilerini kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: ebebec3a69fd0f4fb8e3ad8d554541fa1cc8945e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="sequences"></a>Diziler

> [!NOTE]
Bu makalede API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

A *dizisi* öğeleri mantıksal bir dizi tümü, bir tür. Veri koleksiyonunu sıralı büyük, varsa ancak mutlaka tüm öğeleri kullanmayı düşünmüyorsanız sıraları özellikle yararlı olur. Tek tek sırası öğeleri yalnızca olarak hesaplanan bir sıralı listesini hangi değil tüm öğeleri kullanılan durumlarda daha iyi performans sağlayabilmesi için gerekli. Sıraları temsil ettiği `seq<'T>` türü olan bir diğer ad için `System.Collections.Generic.IEnumerable`. Bu nedenle, uygulayan bir .NET Framework türü `System.IEnumerable` bir dizi olarak kullanılabilir. [Seq Modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) dizileri içeren işlemeleri için destek sağlar.

## <a name="sequence-expressions"></a>Sequence ifadeleri
A *sıra ifade* dizisi için değerlendirilen ifade. Sequence ifadeleri forms sayısını alabilir. En basit biçimi aralığı belirtir. Örneğin, `seq { 1 .. 5 }` 1 ve 5 uç noktalar dahil olmak üzere beş öğeleri içeren bir sıra oluşturur. Ayrıca bir artış belirtin (veya azaltma) arasında iki çift nokta. Örneğin, aşağıdaki kod 10'ün katları dizisini oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Sequence ifadeleri değerleri dizisi üreten F # ifadelerin yapılır. Kullanabileceklerini `yield` dizisinin bir parçası haline değeri oluşturmak üzere anahtar sözcük.

Aşağıda bir örnek verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Kullanabileceğiniz `->` operatörü yerine `yield`, bu durumda atlayabilirsiniz `do` aşağıdaki örnekte gösterildiği gibi anahtar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Aşağıdaki kod kılavuz temsil eden bir diziye bir dizin birlikte koordinat çiftlerinin listesini oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Bir `if` bir dizisinde kullanılan bir filtre ifadesidir. Örneğin, yalnızca asal sayılar bir işlevi olduğunu varsayarak, bir dizi oluşturmak için `isprime` türü `int -> bool`, dizisi aşağıdaki gibi oluşturun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Kullandığınızda `yield` veya `->` yineleme, tek bir öğe dizisi oluşturmak için her bir yineleme beklenir. Her yineleme öğelerinin bir dizisini oluşturursa kullanmak `yield!`. Bu durumda, her bir yineleme oluşturulan öğelerin son dizisi üretmek için birleşir.

Birden çok ifadelerinde birlikte bir sıra ifadesi birleştirebilirsiniz. Her ifade tarafından üretilen öğelerini birlikte birleşir. Örneğin, bu konunun "Örnek" bölümüne bakın.

## <a name="examples"></a>Örnekler
İlk örnek bir yineleme, bir filtre ve dizi oluşturmak için bir uyarı simgesi içeren bir sıra ifadesi kullanır. Bu kod asal sayılar 1 ve konsola 100 arasında bir dizi yazdırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Aşağıdaki kod `yield` diziler üç öğelerinin her iki faktör ve ürün oluşan oluşan çarpma tablo oluşturmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Aşağıdaki örnek kullanımını gösteren `yield!` tek tek tek bir son sırası dizilere birleştirmek için. Bu durumda, her bir ikili ağacı ağaçtaki sıraları son dizisi üretmek için bir özyinelemeli işlev birleşir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a>Dizileri kullanma
Dizileri çoktan aynı işlevleri destekler [listeler](lists.md). Dizileri gruplandırma ve anahtar üretme işlevlerini kullanarak sayım gibi işlemler de destekler. Dizileri sıraları ayıklanması için daha zengin işlevleri de destekler.

Numaralandırılabilir koleksiyonları olduklarından birçok veri, listeler, dizileri, ayarlar ve haritalar gibi örtük olarak sıraları türleridir. Bağımsız değişken herhangi ortak F # veri türleri, ayrıca uygulayan bir .NET Framework veri türü çalışırken bir dizi isteyen bir işlevi `System.Collections.Generic.IEnumerable<'T>`. Bu, yalnızca listeleri sürebilir bir bağımsız değişken olarak bir listesini isteyen bir işlevi karşılaştırın. Türü `seq<'T>` bir tür kısaltmasıdır `IEnumerable<'T>`. Genel uygulayan herhangi bir türü buna `System.Collections.Generic.IEnumerable<'T>`diziler, listeler, içeren ayarlar ve F # ve ayrıca çoğu .NET Framework koleksiyon türü, maps ile uyumlu `seq` yazın ve bir dizi beklenen her yerde kullanılabilir.


## <a name="module-functions"></a>Modül işlevleri
[Seq Modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) içinde [Microsoft.FSharp.Collections ad alanı](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) sıralarıyla çalışma işlevler içerir. Tüm bu türlerin numaralandırılabilir olduğundan ve bu nedenle sıraları olarak kabul bu işlevler listeleri, dizileri, eşlemeleri ve kümeleri de ile çalışır.


## <a name="creating-sequences"></a>Dizileri oluşturma
Daha önce açıklandığı gibi sıralı ifadeler kullanarak veya belirli işlevleri kullanarak dizileri oluşturabilirsiniz.

Kullanarak boş bir dizi oluşturabilirsiniz [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), veya kullanarak tek bir belirtilen öğe bir dizi oluşturabilirsiniz [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Kullanabileceğiniz [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) öğeleri oluşturulacağı sağladığınız işlevini kullanarak bir sıra oluşturmak için. Sıra için bir boyut de sağlar. Bu işlev tıpkı olduğu [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)dizisi yineleme kadar öğeleri oluşturulmaz, dışında. Aşağıdaki kod kullanımını göstermektedir `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

Çıktı

```
0 10 20 30 40
```

Kullanarak [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) ve [Seq.ofList&#60;'T&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), dizi ve listeleri dizileri oluşturabilirsiniz. Ancak, aynı zamanda dizi ve listeleri sıralarına atama işleci kullanarak dönüştürebilirsiniz. Her iki tekniği aşağıdaki kodda gösterilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

Kullanarak [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), içinde tanımlanan gibi zayıf yazılmış bir koleksiyondan bir dizisi oluşturabilirsiniz `System.Collections`. Zayıf yazılmış böyle koleksiyonları öğe türüne sahip `System.Object` ve genel olmayan kullanarak numaralandırılır `System.Collections.Generic.IEnumerable&#96;1` türü. Aşağıdaki kod kullanımını göstermektedir `Seq.cast` dönüştürmek için bir `System.Collections.ArrayList` bir dizisi içine.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Sonsuz sıraları kullanarak tanımlayabilirsiniz [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) işlevi. Böyle bir sıra için öğe dizinden her öğesi oluşturur işlevi sağlar. Sonsuz sıraları nedeniyle geç değerlendirme mümkündür; öğeleri belirttiğiniz işlevini çağırarak gerektiği şekilde oluşturulur. Aşağıdaki kod örneğinde art arda tamsayıların kareler devrik değişen serisi kayan nokta numarası, bu durumda, sonsuz bir sıra oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) hesaplama işlevden bir duruma alır ve bunu her bir sonraki öğe sırası üretmek için dönüştüren bir sıra oluşturur. Durum her öğe hesaplamak için kullanılan ve her öğenin hesaplanan gibi değiştirebilirsiniz yalnızca bir değerdir. İkinci bağımsız değişkeni `Seq.unfold` sırasını başlatmak için kullanılan ilk değerdir. `Seq.unfold` döndürerek dizisi sonlandırmak sağlar durumu için bir seçenek türü kullanan `None` değeri. Aşağıdaki kod sıralarının, iki örnek gösterir `seq1` ve `fib`, tarafından oluşturulan bir `unfold` işlemi. İlk `seq1`, yalnızca bir basit 100 kadar sayılarla sırasıdır. İkinci `fib`, kullanan `unfold` Fibonacci dizisi hesaplamak için. Fibonacci dizideki her öğe önceki iki Fibonacci sayıların toplamını olduğundan, durum değeri önceki iki sayı dizisinin oluşan bir tanımlama grubu değildir. İlk değer `(1,1)`, sıradaki ilk iki sayı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

Çıktı aşağıdaki gibidir:

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Aşağıdaki kod oluşturma ve sonsuz sıralarının değerleri hesaplamak için burada açıklanan dizisi modülü işlevlerin çoğunu kullanan bir örnektir. Kodu çalıştırmak için birkaç dakika sürebilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a>Arama ve öğeleri bulma
Dizileri destek işlevsellik listeleriyle kullanılabilir: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [ Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), ve [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Sıraları için kullanılabilir olan bu işlevlerin sürümleri için aranacak öğe kadar dizisi değerlendirin. Örnekler için bkz: [listeler](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).


## <a name="obtaining-subsequences"></a>Sıraları alma
[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) ve [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) filtreleme ve seçim oluşmaz dışında sıralı öğeleri değerlendirilir kadar listeler için kullanılabilir olan ilgili işlevleri gibi öğeler.

[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) başka bir dizisinden bir sıra oluşturur, ancak belirtilen sayıda öğeyi dizisine sınırlar. [Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) belirtilen sayıda öğeyi bir dizi başından içeren yeni bir sıra oluşturur. Sıradaki yararlanmak için belirttiğiniz çok daha az öğe varsa `Seq.take` oluşturur bir `System.InvalidOperationException`. Arasındaki farkı `Seq.take` ve `Seq.truncate` olan `Seq.truncate` öğe sayısı az sayısı belirlediğiniz ise hata üretmez.

Aşağıdaki kod davranışını gösterir ve arasındaki farklar `Seq.truncate` ve `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

Hata gerçekleşmeden önce çıktı aşağıdaki gibidir.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

Kullanarak [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), koşul işlevinin (Boolean işlevi) belirtin ve bir dizi koşul olduğu özgün sırasının bu öğeleri oluşan başka bir dizisinden oluşturma `true`, ancak Dur Koşul döndüğü ilk öğe önce `false`. [Seq.Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) başka bir dizinin ilk öğeleri belirtilen sayıda atlar ve kalan öğeleri döndüren bir dizi döndürür. [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) koşulu döndürür sürece, başka bir dizinin ilk öğeleri atlayan bir dizi döndürür `true`ve ardından koşulu döndürür ilköğeilebaşlayankalanöğeleridöndürür`false`.

Aşağıdaki kod örneğinde davranışını gösterir ve arasındaki farklar `Seq.takeWhile`, `Seq.skip`, ve `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

Çıktı aşağıdaki gibidir:

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Dizileri dönüştürme
[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) Giriş dizisinin ardışık öğelere tanımlama grupları gruplandırılır yeni bir sıra oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) benzer `Seq.pairwise`, tanımlama grupları dizisi oluşturan yerine bitişik öğelerinin kopyalarını içeren diziler dizisi üretir dışında (bir *penceresi*) serisinden. Her dizisinde istediğiniz bitişik öğe sayısını belirtin.

Aşağıdaki kod örneğinde kullanımını gösteren `Seq.windowed`. Bu durumda penceresinde öğe sayısı 3'tür. Örnek kullanır `printSeq`, önceki kod örneğinde tanımlanan.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

Çıktı aşağıdaki gibidir:

Başlangıç dizisi:

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Birden çok sıraları işlemleriyle
[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) ve [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) iki veya üç dizilerini alabilir ve diziler dizisi üretir. Bu işlevler için karşılık gelen işlevleri gibidir [listeler](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). İki veya daha fazla sıraları içine bir sıralı ayırmak için karşılık gelen bir işlevi yoktur. Bu işlevsellik bir dizisi için gerekiyorsa, sıralı bir listesine dönüştürmek ve kullanmak [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).


## <a name="sorting-comparing-and-grouping"></a>Sıralama, karşılaştırma ve gruplandırma
Listeler için desteklenen sıralama işlevleri de sıralarıyla çalışır. Bu içerir [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) ve [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Bu işlevlerin tam sırası yineleme.

Kullanarak iki dizileri karşılaştırmak [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) işlevi. İşlev ardışık öğelere sırayla karşılaştırır ve ilk eşit olmayan çifti karşılaştığında durdurur. Ek öğeleri karşılaştırma katkıda bulunmamaktadır.

Aşağıdaki kod kullanımı gösterilmiştir `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

Önceki kod yalnızca ilk öğe hesaplanır ve incelenmesi ve sonucu -1'dir.

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) adlı bir değeri oluşturan bir işlev alır bir *anahtar* her öğe için. Bir anahtarı her öğe üzerinde bu işlevini çağırarak her öğe için oluşturulur. `Seq.countBy` ardından anahtar değerlerinin ve her anahtarın değerini oluşturulan öğelerin sayısını içeren bir dizi döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

Çıktı aşağıdaki gibidir:

```
(1, 34) (2, 33) (0, 33)
```

Önceki çıkış 34 öğeleri anahtar 1, üretilen orijinal dizisi 2 anahtarı üretilen 33 değerler ve 0 anahtarı üretilen 33 değerleri olduğunu gösterir.

Bir dizi öğelerini çağırarak gruplandırabilirsiniz [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy` bir sıra ve bir anahtar öğeden üretir. bir işlev alır. İşlev dizideki her öğe üzerinde yürütülür. `Seq.groupBy` Burada her tanımlama grubu ilk öğesi anahtar ve ikincisi, anahtarı üretmek öğe dizisi başlıkları, bir dizi döndürür.

Aşağıdaki kod örneğinde kullanımı gösterilmiştir `Seq.groupBy` numaraları 1 ile 100 dizisi DISTINCT anahtar değerleri 0, 1 ve 2 olan üç gruba bölümlenir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

Çıktı aşağıdaki gibidir:

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Yinelenen öğeler çağırarak ortadan kaldıran bir dizisi oluşturabilirsiniz [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Veya kullanabilirsiniz [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), her bir öğede çağrılabilir anahtar üretme işlevini alır. Sonuçta elde edilen dizisi özgün dizinin benzersiz anahtarlara sahip öğeleri içerir; önceki bir öğe için yinelenen bir anahtar oluşturmak sonraki öğeleri atılır.

Aşağıdaki kod örneğinde kullanımını göstermektedir `Seq.distinct`. `Seq.distinct` İkili sayılar temsil sıraları oluşturma ve yalnızca farklı öğelere 0 ve 1 olduğunu gösteren gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

Aşağıdaki kodda `Seq.distinctBy` pozitif ve negatif sayıları içeren bir sıra ile başlayan ve mutlak değer işlevi anahtar oluşturma işlevi kullanarak. Sonuçta elde edilen dizisi negatif sayılar dizisinde daha önce görüntülenen ve bu nedenle aynı mutlak sahip pozitif sayılar yerine seçili olduğundan, negatif sayıları dizisinin karşılık gelen tüm pozitif sayılar eksik değer veya anahtar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a>Salt okunur ve önbelleğe alınan dizileri
[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) bir dizi salt okunur bir kopyasını oluşturur. `Seq.readonly` bir dizi gibi bir okuma-yazma koleksiyonuna sahip ve özgün koleksiyonunu değiştirmek istiyor musunuz durumlarda faydalıdır. Bu işlev, veri saklama korumak için kullanılabilir. Aşağıdaki kod örneğinde, bir dizi içeren bir türü oluşturulur. Dizi bir özellik sunar, ancak bir dizi dönerek yerine diziden kullanılarak oluşturulan bir dizi döndürür `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq.Cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) bir dizi depolanan bir sürümünü oluşturur. Kullanmak `Seq.cache` yeniden değerlendirme bir dizi veya bir sırası kullanan birden çok iş parçacığı varsa, ancak her öğeye yalnızca bir kez işlem emin olmanız gerekir önlemek için. Birden çok iş parçacığı tarafından kullanılan bir sıranız varsa, numaralandırır ve özgün sırası değerlerini hesaplar bir iş parçacığı olabilir ve diğer iş parçacıkları önbelleğe alınmış sırası kullanabilirsiniz.


## <a name="performing-computations-on-sequences"></a>Dizileri üzerinde hesaplamalar gerçekleştirme
Basit aritmetik işlemler olduğundan bu listeleri gibi gibi [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)ve benzeri.

[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), ve [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) listeler için kullanılabilir olan ilgili işlevleri gibi öğeler. Dizileri destek listeler bir alt kümesini bu işlevlerin tam çeşitleri destekler. Daha fazla bilgi ve örnekler için bkz: [listeler](lists.md).

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[F# Türleri](fsharp-types.md)
