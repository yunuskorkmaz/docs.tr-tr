---
title: Koleksiyon türleri
description: 'F # koleksiyon türleri ve bunların koleksiyon türlerinden nasıl farklı olduğunu öğrenin.'
ms.date: 08/14/2020
ms.openlocfilehash: 0b5be8f656d6728fe382b1944bda0a410a94d226
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720341"
---
# <a name="f-collection-types"></a>F # koleksiyon türleri

Bu konuyu inceleyerek, hangi F # koleksiyon türünün belirli bir ihtiyacı karşılayacak en iyi şekilde olduğunu belirleyebilirsiniz. Bu koleksiyon türleri, .NET 'teki koleksiyon türlerinden farklıdır, örneğin, ad alanındaki gibi, `System.Collections.Generic` F # koleksiyon türleri nesne odaklı bir perspektifin yerine işlevsel programlama perspektifinden tasarlanmalıdır. Daha belirgin olarak, yalnızca dizi koleksiyonunda kesilebilir öğeler vardır. Bu nedenle, bir koleksiyonu değiştirdiğinizde orijinal koleksiyonu değiştirmek yerine değiştirilmiş koleksiyonun bir örneğini oluşturursunuz.

Koleksiyon türleri, nesnelerin depolandığı veri yapısı türüne de göre farklılık gösterir. Karma tablolar, bağlantılı listeler ve diziler gibi veri yapıları farklı performans özelliklerine ve farklı bir kullanılabilir işlemler kümesine sahiptir.

## <a name="table-of-collection-types"></a>Koleksiyon türleri tablosu

Aşağıdaki tabloda, F # koleksiyon türleri gösterilmektedir.

|Tür|Description|İlişkili Bağlantılar|
|----|-----------|-------------|
|[Liste](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharplist-1.html)|Aynı türdeki sıralı, sabit bir öğe dizisi. Bağlantılı liste olarak uygulanır.|[Listeler](lists.md)<br /><br />[Modül Listele](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)|
|[Dizide](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-array-1.html)|Aynı türde olan ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı, kesilebilir bir koleksiyonu.|[Diziler](arrays.md)<br /><br />[Dizi modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)<br /><br />[Array2D modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html)<br /><br />[Array3D modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array3dmodule.html)|
|[sıra](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seq-1.html)|Tek bir türden oluşan mantıksal dizi öğeleri. Diziler özellikle büyük, sıralı bir veri koleksiyonunuz olduğunda ancak tüm öğeleri kullanmak zorunda olmadığınız durumlarda faydalıdır. Tek tek dizi öğeleri yalnızca gerekli olduğu gibi hesaplanır. bu nedenle, tüm öğeler kullanılmazsa bir sıra bir listeden daha iyi çalışabilir. Diziler, `seq<'T>` için bir diğer ad olan türü tarafından temsil edilir `IEnumerable<T>` . Bu nedenle, uygulayan .NET Framework her türlü tür `System.Collections.Generic.IEnumerable<'T>` bir sıra olarak kullanılabilir.|[Diziler](sequences.md)<br /><br />[Seq modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html)|
|[Harita](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharpmap-2.html)|Öğelerin sabit bir sözlüğü. Öğelere anahtar tarafından erişilir.|[Eşleme Modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-mapmodule.html)|
|[Ayarla](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharpset-1.html)|İkili ağaçlara dayalı, karşılaştırma F # yapısal karşılaştırma işlevidir ve bu da anahtar değerlerinde arabirimin uygulamalarını kullanan bir sabit kümesidir `System.IComparable` .|[Modül ayarla](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-setmodule.html)|

### <a name="table-of-functions"></a>İşlev tablosu

Bu bölüm, F # koleksiyon türlerinde kullanılabilir olan işlevleri karşılaştırır. İşlevin hesaplama karmaşıklığı verilir, burada N ilk koleksiyonun boyutudur ve d ise ikinci koleksiyonun boyutudur. Kısa çizgi (-) bu işlevin koleksiyonda kullanılabilir olmadığını gösterir. Diziler geç olarak değerlendirildiğinden, `Seq.distinct` (1) gibi bir işlev hemen döndürdüğünden, ancak numaralandırılmakta olduğu sırada sıranın performansını etkilese de o gibi bir işlev.

