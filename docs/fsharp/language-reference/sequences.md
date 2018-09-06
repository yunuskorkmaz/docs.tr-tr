---
title: Diziler (F#)
description: 'F # dizileri, veri koleksiyonu sıralı bir büyük, varsa, ancak tüm öğeleri kullanmak mutlaka beklemiyoruz kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: cfe8d1e350a8ac46b7700c12aa84d250f8b35855
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036515"
---
# <a name="sequences"></a>Diziler

> [!NOTE]
Bu makaledeki API başvuru bağlantıları için MSDN sürer.  Docs.microsoft.com API başvuru tamamlanmadı.

A *dizisi* öğeleri mantıksal bir dizisidir tümü tek. Veri koleksiyonu sıralı bir büyük, varsa ancak mutlaka tüm öğeleri kullanmayı düşünmüyorsanız dizileri özellikle yararlı olur. Tek tek dizisi öğeleri yalnızca olarak hesaplanan bir sıralı listesini tüm öğeleri kullanılan olmadığı durumlarda daha iyi performans sağlayabilir gerekli. Dizileri olarak temsil edilir `seq<'T>` bir diğer ad türü için `System.Collections.Generic.IEnumerable`. Bu nedenle, uygulayan bir .NET Framework tür `System.IEnumerable` dizisi olarak kullanılabilir. [Seq Modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) dizileri içeren işlemeleri için destek sağlar.

## <a name="sequence-expressions"></a>Sequence ifadeleri

A *sıra ifade* bir dizisine değerlendiren bir ifade. Sequence ifadeleri, çok sayıda formu alabilir. En basit şekliyle bir aralığını belirtir. Örneğin, `seq { 1 .. 5 }` 1 ve 5 uç noktaları da dahil olmak üzere beş öğe içeren bir dizi oluşturur. Ayrıca bir artımı belirtin (veya azaltma) arasında iki çift nokta. Örneğin, aşağıdaki kod, 10 katları dizisini oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Sequence ifadeleri, değerler dizisi oluşturan F # ifadeleri yapılır. Kullanabilecekleri `yield` dizisinin bir parçası haline değerler üretmek için anahtar sözcüğü.

Aşağıda bir örnek verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Kullanabileceğiniz `->` yerine işleci `yield`, bu durumda atlayabilirsiniz `do` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Aşağıdaki kod, kılavuz temsil eden bir diziye dizin birlikte koordinat çiftlerinin listesini oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Bir `if` sıralı olarak kullanılan bir filtre ifadesidir. Örneğin, yalnızca asal sayıları bir işlevi olduğunu varsayarak, bir dizi oluşturmak için `isprime` türü `int -> bool`, dizisi şu şekilde oluşturun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Kullanırken `yield` veya `->` yinelemeyi, tek bir öğe dizisi oluşturmak için her yinelemede beklenir. Her yinelemenin bir dizi öğe üretir kullanırsanız `yield!`. Bu durumda, her yinelemede oluşturulan öğeleri son dizisini üretmek için bitiştirilir.

Birlikte sırası ifadesindeki birden çok ifadeleri birleştirebilirsiniz. Her bir ifade tarafından oluşturulan öğeleri birleştirilmesinden. Örneğin, bu konunun "Örnekler" bölümüne bakın.

## <a name="examples"></a>Örnekler

İlk örnek, bir yineleme, bir filtre ve bir dizi oluşturmak için bir yield içeren bir sıralama ifadesi kullanır. Bu kod, bir dizi asal sayıları 1 ila 100 konsola yazdırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Aşağıdaki kod `yield` tanımlama üç öğelerin her biri iki faktör ve ürün oluşan oluşan bir çarpan tablosunu oluşturmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Aşağıdaki örnek, kullanımını gösterir `yield!` tek bir son dizi bireysel dizilere birleştirilecek. Bu durumda, sıraları için her bir ikili ağacı ağaçtaki son dizisi oluşturmak için bir özyinelemeli işlev bitiştirilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Dizileri kullanma

Dizileri aynı işlevlerin birçoğunu destekleyen [listeler](lists.md). Dizileri gruplandırma ve anahtar oluşturuluyor işlevlerini kullanarak sayım gibi işlemleri de destekler. Dizileri sıraları ayıklanması için daha çok çeşitli işlevleri de destekler.

Çünkü bunlar numaralandırılabilir koleksiyonları listeler, diziler, ayarlar ve haritalar gibi çok sayıda veri türlerini örtük olarak dizileri:. Bağımsız değişken tüm ortak F # veri türleri, ayrıca uygulayan bir .NET Framework veri türü için çalıştığı bir dizisini alan bir işlev `System.Collections.Generic.IEnumerable<'T>`. Bunu, bu listeleri yalnızca alabilir bağımsız değişken bir liste alan işlevi karşılaştırın. Türü `seq<'T>` bir tür kısaltmasıdır `IEnumerable<'T>`. Genel uygulayan herhangi bir tür buna `System.Collections.Generic.IEnumerable<'T>`içeren diziler, listeler, ayarlar ve F # ve ayrıca çoğu .NET Framework koleksiyon türü, maps ile uyumludur `seq` yazın ve bir dizi beklendiği her yerde kullanılabilir.

## <a name="module-functions"></a>Modül işlevleri

[Seq Modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) içinde [Microsoft.FSharp.Collections ad alanı](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) dizileri ile çalışmak için işlevler içerir. Bu işlevler, tüm bu türlerin numaralandırılabilir olduğundan ve bu nedenle dizileri kabul listeler, diziler, eşlemeler ve kümeleri de ile çalışır.

## <a name="creating-sequences"></a>Dizileri oluşturma

Sequence ifadeleri, daha önce açıklanan şekilde kullanarak veya belirli işlevleri kullanarak dizileri oluşturabilirsiniz.

Boş bir dizi kullanarak oluşturabileceğiniz [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), ya da tek belirtilen öğeyi bir dizi kullanarak oluşturabileceğiniz [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Kullanabileceğiniz [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) kendisi için öğeleri sağlayan bir işlev kullanılarak oluşturulan bir sıra oluşturmak için. Sıra için bir boyutu da sağlar. Bu işlev olduğu gibi [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)dışında öğeleri dizi yineleme kadar oluşturulmaz. Aşağıdaki kod kullanışını `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

Çıktı

```
0 10 20 30 40
```

Kullanarak [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) ve [Seq.ofList&#60;'T&#62; işlevi](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), dizi ve listeleri dizileri oluşturabilirsiniz. Ancak, aynı zamanda dizi ve listeleri dizileri için bir atama işleci kullanarak dönüştürebilirsiniz. Aşağıdaki kodda iki teknik gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

Kullanarak [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), bir dizisi içinde tanımlanan gibi zayıf yazılmış bir koleksiyondan oluşturabileceğiniz `System.Collections`. Zayıf yazılmış böyle koleksiyonları öğe türüne sahip `System.Object` ve genel olmayan kullanarak numaralandırılır `System.Collections.Generic.IEnumerable&#96;1` türü. Aşağıdaki kod kullanışını `Seq.cast` dönüştürmek için bir `System.Collections.ArrayList` dizisini.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Sonsuz sıraları kullanarak tanımlayabilirsiniz [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) işlevi. Böyle bir dizisi için her öğesi, öğenin dizini oluşturan bir işlev sağlar. Sonsuz dizileri nedeniyle geç değerlendirme mümkündür; öğeleri, belirttiğiniz işlevi çağrılarak gerektiğinde oluşturulur. Aşağıdaki kod örneği, art arda gelen tamsayılar kareler devrik değişen serisi kayan nokta numarası, bu durumda, sonsuz bir sıra üretir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) hesaplama işlevden bir duruma alır ve dizideki sonraki her öğe oluşturmak için bunu dönüştüren bir sıra üretir. Durum işlem her öğe için kullanılır ve her öğenin hesaplanan gibi değiştirebilirsiniz yalnızca bir değerdir. İkinci bağımsız değişkeni `Seq.unfold` sırasını başlatmak için kullanılan ilk değerdir. `Seq.unfold` sıra döndürerek sonlandırması sağlar durumu için bir seçenek türü kullanır `None` değeri. Aşağıdaki kod sırası, iki örnek gösterir `seq1` ve `fib`, tarafından oluşturulan bir `unfold` işlemi. Birincisi, `seq1`, yalnızca basit bir sıra numarası 100 adede kadar olan. İkinci `fib`, kullandığı `unfold` Fibonacci sırayı hesaplamak için. Fibonacci dizideki her öğe için önceki iki Fibonacci sayıların toplamı olduğundan, durum değeri önceki iki sayı dizisindeki oluşan bir demet ' dir. İlk değer `(1,1)`, dizideki ilk iki sayı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

Çıktı aşağıdaki gibidir:

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Aşağıdaki kod oluşturma ve sınırsız dizilerinin değeri hesaplamak için burada açıklanan dizisi modülü işlevlerin çoğunu kullanan bir örnektir. Kodu çalıştırmak için birkaç dakika sürebilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Arama ve öğeleri bulma

Dizileri listeleri ile kullanılamayan işlevselliği destekler: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [ Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), ve [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Sıraları için kullanılabilir olan bu işlevlerin sürümleri için Aranmakta olan öğe kadar dizisi değerlendirin. Örnekler için bkz [listeler](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Demetlerin edinme

[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) ve [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) tanımladığınıza göre filtreleme ve seçim oluşmaz dışında sıralı öğeleri değerlendirilir kadar listeleri için kullanılabilir ilgili işlevleri gibi.

[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) başka bir dizisini oluşturur, ancak belirtilen sayıda öğeyi dizisine sınırlar. [Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) yalnızca belirtilen sayıda öğeyi başından itibaren bir dizi içeren yeni bir dizi oluşturur. Dizideki yararlanmak için belirttiğinizden daha az öğe varsa `Seq.take` oluşturur bir `System.InvalidOperationException`. Arasındaki fark `Seq.take` ve `Seq.truncate` olan `Seq.truncate` öğelerin sayısını belirttiğiniz az sayı ise, bir hata üretmez.

Aşağıdaki kod, davranışı gösterir ve arasındaki farklar `Seq.truncate` ve `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

Hata gerçekleşmeden önce çıktısı aşağıdaki gibidir.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

Kullanarak [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), bir koşul işlevi (Boolean işlev) belirtmek ve bu koşul olduğu orijinal sıranın öğelerini oluşan başka bir dizisinden bir sıra oluşturmak `true`, ancak Koşul döndüğü ilk öğeden önce `false`. [Seq.Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) değerinin başka bir dizideki ilk öğe belirtilen sayıda atlar ve kalan öğeleri döndürdüğü bir dizisini döndürür. [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) koşul döndürdüğü sürece, başka bir dizinin ilk öğesini atlayan bir dizisini döndürür `true`ve ardından koşul döndürür ilköğeilebaşlayankalanöğeleridöndürür`false`.

Aşağıdaki kod örneği davranışlarını gösterir ve arasındaki farklar `Seq.takeWhile`, `Seq.skip`, ve `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

Çıktı aşağıdaki gibidir:

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Dizileri dönüştürme

[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) Giriş dizisinin ardışık öğeleri tanımlama grupları gruplandırılır yeni bir dizi oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) benzer `Seq.pairwise`dışında bir dizi diziler oluşturan yerine bitişik öğelerinin kopyalarını içeren bir dizi sırası üretir (bir *penceresi*) serisinden. Her dizide'de istediğiniz bitişik öğelerin sayısını belirtin.

Aşağıdaki kod örneği, kullanımını gösterir `Seq.windowed`. Bu durumda penceresinde öğe sayısı 3'tür. Örnekte `printSeq`, önceki kod örneğinde tanımlanmıştır.

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

## <a name="operations-with-multiple-sequences"></a>Birden çok dizileri ile işlemleri

[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) ve [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) iki veya üç dizilerini alabilir ve tanımlama grubu bir sıra oluşturur. Bu işlevler gibi ilgili işlevler için kullanılabilir olan [listeler](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). İki veya daha fazla dizileri halinde bir dizi ayırmak için karşılık gelen işlevi yoktur. Bu işlev için bir dizisi gerekiyorsa, sıralı bir listeye dönüştürün ve kullanmak [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

## <a name="sorting-comparing-and-grouping"></a>Sıralama, karşılaştırma ve gruplandırma

Desteklenen listeler için sıralama işlevleri dizileri ile de çalışır. Bu içerir [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) ve [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Bu işlevler, tüm sırasıyla gezin.

İki sıranın kullanarak karşılaştırmak [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) işlevi. İşlev ardışık öğeleri sırayla karşılaştırır ve ilk eşit çift karşılaştığında durdurur. Ek öğeler varsa, karşılaştırma katkıda bulunmuyor.

Aşağıdaki kod kullanımını gösterir `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

Önceki kodda, yalnızca ilk öğenin hesaplanan ve incelenir ve sonucu -1'dir.

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) adı verilen bir değer oluşturan bir işlev alır bir *anahtar* her öğe için. Bir anahtarı, her bir öğede bu işlev çağrısı yaparak her öğe için oluşturulur. `Seq.countBy` Daha sonra anahtar değerleri ve oluşturulan her anahtarın değerini öğeleri sayısını içeren bir dizi döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

Çıktı aşağıdaki gibidir:

```
(1, 34) (2, 33) (0, 33)
```

Önceki çıktı 34 öğeleri anahtar 1, üretilen orijinal sıranın 2 anahtarı üretilen 33 değerleri ve 0 anahtarı üretilen 33 değerler olduğunu gösterir.

Çağırarak bir dizinin öğeleri gruplandırabilirsiniz [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy` bir dizi ve bir öğeyi bir anahtar oluşturan bir işlevi alır. İşlevin dizinin her öğesi üzerinde yürütülür. `Seq.groupBy` Diziler, burada her dizi ilk öğesine anahtar, anahtara oluşturan öğeleri dizisi ikinci ise bir dizisini döndürür.

Aşağıdaki kod örneği, kullanımını gösterir `Seq.groupBy` sayı 1 ile 100 dizisini ayrı anahtar değer 0, 1 ve 2 üç gruplar halinde bölümlere ayırmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

Çıktı aşağıdaki gibidir:

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Yinelenen öğeler çağırarak ortadan kaldıran bir dizi oluşturabilirsiniz [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Ya da [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), her bir öğede çağrılabilir anahtar oluşturuluyor bir işlevi alır. Sonuç dizisi özgün dizinin benzersiz anahtarları olan öğeleri içerir. bir önceki öğeye yinelenen bir anahtar oluşturan sonraki öğeleri atılır.

Aşağıdaki kod örneği kullanışını `Seq.distinct`. `Seq.distinct` ikili sayıları temsil dizileri oluşturma ve ardından yalnızca ayrı öğelerinde 0 ve 1 olduğunu gösteren gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

Aşağıdaki kodda `Seq.distinctBy` negatif ve pozitif sayıları içeren bir dizi ile başlayan ve mutlak değer işlevi anahtar oluşturuluyor işlevi kullanarak. Sonuçta elde edilen sırası negatif sayılar sırada görünmesini ve bu nedenle aynı mutlak sahip pozitif sayı yerine seçili olduğundan, sırası negatif sayıları karşılık gelen tüm pozitif sayıları eksik değer veya anahtar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Salt okunur ve önbelleğe alınan dizileri

[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) bir dizi salt okunur bir kopyasını oluşturur. `Seq.readonly` bir dizi gibi bir okuma-yazma koleksiyonu olması ve özgün koleksiyonu değiştirmek istiyor musunuz gerektiğinde yararlı olur. Bu işlev, veri saklama korumak için kullanılabilir. Aşağıdaki kod örneğinde, bir dizi içeren bir tür oluşturulur. Dizinin bir özelliğini gösterir, ancak bir dizi döndürmek yerine, diziden kullanılarak oluşturulan bir dizisini döndürür `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq.Cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) bir dizi depolanmış bir sürümünü oluşturur. Kullanma `Seq.cache` yeniden değerlendirme bir dizi veya birden çok iş parçacığı kullanan bir dizi varsa, ancak her öğe üzerinde yalnızca bir kez etkilediği emin olmanız gerekir önlemek için. Birden çok iş parçacığı tarafından kullanılan bir dizi varsa, bir iş parçacığı numaralandırır ve orijinal sıranın değerlerini hesaplar olabilir ve diğer iş parçacıkları, önbelleğe alınan sırası kullanabilirsiniz.

## <a name="performing-computations-on-sequences"></a>Dizileri üzerinde hesaplamalar gerçekleştirme

Basit aritmetik işlemler aittir listeleri gibi gibi [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)ve benzeri.

[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), ve [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) listeleri için kullanılabilir olan ilgili işlevlerle gibi şunlardır. Destek listeleyen bir kısmı bu işlevlerin tam çeşitlemeleri dizilerini destekler. Daha fazla bilgi ve örnekler için bkz. [listeler](lists.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
