---
title: Koleksiyon türleri
description: Koleksiyon türleri F# ve bunların .NET Framework koleksiyon türlerinden farklı oldukları hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: df34a18e7762c52e169aa8a69709ae16064c134d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628871"
---
# <a name="f-collection-types"></a>F# Koleksiyon Türleri

Bu konuyu inceleyerek, hangi F# koleksiyon türünün belirli bir gereksinim için en uygun olduğunu belirleyebilirsiniz. Bu koleksiyon türleri, F# koleksiyon türlerinin nesne odaklı bir perspektif yerine işlevsel programlama perspektifinden tasarlandıkları `System.Collections.Generic` ad alanındaki koleksiyon türlerinden farklı .NET Framework. Daha belirgin olarak, yalnızca dizi koleksiyonunda kesilebilir öğeler vardır. Bu nedenle, bir koleksiyonu değiştirdiğinizde orijinal koleksiyonu değiştirmek yerine değiştirilmiş koleksiyonun bir örneğini oluşturursunuz.

Koleksiyon türleri, nesnelerin depolandığı veri yapısı türüne de göre farklılık gösterir. Karma tablolar, bağlantılı listeler ve diziler gibi veri yapıları farklı performans özelliklerine ve farklı bir kullanılabilir işlemler kümesine sahiptir.

## <a name="f-collection-types"></a>F# Koleksiyon Türleri

Aşağıdaki tabloda koleksiyon türleri F# gösterilmektedir.