|İşlev|Dizi|Liste|Sequence|Harita|Ayarla|Description|
|--------|-----|----|--------|---|---|-----------|
|ýna|O (N)|O (N)|O (N)|-|-|İkinci koleksiyonun öğeleri tarafından izlenen ilk koleksiyonun öğelerini içeren yeni bir koleksiyon döndürür.|
|add|-|-|-|O (günlük (N))|O (günlük (N))|Eklenen öğe ile yeni bir koleksiyon döndürür.|
|ortalama|O (N)|O (N)|O (N)|-|-|Koleksiyondaki öğelerin ortalamasını döndürür.|
|averageBy|O (N)|O (N)|O (N)|-|-|Her bir öğeye uygulanan, belirtilen işlevin sonuçlarının ortalamasını döndürür.|
|blit|O (N)|-|-|-|-|Dizinin bir bölümünü kopyalar.|
|cache|-|-|O (N)|-|-|Bir dizinin öğelerini hesaplar ve depolar.|
|atama|-|-|O (N)|-|-|Öğeleri belirtilen türe dönüştürür.|
|'yu|O (N)|O (N)|O (N)|-|-|`f`Listedeki her öğeye verilen işlevi uygular `x` . İşlevin döndürdüğü her öğe için sonuçları içeren listeyi döndürür `Some(f(x))` .|
|Topla|O (N)|O (N)|O (N)|-|-|Verilen işlevi koleksiyonun her öğesine uygular, tüm sonuçları birleştirir ve Birleşik listeyi döndürür.|
|compareWith|-|-|O (N)|-|-|Verilen karşılaştırma işlevini, öğe by öğesi kullanarak iki diziyi karşılaştırır.|
|concat|O (N)|O (N)|O (N)|-|-|Verilen numaralandırmalar numaralandırmayı tek bir birleştirilmiş sabit listesi olarak birleştirir.|
|contains|-|-|-|-|O (günlük (N))|Küme belirtilen öğeyi içeriyorsa true değerini döndürür.|
|containsKey|-|-|-|O (günlük (N))|-|Bir öğenin bir haritanın etki alanında olup olmadığını test eder.|
|count|-|-|-|-|O (N)|Kümedeki öğelerin sayısını döndürür.|
|countBy|-|-|O (N)|-|-|Bir dizinin her öğesine anahtar oluşturma işlevi uygular ve özgün dizideki benzersiz anahtarlar ve oluşum sayısını veren bir sıra döndürür.|
|kopyalama|O (N)|-|O (N)|-|-|Koleksiyonu kopyalar.|
|oluşturmaya|O (N)|-|-|-|-|Başlangıçta verilen değerin tamamı olan tüm öğelerin bir dizisini oluşturur.|
|ilir|-|-|O (1)|-|-|Bir sıranın verilen gecikmeli belirtiminden oluşturulan bir diziyi döndürür.|
|difference|-|-|-|-|O (M \* günlüğü (N))|İkinci küme, ilk kümeden kaldırılan öğeleri içeren yeni bir küme döndürür.|
|distinct|||O (1)\*|||Girdilerde genel karma ve eşitlik karşılaştırmalarına göre yinelenen giriş içermeyen bir dizi döndürür. Bir öğe dizide birden çok kez oluşursa, sonraki oluşumlar atılır.|
|distinctBy|||O (1)\*|||Verilen anahtar oluşturma işlevinin döndürdüğü anahtarlarda genel karma ve eşitlik karşılaştırmalarına göre yinelenen giriş içermeyen bir dizi döndürür. Bir öğe dizide birden çok kez oluşursa, sonraki oluşumlar atılır.|
|empty|O (1)|O (1)|O (1)|O (1)|O (1)|Boş bir koleksiyon oluşturur.|
|bulunur|O (N)|O (N)|O (N)|O (günlük (N))|O (günlük (N))|Dizideki herhangi bir öğenin verilen koşulu karşılayıp karşılamadığını sınar.|
|exists2|O (dk (N, M))|-|O (dk (N, M))|||Giriş sıralarının karşılık gelen herhangi bir çiftinin verilen koşulu karşılayıp karşılamadığını sınar.|
|fill|O (N)|||||Dizinin öğe aralığını verilen değere ayarlar.|
|filtre|O (N)|O (N)|O (N)|O (N)|O (N)|Yalnızca verilen koşulun döndürdüğü koleksiyonun öğelerini içeren yeni bir koleksiyon döndürür `true` .|
|find|O (N)|O (N)|O (N)|O (günlük (N))|-|Verilen işlevin döndürdüğü ilk öğeyi döndürür `true` . `System.Collections.Generic.KeyNotFoundException`Böyle bir öğe yoksa, döndürür.|
|FindIndex|O (N)|O (N)|O (N)|-|-|Dizideki verilen koşulu karşılayan ilk öğenin dizinini döndürür. Koşulla `System.Collections.Generic.KeyNotFoundException` eşleşen hiçbir öğe yoksa yükseltilir.|
|findKey|-|-|-|O (günlük (N))|-|Koleksiyondaki her eşlemede işlevi değerlendirir ve işlevin döndürdüğü ilk eşlemenin anahtarını döndürür `true` . Böyle bir öğe yoksa, bu işlev yükseltilir `System.Collections.Generic.KeyNotFoundException` .|
|kat|O (N)|O (N)|O (N)|O (N)|O (N)|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Giriş işlevi f ise ve öğeler i0... ' de, bu işlev f 'yi hesaplar (... (f s i0)...) 'ndaki.|
|fold2|O (N)|O (N)|-|-|-|İki koleksiyonun karşılık gelen öğelerine bir işlev uygular ve hesaplama aracılığıyla bir Biriktiricinin bağımsız değişkenini akıtma. Koleksiyonlar aynı boyutlarda olmalıdır. Giriş işlevi f ise ve öğeler i0... ve Içinde j0... jN, bu işlev f 'yi hesaplar (... (f s i0 j0)...) jN.|
|foldBack|O (N)|O (N)|-|O (N)|O (N)|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Giriş işlevi f ise ve öğeler i0... Içinde, bu işlev f i0 (...) hesaplar. (s 'de f)).|
|foldBack2|O (N)|O (N)|-|-|-|İki koleksiyonun karşılık gelen öğelerine bir işlev uygular ve hesaplama aracılığıyla bir Biriktiricinin bağımsız değişkenini akıtma. Koleksiyonlar aynı boyutlarda olmalıdır. Giriş işlevi f ise ve öğeler i0... ve Içinde j0... jN, bu işlev f i0 j0 (...) hesaplar. (jN 'de f)).|
|ForAll|O (N)|O (N)|O (N)|O (N)|O (N)|Koleksiyondaki tüm öğelerin verilen koşulu karşılayıp karşılamadığını sınar.|
|forall2|O (N)|O (N)|O (N)|-|-|Koleksiyonda karşılık gelen tüm öğelerin belirtilen koşulu ikili olarak karşılayıp karşılamadığını sınar.|
|al/n|O (1)|O (N)|O (N)|-|-|Koleksiyondan dizinini verilen bir öğeyi döndürür.|
|başlı|-|O (1)|O (1)|-|-|Koleksiyonun ilk öğesini döndürür.|
|init|O (N)|O (N)|O (1)|-|-|Öğeleri hesaplamak için boyut ve Oluşturucu işlevi verilen bir koleksiyon oluşturur.|
|Initınfinite|-|-|O (1)|-|-|Yinelendiğinde, verilen işlevi çağırarak birbirini izleyen öğeleri döndüren bir dizi oluşturur.|
|intersect|-|-|-|-|O (günlük (N) \* günlük (M))|İki kümenin kesişimini hesaplar.|
|intersectMany|-|-|-|-|O (N1 \* N2...)|Bir küme dizisinin kesişimini hesaplar. Dizi boş olmamalıdır.|
|isEmpty|O (1)|O (1)|O (1)|O (1)|-|`true`Koleksiyonun boş olup olmadığını döndürür.|
|isProperSubset|-|-|-|-|O (M \* günlüğü (N))|`true`İlk küme öğelerinin ikinci küme içinde olup olmadığını ve ikinci küme en az bir öğesinin ilk küme içinde olup olmadığını döndürür.|
|isProperSuperset|-|-|-|-|O (M \* günlüğü (N))|`true`İkinci küme tüm öğeleri ilk küme içinde ise ve ilk küme en az bir öğesi ikinci küme içinde değilse, döndürür.|
|isSubset|-|-|-|-|O (M \* günlüğü (N))|`true`İlk küme öğelerinin ikinci küme içinde olup olmadığını döndürür.|
|isSuperset|-|-|-|-|O (M \* günlüğü (N))|`true`İkinci küme öğelerinin ilk küme içinde olup olmadığını döndürür.|
|Pi|O (N)|O (N)|O (N)|O (N)|O (N)|Verilen işlevi koleksiyonun her öğesine uygular.|
|iteri|O (N)|O (N)|O (N)|-|-|Verilen işlevi koleksiyonun her öğesine uygular. İşleve geçirilen tamsayı, öğenin dizinini gösterir.|
|iteri2|O (N)|O (N)|-|-|-|Verilen işlevi, iki dizide eşleşen indekslerden çizilmiş bir öğe çiftine uygular. İşleve geçirilen tamsayı, öğelerin dizinini gösterir. İki dizi aynı uzunlukta olmalıdır.|
|iter2|O (N)|O (N)|O (N)|-|-|Verilen işlevi, iki dizide eşleşen indekslerden çizilmiş bir öğe çiftine uygular. İki dizi aynı uzunlukta olmalıdır.|
|Son|O (1)|O (N)|O (N)|-|-|Geçerli koleksiyondaki son öğeyi döndürür.|
|length|O (1)|O (N)|O (N)|-|-|Koleksiyondaki öğe sayısını döndürür.|
|map|O (N)|O (N)|O (1)|-|-|Öğeleri verilen işlevin dizinin her öğesine uygulanması sonucu olan bir koleksiyon oluşturur.|
|MAP2|O (N)|O (N)|O (1)|-|-|Öğeleri verilen işlevi iki koleksiyonun karşılık gelen öğelerine ikili olarak uygulamanın sonuçları olan bir koleksiyon oluşturur. İki giriş dizisi aynı uzunlukta olmalıdır.|
|map3|-|O (N)|-|-|-|Öğeleri verilen işlevi üç koleksiyonun karşılık gelen öğelerine aynı anda uygulama sonuçları olan bir koleksiyon oluşturur.|
|hatası|O (N)|O (N)|O (N)|-|-|Öğeleri verilen işlevin dizinin her öğesine uygulanması sonucu olan bir dizi oluşturur. İşleve geçirilen tamsayı dizin, dönüştürülmekte olan öğenin dizinini gösterir.|
|mapi2|O (N)|O (N)|-|-|-|Öğeleri, bu iki koleksiyonun karşılık gelen öğelerine, öğelerin dizinini geçirerek verilen işlevi uygulamanın sonuçları olan bir koleksiyon oluşturur. İki giriş dizisi aynı uzunlukta olmalıdır.|
|max|O (N)|O (N)|O (N)|-|-|[En büyük](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#max) işleç kullanılarak karşılaştırılan koleksiyondaki en büyük öğeyi döndürür.|
|maxBy|O (N)|O (N)|O (N)|-|-|İşlev sonucu üzerinde [Max](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#max) kullanılarak karşılaştırıldığında koleksiyondaki en büyük öğeyi döndürür.|
|maxElement|-|-|-|-|O (günlük (N))|Küme için kullanılan sıralamaya göre küme içindeki en büyük öğeyi döndürür.|
|dk|O (N)|O (N)|O (N)|-|-|[Min](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#min) işleci kullanılarak karşılaştırılan koleksiyonda en az öğeyi döndürür.|
|minBy|O (N)|O (N)|O (N)|-|-|İşlev sonucunda [Min](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#min) işleci kullanılarak karşılaştırılan koleksiyondaki en az öğeyi döndürür.|
|minElement|-|-|-|-|O (günlük (N))|Küme için kullanılan sıralamaya göre küme içindeki en düşük öğeyi döndürür.|
|ofArray|-|O (N)|O (1)|O (N)|O (N)|Verilen dizi ile aynı öğeleri içeren bir koleksiyon oluşturur.|
|ofList|O (N)|-|O (1)|O (N)|O (N)|Verilen liste ile aynı öğeleri içeren bir koleksiyon oluşturur.|
|ofSeq|O (N)|O (N)|-|O (N)|O (N)|Verilen sırayla aynı öğeleri içeren bir koleksiyon oluşturur.|
|yapılandırdı|-|-|O (N)|-|-|Giriş dizisindeki her öğenin bir dizisini ve yalnızca ikinci öğenin öncülü olarak döndürülen ilk öğesi hariç öncülü döndürür.|
|partition|O (N)|O (N)|-|O (N)|O (N)|Koleksiyonu iki koleksiyona böler. İlk koleksiyon, verilen koşulun döndürdüğü öğeleri içerir `true` ve ikinci koleksiyon verilen koşulun döndürdüğü öğeleri içerir `false` .|
|permute|O (N)|O (N)|-|-|-|Belirtilen PERMÜTASYONA göre tüm öğeleri içeren bir dizi döndürür.|
|seçin|O (N)|O (N)|O (N)|O (günlük (N))|-|İşlevin bazılarını döndürdüğü ilk sonucu döndüren ardışık öğelere verilen işlevi uygular. İşlev hiçbir şekilde hiçbir şekilde döndürmezse, `System.Collections.Generic.KeyNotFoundException` tetiklenir.|
|readonly|-|-|O (N)|-|-|Verilen dizi nesnesini temsil eden bir dizi nesnesi oluşturur. Bu işlem, bir tür dönüştürme işleminin özgün sırayı yeniden bulamamasını ve mukutabilmesini sağlar. Örneğin, bir dizi verildiyse, döndürülen dizi dizinin öğelerini döndürür, ancak döndürülen dizi nesnesini bir diziye çevirebilirsiniz.|
|azal|O (N)|O (N)|O (N)|-|-|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Bu işlev, işlevi ilk iki öğeye uygulayarak başlar, bu sonucu, üçüncü öğesiyle birlikte işlevine geçirir ve bu şekilde devam eder. İşlev, nihai sonucu döndürür.|
|reduceBack|O (N)|O (N)|-|-|-|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Giriş işlevi f ise ve öğeler i0... Içinde, bu işlev f i0 (...) hesaplar. (-1 içinde f)).|
|remove|-|-|-|O (günlük (N))|O (günlük (N))|Haritanın etki alanından bir öğeyi kaldırır. Öğe yoksa, hiçbir özel durum harekete geçirilir.|
|çoğaltmak|-|O (N)|-|-|-|Verilen değere ayarlanan her öğe için belirtilen uzunluğun bir listesini oluşturur.|
|düzenleme|O (N)|O (N)|-|-|-|Öğeleri ters sırada olan yeni bir liste döndürür.|
|dığınız|O (N)|O (N)|O (N)|-|-|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Bu işlem, işlevi ikinci bağımsız değişkene ve listenin ilk öğesine uygular. İşlem daha sonra bu sonucu ikinci öğesiyle birlikte işleve geçirir ve bu şekilde devam eder. Son olarak, işlem ara sonuçların ve nihai sonucun listesini döndürür.|
|scanBack|O (N)|O (N)|-|-|-|FoldBack işlemine benzer, ancak hem ara hem de nihai sonuçları döndürür.|
|adet|-|-|O (1)|-|O (1)|Yalnızca bir öğe veren bir sıra döndürür.|
|set|O (1)|-|-|-|-|Bir dizinin bir öğesini belirtilen değere ayarlar.|
|Atla|-|-|O (N)|-|-|Temel alınan sıranın N öğelerini atlayan bir sıra döndürür ve sonra sıranın kalan öğelerini verir.|
|skipWhile|-|-|O (N)|-|-|Yinelendiğinde, belirtilen koşulun döndürdüğü sırada temeldeki sıranın öğelerini atlayan `true` ve sonra dizinin kalan öğelerini verdiği bir diziyi döndürür.|
|sort|O (N \* günlük (n)) Ortalama<br /><br />O (N ^ 2) en kötü durum|O (N \* günlük (n))|O (N \* günlük (n))|-|-|Koleksiyonu öğe değerine göre sıralar. Öğeler [karşılaştırma](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#compare)kullanılarak karşılaştırılır.|
|sortBy|O (N \* günlük (n)) Ortalama<br /><br />O (N ^ 2) en kötü durum|O (N \* günlük (n))|O (N \* günlük (n))|-|-|Verilen projeksiyonun sağladığı anahtarları kullanarak verilen listeyi sıralar. Anahtarlar [Compare](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#compare)kullanılarak karşılaştırılır.|
|sortInPlace|O (N \* günlük (n)) Ortalama<br /><br />O (N ^ 2) en kötü durum|-|-|-|-|Bir dizinin öğelerini yerinde değiştirerek ve verilen karşılaştırma işlevini kullanarak sıralar. Öğeler [Compare](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#compare)kullanılarak karşılaştırılır.|
|sortInPlaceBy|O (N \* günlük (n)) Ortalama<br /><br />O (N ^ 2) en kötü durum|-|-|-|-|Bir dizinin öğelerini yerinde değiştirerek ve anahtarlar için verilen projeksiyonları kullanarak sıralar. Öğeler [Compare](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#compare)kullanılarak karşılaştırılır.|
|sortInPlaceWith|O (N \* günlük (n)) Ortalama<br /><br />O (N ^ 2) en kötü durum|-|-|-|-|Bir dizinin öğelerini yerinde değiştirerek ve sıralama olarak verilen karşılaştırma işlevini kullanarak sıralar.|
|sortWith|O (N \* günlük (n)) Ortalama<br /><br />O (N ^ 2) en kötü durum|O (N \* günlük (n))|-|-|-|Sıralama olarak verilen karşılaştırma işlevini kullanarak bir koleksiyonun öğelerini sıralar ve yeni bir koleksiyon döndürür.|
|alt|O (N)|-|-|-|-|Dizin ve uzunluk başlangıcı tarafından belirtilen verilen alt aralığı içeren bir dizi oluşturur.|
|TOPLA|O (N)|O (N)|O (N)|-|-|Koleksiyondaki öğelerin toplamını döndürür.|
|sumBy|O (N)|O (N)|O (N)|-|-|Koleksiyonun her öğesine işlev uygulanarak oluşturulan sonuçların toplamını döndürür.|
|Connect|-|O (1)|-|-|-|Listeyi ilk öğesi olmadan döndürür.|
|take|-|-|O (N)|-|-|Sıranın belirtilen sayıya kadar olan öğelerini döndürür.|
|takeWhile|-|-|O (1)|-|-|Yinelendiğinde, belirtilen koşulun döndürdüğü sırada temel alınan sıranın öğelerini veren `true` ve daha fazla öğe döndürdüğü bir dizi döndürür.|
|toArray|-|O (N)|O (N)|O (N)|O (N)|Verilen koleksiyondan bir dizi oluşturur.|
|toList|O (N)|-|O (N)|O (N)|O (N)|Verilen koleksiyondan bir liste oluşturur.|
|toSeq|O (1)|O (1)|-|O (1)|O (1)|Verilen koleksiyondan bir dizi oluşturur.|
|kesilemedi|-|-|O (1)|-|-|Numaralandırıldıktan sonra N öğesinden fazla öğe döndürdüğünü belirten bir dizi döndürür.|
|tryFind|O (N)|O (N)|O (N)|O (günlük (N))|-|Belirli bir koşulu karşılayan bir öğe arar.|
|tryFindIndex|O (N)|O (N)|O (N)|-|-|Verilen bir koşulu karşılayan ilk öğeyi arar ve eşleşen öğenin dizinini veya böyle bir öğe yoksa, döndürür `None` .|
|tryFindKey|-|-|-|O (günlük (N))|-|Koleksiyonda verilen koşulu karşılayan ilk eşlemenin anahtarını döndürür veya böyle bir öğe yoksa, döndürür `None` .|
|tryPick|O (N)|O (N)|O (N)|O (günlük (N))|-|İşlevin bazı değerler için döndürdüğü ilk sonucu döndüren ardışık öğelere verilen işlevi uygular `Some` . Böyle bir öğe yoksa, işlem döndürülür `None` .|
|unfold|-|-|O (N)|-|-|Verilen hesaplamanın oluşturduğu öğeleri içeren bir dizi döndürür.|
|birleşim|-|-|-|-|O (M \* günlüğü (N))|İki kümenin birleşimini hesaplar.|
|unionMany|-|-|-|-|O (N1 \* N2...)|Bir küme dizisinin birleşimini hesaplar.|
|sıkıştırmasını açın|O (N)|O (N)|O (N)|-|-|Çiftler listesini iki listeye böler.|
|unzip3|O (N)|O (N)|O (N)|-|-|Üçlü listesini üç listeye böler.|
|e|-|-|O (N)|-|-|Giriş dizisinden çizilen öğeleri içeren kayan pencereler veren bir dizi döndürür. Her pencere yeni bir dizi olarak döndürülür.|
|zip|O (N)|O (N)|O (N)|-|-|İki koleksiyonu çiftler listesi halinde birleştirir. İki liste eşit uzunlukta olmalıdır.|
|zip3|O (N)|O (N)|O (N)|-|-|Üç koleksiyonu üçlü bir liste halinde birleştirir. Listelerin uzunlukları eşit olmalıdır.|

## <a name="see-also"></a>Ayrıca bkz.

- [F# Türleri](fsharp-types.md)
- [F # dil başvurusu](index.md)