|Tür|Açıklama|İlgili bağlantılar|
|----|-----------|-------------|
|[Listele](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Aynı türdeki sıralı, sabit bir öğe dizisi. Bağlantılı liste olarak uygulanır.|[Listeler](lists.md)<br /><br />[Modül Listele](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Dizide](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Aynı türde olan ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı, kesilebilir bir koleksiyonu.|[Diziler](arrays.md)<br /><br />[Dizi modülü](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2D modülü](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3D modülü](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[sıra](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Tek bir türden oluşan mantıksal dizi öğeleri. Diziler özellikle büyük, sıralı bir veri koleksiyonunuz olduğunda ancak tüm öğeleri kullanmak zorunda olmadığınız durumlarda faydalıdır. Tek tek dizi öğeleri yalnızca gerekli olduğu gibi hesaplanır. bu nedenle, tüm öğeler kullanılmazsa bir sıra bir listeden daha iyi çalışabilir. Diziler, `IEnumerable<T>`için bir diğer ad olan `seq<'T>` türü tarafından temsil edilir. Bu nedenle, `System.Collections.Generic.IEnumerable<'T>` uygulayan .NET Framework her türlü tür bir sıra olarak kullanılabilir.|[Diziler](sequences.md)<br /><br />[Seq modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[Harita](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Öğelerin sabit bir sözlüğü. Öğelere anahtar tarafından erişilir.|[Eşleme Modülü](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Kurmak](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Anahtar değerlerinde `System.IComparable` arabiriminin uygulamalarını kullanan, büyük olasılıkla karşılaştırma F# yapısal karşılaştırma işlevi olduğu, ikili ağaçları temel alan sabit bir küme.|[Modül ayarla](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Işlev tablosu

Bu bölüm, F# koleksiyon türlerinde kullanılabilir olan işlevleri karşılaştırır. İşlevin hesaplama karmaşıklığı verilir, burada N ilk koleksiyonun boyutudur ve d ise ikinci koleksiyonun boyutudur. Kısa çizgi (-) bu işlevin koleksiyonda kullanılabilir olmadığını gösterir. Diziler geç olarak değerlendirildiğinden, Seq. Distinct gibi bir işlev hemen döndürdüğü için O (1) olabilir, ancak numaralandırıldıktan sonra sıranın performansını etkilese de

|İşlev|Dizi|Liste|Sequence|Eşleme|Ayarla|Açıklama|
|--------|-----|----|--------|---|---|-----------|
|ýna|O (N)|O (N)|O (N)|-|-|İkinci koleksiyonun öğeleri tarafından izlenen ilk koleksiyonun öğelerini içeren yeni bir koleksiyon döndürür.|
|add|-|-|-|O (log N)|O (log N)|Eklenen öğe ile yeni bir koleksiyon döndürür.|
|ortalama|O (N)|O (N)|O (N)|-|-|Koleksiyondaki öğelerin ortalamasını döndürür.|
|averageBy|O (N)|O (N)|O (N)|-|-|Her bir öğeye uygulanan, belirtilen işlevin sonuçlarının ortalamasını döndürür.|
|blit|O (N)|-|-|-|-|Dizinin bir bölümünü kopyalar.|
|cache|-|-|O (N)|-|-|Bir dizinin öğelerini hesaplar ve depolar.|
|atama|-|-|O (N)|-|-|Öğeleri belirtilen türe dönüştürür.|
|'yu|O (N)|O (N)|O (N)|-|-|Verilen işlevi `f` listedeki her öğe `x` uygular. İşlevin `Some(f(x))`döndürdüğü her öğe için sonuçları içeren listeyi döndürür.|
|topladıktan|O (N)|O (N)|O (N)|-|-|Verilen işlevi koleksiyonun her öğesine uygular, tüm sonuçları birleştirir ve Birleşik listeyi döndürür.|
|compareWith|-|-|O (N)|-|-|Verilen karşılaştırma işlevini, öğe by öğesi kullanarak iki diziyi karşılaştırır.|
|concat|O (N)|O (N)|O (N)|-|-|Verilen numaralandırmalar numaralandırmayı tek bir birleştirilmiş sabit listesi olarak birleştirir.|
|içerir|-|-|-|-|O (log N)|Küme belirtilen öğeyi içeriyorsa true değerini döndürür.|
|containsKey|-|-|-|O (log N)|-|Bir öğenin bir haritanın etki alanında olup olmadığını test eder.|
|count|-|-|-|-|O (N)|Kümedeki öğelerin sayısını döndürür.|
|countBy|-|-|O (N)|-|-|Bir dizinin her öğesine anahtar oluşturma işlevi uygular ve özgün dizideki benzersiz anahtarlar ve oluşum sayısını veren bir sıra döndürür.|
|copy|O (N)|-|O (N)|-|-|Koleksiyonu kopyalar.|
|oluşturmaya|O (N)|-|-|-|-|Başlangıçta verilen değerin tamamı olan tüm öğelerin bir dizisini oluşturur.|
|delay|-|-|O (1)|-|-|Bir sıranın verilen gecikmeli belirtiminden oluşturulan bir diziyi döndürür.|
|difference|-|-|-|-|O (M &#42; günlüğü N)|İkinci küme, ilk kümeden kaldırılan öğeleri içeren yeni bir küme döndürür.|
|distinct|||O (1)&#42;|||Girdilerde genel karma ve eşitlik karşılaştırmalarına göre yinelenen giriş içermeyen bir dizi döndürür. Bir öğe dizide birden çok kez oluşursa, sonraki oluşumlar atılır.|
|distinctBy|||O (1)&#42;|||Verilen anahtar oluşturma işlevinin döndürdüğü anahtarlarda genel karma ve eşitlik karşılaştırmalarına göre yinelenen giriş içermeyen bir dizi döndürür. Bir öğe dizide birden çok kez oluşursa, sonraki oluşumlar atılır.|
|empty|O (1)|O (1)|O (1)|O (1)|O (1)|Boş bir koleksiyon oluşturur.|
|bulunur|O (N)|O (N)|O (N)|O (log N)|O (log N)|Dizideki herhangi bir öğenin verilen koşulu karşılayıp karşılamadığını sınar.|
|exists2|O (dk (N, M))|-|O (dk (N, M))|||Giriş sıralarının karşılık gelen herhangi bir çiftinin verilen koşulu karşılayıp karşılamadığını sınar.|
|fill|O (N)|||||Dizinin öğe aralığını verilen değere ayarlar.|
|filtre|O (N)|O (N)|O (N)|O (N)|O (N)|Yalnızca verilen koşulun `true`döndürdüğü koleksiyonun öğelerini içeren yeni bir koleksiyon döndürür.|
|find|O (N)|O (N)|O (N)|O (log N)|-|Verilen işlevin `true`döndürdüğü ilk öğeyi döndürür. Böyle bir öğe yoksa `System.Collections.Generic.KeyNotFoundException` döndürür.|
|FindIndex|O (N)|O (N)|O (N)|-|-|Dizideki verilen koşulu karşılayan ilk öğenin dizinini döndürür. Koşula uyan hiçbir öğe yoksa `System.Collections.Generic.KeyNotFoundException` başlatır.|
|findKey|-|-|-|O (log N)|-|Koleksiyondaki her eşlemede işlevi değerlendirir ve işlevin `true`döndürdüğü ilk eşlemenin anahtarını döndürür. Böyle bir öğe yoksa, bu işlev `System.Collections.Generic.KeyNotFoundException`başlatır.|
|ırın|O (N)|O (N)|O (N)|O (N)|O (N)|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Giriş işlevi f ise ve öğeler i0... ' de, bu işlev f 'yi hesaplar (... (f s i0)...) 'ndaki.|
|fold2|O (N)|O (N)|-|-|-|İki koleksiyonun karşılık gelen öğelerine bir işlev uygular ve hesaplama aracılığıyla bir Biriktiricinin bağımsız değişkenini akıtma. Koleksiyonlar aynı boyutlarda olmalıdır. Giriş işlevi f ise ve öğeler i0... ve Içinde j0... jN, bu işlev f 'yi hesaplar (... (f s i0 j0)...) jN.|
|foldBack|O (N)|O (N)|-|O (N)|O (N)|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Giriş işlevi f ise ve öğeler i0... Içinde, bu işlev f i0 (...) hesaplar. (s 'de f)).|
|foldBack2|O (N)|O (N)|-|-|-|İki koleksiyonun karşılık gelen öğelerine bir işlev uygular ve hesaplama aracılığıyla bir Biriktiricinin bağımsız değişkenini akıtma. Koleksiyonlar aynı boyutlarda olmalıdır. Giriş işlevi f ise ve öğeler i0... ve Içinde j0... jN, bu işlev f i0 j0 (...) hesaplar. (jN 'de f)).|
|ForAll|O (N)|O (N)|O (N)|O (N)|O (N)|Koleksiyondaki tüm öğelerin verilen koşulu karşılayıp karşılamadığını sınar.|
|forall2|O (N)|O (N)|O (N)|-|-|Koleksiyonda karşılık gelen tüm öğelerin belirtilen koşulu ikili olarak karşılayıp karşılamadığını sınar.|
|al/n|O (1)|O (N)|O (N)|-|-|Koleksiyondan dizinini verilen bir öğeyi döndürür.|
|başlı|-|O (1)|O (1)|-|-|Koleksiyonun ilk öğesini döndürür.|
|init|O (N)|O (N)|O (1)|-|-|Öğeleri hesaplamak için boyut ve Oluşturucu işlevi verilen bir koleksiyon oluşturur.|
|Initınfinite|-|-|O (1)|-|-|Yinelendiğinde, verilen işlevi çağırarak birbirini izleyen öğeleri döndüren bir dizi oluşturur.|
|kesiş|-|-|-|-|O (günlük N &#42; günlük M)|İki kümenin kesişimini hesaplar.|
|intersectMany|-|-|-|-|O (N1 &#42; N2...)|Bir küme dizisinin kesişimini hesaplar. Dizi boş olmamalıdır.|
|IsEmpty|O (1)|O (1)|O (1)|O (1)|-|Koleksiyon boşsa `true` döndürür.|
|isProperSubset|-|-|-|-|O (M &#42; günlüğü N)|İlk küme tüm öğeleri ikinci küme içinde ise ve ikinci küme en az bir öğesi ilk küme içinde değilse `true` döndürür.|
|isProperSuperset|-|-|-|-|O (M &#42; günlüğü N)|İkinci küme tüm öğeleri ilk küme içinde ise ve ilk küme en az bir öğesi ikinci küme içinde değilse `true` döndürür.|
|isSubset|-|-|-|-|O (M &#42; günlüğü N)|İlk küme tüm öğeleri ikinci küme içinde ise `true` döndürür.|
|isSuperset|-|-|-|-|O (M &#42; günlüğü N)|İkinci küme tüm öğeleri ilk küme içinde ise `true` döndürür.|
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
|max|O (N)|O (N)|O (N)|-|-|[En büyük](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) işleç kullanılarak karşılaştırılan koleksiyondaki en büyük öğeyi döndürür.|
|maxBy|O (N)|O (N)|O (N)|-|-|İşlev sonucu üzerinde [Max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) kullanılarak karşılaştırıldığında koleksiyondaki en büyük öğeyi döndürür.|
|maxElement|-|-|-|-|O (log N)|Küme için kullanılan sıralamaya göre küme içindeki en büyük öğeyi döndürür.|
|min|O (N)|O (N)|O (N)|-|-|[Min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) işleci kullanılarak karşılaştırılan koleksiyonda en az öğeyi döndürür.|
|minBy|O (N)|O (N)|O (N)|-|-|İşlev sonucunda [Min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) işleci kullanılarak karşılaştırılan koleksiyondaki en az öğeyi döndürür.|
|minElement|-|-|-|-|O (log N)|Küme için kullanılan sıralamaya göre küme içindeki en düşük öğeyi döndürür.|
|ofArray|-|O (N)|O (1)|O (N)|O (N)|Verilen dizi ile aynı öğeleri içeren bir koleksiyon oluşturur.|
|ofList|O (N)|-|O (1)|O (N)|O (N)|Verilen liste ile aynı öğeleri içeren bir koleksiyon oluşturur.|
|ofSeq|O (N)|O (N)|-|O (N)|O (N)|Verilen sırayla aynı öğeleri içeren bir koleksiyon oluşturur.|
|yapılandırdı|-|-|O (N)|-|-|Giriş dizisindeki her öğenin bir dizisini ve yalnızca ikinci öğenin öncülü olarak döndürülen ilk öğesi hariç öncülü döndürür.|
|partition|O (N)|O (N)|-|O (N)|O (N)|Koleksiyonu iki koleksiyona böler. İlk koleksiyon, verilen koşulun `true`döndürdüğü öğeleri içerir ve ikinci koleksiyon, verilen koşulun `false`döndürdüğü öğeleri içerir.|
|permute|O (N)|O (N)|-|-|-|Belirtilen PERMÜTASYONA göre tüm öğeleri içeren bir dizi döndürür.|
|seçin|O (N)|O (N)|O (N)|O (log N)|-|İşlevin bazılarını döndürdüğü ilk sonucu döndüren ardışık öğelere verilen işlevi uygular. İşlev hiçbir şekilde hiç bir değer döndürmüyorsa `System.Collections.Generic.KeyNotFoundException` tetiklenir.|
|readonly|-|-|O (N)|-|-|Verilen dizi nesnesini temsil eden bir dizi nesnesi oluşturur. Bu işlem, bir tür dönüştürme işleminin özgün sırayı yeniden bulamamasını ve mukutabilmesini sağlar. Örneğin, bir dizi verildiyse, döndürülen dizi dizinin öğelerini döndürür, ancak döndürülen dizi nesnesini bir diziye çevirebilirsiniz.|
|azal|O (N)|O (N)|O (N)|-|-|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Bu işlev, işlevi ilk iki öğeye uygulayarak başlar, bu sonucu, üçüncü öğesiyle birlikte işlevine geçirir ve bu şekilde devam eder. İşlev, nihai sonucu döndürür.|
|reduceBack|O (N)|O (N)|-|-|-|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Giriş işlevi f ise ve öğeler i0... Içinde, bu işlev f i0 (...) hesaplar. (-1 içinde f)).|
|remove|-|-|-|O (log N)|O (log N)|Haritanın etki alanından bir öğeyi kaldırır. Öğe yoksa, hiçbir özel durum harekete geçirilir.|
|çoğaltmak|-|O (N)|-|-|-|Verilen değere ayarlanan her öğe için belirtilen uzunluğun bir listesini oluşturur.|
|düzenleme|O (N)|O (N)|-|-|-|Öğeleri ters sırada olan yeni bir liste döndürür.|
|dığınız|O (N)|O (N)|O (N)|-|-|Koleksiyonun her öğesine bir işlev uygular ve hesaplama aracılığıyla bir biriktiricidir bağımsız değişkenini akıtma. Bu işlem, işlevi ikinci bağımsız değişkene ve listenin ilk öğesine uygular. İşlem daha sonra bu sonucu ikinci öğesiyle birlikte işleve geçirir ve bu şekilde devam eder. Son olarak, işlem ara sonuçların ve nihai sonucun listesini döndürür.|
|scanBack|O (N)|O (N)|-|-|-|FoldBack işlemine benzer, ancak hem ara hem de nihai sonuçları döndürür.|
|Adet|-|-|O (1)|-|O (1)|Yalnızca bir öğe veren bir sıra döndürür.|
|set|O (1)|-|-|-|-|Bir dizinin bir öğesini belirtilen değere ayarlar.|
|Atla|-|-|O (N)|-|-|Temel alınan sıranın N öğelerini atlayan bir sıra döndürür ve sonra sıranın kalan öğelerini verir.|
|skipWhile|-|-|O (N)|-|-|Yinelendiğinde, belirtilen koşulun `true` döndürdüğü sırada temeldeki sıranın öğelerini atlayan, sonra da sıranın kalan öğelerini verdiği bir dizi döndürür.|
|sort|O (N günlük N) Ortalama<br /><br />O (N ^ 2) en kötü durum|O (N günlük N)|O (N günlük N)|-|-|Koleksiyonu öğe değerine göre sıralar. Öğeler [karşılaştırma](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)kullanılarak karşılaştırılır.|
|sortBy|O (N günlük N) Ortalama<br /><br />O (N ^ 2) en kötü durum|O (N günlük N)|O (N günlük N)|-|-|Verilen projeksiyonun sağladığı anahtarları kullanarak verilen listeyi sıralar. Anahtarlar [Compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)kullanılarak karşılaştırılır.|
|sortInPlace|O (N günlük N) Ortalama<br /><br />O (N ^ 2) en kötü durum|-|-|-|-|Bir dizinin öğelerini yerinde değiştirerek ve verilen karşılaştırma işlevini kullanarak sıralar. Öğeler [Compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)kullanılarak karşılaştırılır.|
|sortInPlaceBy|O (N günlük N) Ortalama<br /><br />O (N ^ 2) en kötü durum|-|-|-|-|Bir dizinin öğelerini yerinde değiştirerek ve anahtarlar için verilen projeksiyonları kullanarak sıralar. Öğeler [Compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)kullanılarak karşılaştırılır.|
|sortInPlaceWith|O (N günlük N) Ortalama<br /><br />O (N ^ 2) en kötü durum|-|-|-|-|Bir dizinin öğelerini yerinde değiştirerek ve sıralama olarak verilen karşılaştırma işlevini kullanarak sıralar.|
|sortWith|O (N günlük N) Ortalama<br /><br />O (N ^ 2) en kötü durum|O (N günlük N)|-|-|-|Sıralama olarak verilen karşılaştırma işlevini kullanarak bir koleksiyonun öğelerini sıralar ve yeni bir koleksiyon döndürür.|
|sub|O (N)|-|-|-|-|Dizin ve uzunluk başlangıcı tarafından belirtilen verilen alt aralığı içeren bir dizi oluşturur.|
|TOPLA|O (N)|O (N)|O (N)|-|-|Koleksiyondaki öğelerin toplamını döndürür.|
|sumBy|O (N)|O (N)|O (N)|-|-|Koleksiyonun her öğesine işlev uygulanarak oluşturulan sonuçların toplamını döndürür.|
|Connect|-|O (1)|-|-|-|Listeyi ilk öğesi olmadan döndürür.|
|take|-|-|O (N)|-|-|Sıranın belirtilen sayıya kadar olan öğelerini döndürür.|
|takeWhile|-|-|O (1)|-|-|Yinelendiğinde, belirtilen koşulun `true` döndürdüğü sırada temel alınan sıranın öğelerini veren bir dizi döndürür ve daha fazla öğe döndürmez.|
|toArray|-|O (N)|O (N)|O (N)|O (N)|Verilen koleksiyondan bir dizi oluşturur.|
|toList|O (N)|-|O (N)|O (N)|O (N)|Verilen koleksiyondan bir liste oluşturur.|
|toSeq|O (1)|O (1)|-|O (1)|O (1)|Verilen koleksiyondan bir dizi oluşturur.|
|kesilemedi|-|-|O (1)|-|-|Numaralandırıldıktan sonra N öğesinden fazla öğe döndürdüğünü belirten bir dizi döndürür.|
|tryFind|O (N)|O (N)|O (N)|O (log N)|-|Belirli bir koşulu karşılayan bir öğe arar.|
|tryFindIndex|O (N)|O (N)|O (N)|-|-|Verilen bir koşulu karşılayan ilk öğeyi arar ve eşleşen öğenin dizinini döndürür veya böyle bir öğe yoksa `None`.|
|tryFindKey|-|-|-|O (log N)|-|Koleksiyonda verilen koşulu karşılayan ilk eşlemenin anahtarını döndürür veya böyle bir öğe yoksa `None` döndürür.|
|tryPick|O (N)|O (N)|O (N)|O (log N)|-|İşlevin bazı değerler için `Some` döndürdüğü ilk sonucu döndüren ardışık öğelere verilen işlevi uygular. Böyle bir öğe yoksa, işlem `None`döndürür.|
|unfold|-|-|O (N)|-|-|Verilen hesaplamanın oluşturduğu öğeleri içeren bir dizi döndürür.|
|birleşim|-|-|-|-|O (M &#42; günlüğü N)|İki kümenin birleşimini hesaplar.|
|unionMany|-|-|-|-|O (N1 &#42; N2...)|Bir küme dizisinin birleşimini hesaplar.|
|sıkıştırmasını açın|O (N)|O (N)|O (N)|-|-|Çiftler listesini iki listeye böler.|
|unzip3|O (N)|O (N)|O (N)|-|-|Üçlü listesini üç listeye böler.|
|e|-|-|O (N)|-|-|Giriş dizisinden çizilen öğeleri içeren kayan pencereler veren bir dizi döndürür. Her pencere yeni bir dizi olarak döndürülür.|
|zip|O (N)|O (N)|O (N)|-|-|İki koleksiyonu çiftler listesi halinde birleştirir. İki liste eşit uzunlukta olmalıdır.|
|zip3|O (N)|O (N)|O (N)|-|-|Üç koleksiyonu üçlü bir liste halinde birleştirir. Listelerin uzunlukları eşit olmalıdır.|

## <a name="see-also"></a>Ayrıca bkz.

- [F# Türleri](fsharp-types.md)
- [F# Dili Başvurusu](index.md)
