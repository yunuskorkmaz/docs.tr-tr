---
title: F# Koleksiyon Türleri
description: "F # koleksiyon türleri ve bunlar .NET Framework'teki koleksiyon türlerinden farklılıklar hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: a3cfc3f06582c31a79dce43b583eca39f69ddf1e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864767"
---
# <a name="f-collection-types"></a>F# Koleksiyon Türleri

Bu konuyu gözden geçirerek hangi F # koleksiyon türü en iyi uyan belirli bir gereksinimi belirleyebilirsiniz. Bu koleksiyon türleri olanlar gibi .NET Framework koleksiyon türlerini farklı `System.Collections.Generic` ad alanı, F # koleksiyon türleri nesne yönelimli bir perspektif yerine işlevsel programlama perspektif tasarlanmış olmasıdır. Özellikle, yalnızca dizi koleksiyon değişebilir öğelere sahiptir. Bu nedenle, bir koleksiyon değiştirdiğinizde, özgün koleksiyon değiştirme yerine değiştirilen koleksiyonu bir örneğini oluşturun.

Koleksiyon türleri, nesneleri depolandığı veri yapısı türü ayrıca farklı. Karma tabloları, bağlantılı liste ve diziler gibi veri yapıları farklı performans özellikleri ve kullanılabilir işlemleri farklı bir dizi var.

## <a name="f-collection-types"></a>F# Koleksiyon Türleri

Aşağıdaki tabloda, F # koleksiyon türleri gösterilmiştir.

|Tür|Açıklama|İlgili bağlantılar|
|----|-----------|-------------|
|[Liste](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Bir sıralı, sabit dizi öğeleri aynı türde. Bağlı bir liste uygulanır.|[Listeler](lists.md)<br /><br />[List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Dizi](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Tümü aynı türde olan ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı, değişebilir bir koleksiyonu.|[Diziler](arrays.md)<br /><br />[Array Modülü](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2D Modülü](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3D Modülü](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[Seq](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Tümü tek öğeleri mantıksal bir dizi. Veri koleksiyonu sıralı bir büyük, varsa, ancak tüm öğeleri kullanmak mutlaka beklemiyoruz dizileri özellikle yararlı olur. Tek tek sırası öğeleri yalnızca'olarak hesaplanır, yoksa bir dizisi listesini daha iyi gerçekleştirebilir, böylece tüm öğeleri kullanılan gerekmez. Dizileri olarak temsil edilir `seq<'T>` bir diğer ad türü için `IEnumerable<T>`. Bu nedenle, uygulayan bir .NET Framework tür `System.Collections.Generic.IEnumerable<'T>` dizisi olarak kullanılabilir.|[Diziler](sequences.md)<br /><br />[Seq Modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[Harita](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Öğe değişmez bir sözlük. Öğeleri anahtar tarafından erişilir.|[Map Modülü](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Ayarlayın](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Karşılaştırma olduğu F # Yapısal karşılaştırma işlevi, büyük olasılıkla uygulamalarını kullanan ikili ağaçları temel alan bir sabit kümesi `System.IComparable` anahtar değerler üzerinden arabirimi.|[Set Modülü](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tablo işlevleri

Bu bölümde, F # koleksiyon türleri üzerinde kullanılabilir olan işlevlerin karşılaştırır. Burada N birinci koleksiyon boyutudur ve M ikinci koleksiyon boyutu varsa işlevi hesaplama karmaşıklığını verilir. Bir tire (-) Bu işlev koleksiyonu üzerinde kullanılabilir olmadığını gösterir. Dizileri gevşek değerlendirildiği için hemen döndürüldüğünden rağmen yine de numaralandırıldığı zaman dizisi performansını etkiler Seq.distinct gibi bir işlevi O(1) olabilir.

|İşlev|Dizi|List|Dizisi|Harita|Ayarlayın|Açıklama|
|--------|-----|----|--------|---|---|-----------|
|Ekleme|O(M)|O(N)|O(N)|-|-|İlk koleksiyonun ikinci koleksiyon öğelerini tarafından izlenen öğeleri içeren yeni bir koleksiyon döndürür.|
|add|-|-|-|O (log N)|O (log N)|Eklenen öğeyi yeni bir koleksiyon döndürür.|
|Ortalama|O(N)|O(N)|O(N)|-|-|Koleksiyondaki öğelerin ortalamasını döndürür.|
|averageBy|O(N)|O(N)|O(N)|-|-|Her öğeye uygulanan sağlanan işlev sonuçlarının ortalamasını döndürür.|
|blit|O(N)|-|-|-|-|Bir dizinin bir bölümünü kopyalar.|
|önbellek|-|-|O(N)|-|-|Hesaplar ve bir dizi öğelerini depolar.|
|atama|-|-|O(N)|-|-|Öğeleri belirtilen türe dönüştürür.|
|Seçin|O(N)|O(N)|O(N)|-|-|Verilen işlevi uygular `f` her öğeye `x` listesi. İşlevin döndüğü her öğe için sonuçları içeren listesini döndürür `Some(f(x))`.|
|TOPLA|O(N)|O(N)|O(N)|-|-|Koleksiyonun her öğesine verilen işlevi uygular, tüm sonuçları art arda ekler ve birleşik listeyi döndürür.|
|compareWith|-|-|O(N)|-|-|İki diziyi öğe öğe verilen karşılaştırma işlevini kullanarak karşılaştırır.|
|concat|O(N)|O(N)|O(N)|-|-|Belirtilen numaralandırma-,-sabit listeleri tek bir birleştirilmiş sabit listesi olarak birleştirir.|
|içerir|-|-|-|-|O (log N)|Küme belirtilen öğeyi içeriyorsa true döndürür.|
|containsKey|-|-|-|O (log N)|-|Bir öğenin bir harita etki alanında olup olmadığını test eder.|
|count|-|-|-|-|O(N)|Kümedeki öğelerin sayısını döndürür.|
|countBy|-|-|O(N)|-|-|Bir dizinin her öğesi için bir anahtar oluşturuluyor işlevi uygulanır ve benzersiz anahtarları ve kendi özgün dizideki yinelenme sayısını verir bir dizisini döndürür.|
|copy|O(N)|-|O(N)|-|-|Koleksiyon kopyalar.|
|oluşturma|O(N)|-|-|-|-|Tüm başlangıçta belirtilen değere eşit olan tüm öğeleri bir dizi oluşturur.|
|gecikme|-|-|O(1)|-|-|Oluşturulan bir sıralı bir dizi belirli gecikmeli belirtiminden döndürür.|
|difference|-|-|-|-|O (M &#42; log N)|İlk kümeden kaldırılmış ikinci kümenin öğeleri ile yeni bir küme döndürür.|
|Farklı|||O(1)&AMP;#42;|||Genel karma ve eşitlik karşılaştırmaları girişlere göre yinelenen giriş olmadığından içeren bir dizi döndürür. Bir öğe sırasını birden çok kez oluşursa, sonraki örnekleri atılır.|
|distinctBy|||O(1)&AMP;#42;|||Belirtilen anahtar oluşturuluyor işlevinin döndürdüğü anahtarlar genel karma ve eşitlik karşılaştırmaları göre yinelenen giriş olmadığından içeren bir dizi döndürür. Bir öğe sırasını birden çok kez oluşursa, sonraki örnekleri atılır.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Boş bir koleksiyon oluşturur.|
|Var.|O(N)|O(N)|O(N)|O (log N)|O (log N)|Herhangi bir öğe dizisi belirtilen koşulu karşılayıp karşılamadığını test eder.|
|exists2|O(Min(N,M))|-|O(Min(N,M))|||Herhangi bir karşılık gelen öğe giriş dizilerinin çiftinin belirtilen koşulu karşılayıp karşılamadığını test eder.|
|fill|O(N)|||||Dizideki öğe aralığını belirtilen değere ayarlar.|
|filtre|O(N)|O(N)|O(N)|O(N)|O(N)|Yalnızca belirli bir koşul döndüğü koleksiyonun öğeleri içeren yeni bir koleksiyon döndürür `true`.|
|find|O(N)|O(N)|O(N)|O (log N)|-|Verilen işlevin döndüğü ilk öğeyi döndürür `true`. Döndürür `System.Collections.Generic.KeyNotFoundException` böyle bir öğe varsa.|
|findIndex|O(N)|O(N)|O(N)|-|-|Belirli bir koşulu karşılayan dizideki ilk öğenin dizinini döndürür. Başlatır `System.Collections.Generic.KeyNotFoundException` herhangi bir öğe koşulu karşılıyorsa.|
|findKey|-|-|-|O (log N)|-|Koleksiyondaki her eşleme işlev değerlendirir ve işlevin döndüğü ilk eşleme anahtarını döndürür `true`. Böyle bir öğe varsa, bu işlev başlatır `System.Collections.Generic.KeyNotFoundException`.|
|Katlama|O(N)|O(N)|O(N)|O(N)|O(N)|İşlevi, iş parçacığı hesaplama accumulator bağımsız değişken, koleksiyonun her öğesine uygular. F Giriş işlevi ise ve i0... içindeki öğelerin çoğu, bu işlev, f (...) hesaplar. (f s i0)...) .|
|fold2|O(N)|O(N)|-|-|-|Bir işlev hesaplama accumulator bağımsız değişken iş parçacığı, iki koleksiyon karşılık gelen öğelere uygulanır. Koleksiyonları aynı boyutlarına sahip olmalıdır. Giriş işlevi f ve öğeler içinde i0... ve j0... jN, bu işlev, f (...) hesaplar. (f s i0 j0)...) İçinde jN.|
|foldBack|O(N)|O(N)|-|O(N)|O(N)|İşlevi, iş parçacığı hesaplama accumulator bağımsız değişken, koleksiyonun her öğesine uygular. F Giriş işlevi ise ve i0... içindeki öğelerin çoğu, bu işleve f i0 hesaplar (...) (f s)).|
|foldBack2|O(N)|O(N)|-|-|-|Bir işlev hesaplama accumulator bağımsız değişken iş parçacığı, iki koleksiyon karşılık gelen öğelere uygulanır. Koleksiyonları aynı boyutlarına sahip olmalıdır. Giriş işlevi f ve öğeler içinde i0... ve j0... jN, bu işleve f i0 j0 hesaplar (...) (f jN s)).|
|forall|O(N)|O(N)|O(N)|O(N)|O(N)|Tüm koleksiyon öğelerini belirli bir koşul karşılamak olup olmadığını sınar.|
|forall2|O(N)|O(N)|O(N)|-|-|Karşılık gelen tüm koleksiyon öğelerini belirli bir koşul ikili karşılamak olup olmadığını sınar.|
|Alma / n.|O(1)|O(N)|O(N)|-|-|Bir öğenin dizinini verilen koleksiyondan döndürür.|
|HEAD|-|O(1)|O(1)|-|-|Koleksiyonun ilk öğesine döndürür.|
|Init|O(N)|O(N)|O(1)|-|-|Boyutu ve öğeleri hesaplamak için oluşturucu işlevi verilen bir koleksiyon oluşturur.|
|initInfinite|-|-|O(1)|-|-|Bir sıra üretir, yinelendiğinde ardışık öğeleri verilen işlevin çağırarak döndürür.|
|INTERSECT|-|-|-|-|O (log N &#42; günlük M)|İki kümenin kesişimini hesaplar.|
|intersectMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Bir dizi kümenin kesişimini hesaplar. Sıra boş olmamalıdır.|
|IsEmpty|O(1)|O(1)|O(1)|O(1)|-|Döndürür `true` koleksiyonu boş ise.|
|isProperSubset|-|-|-|-|O (M &#42; log N)|Döndürür `true` ilk kümenin tüm öğeleri ikinci küme içindedir ve ikinci kümenin en az bir öğesi olmayan ilk ayarlayın.|
|isProperSuperset|-|-|-|-|O (M &#42; log N)|Döndürür `true` ikinci kümenin tüm öğeleri ilk küme içindedir ve ikinci kümede ilk kümenin en az bir öğe değil.|
|isSubset|-|-|-|-|O (M &#42; log N)|Döndürür `true` ilk kümenin tüm öğeleri ikinci kümede ise.|
|isSuperset|-|-|-|-|O (M &#42; log N)|Döndürür `true` ise ikinci kümenin tüm öğeleri ilk ayarlayın.|
|Iter|O(N)|O(N)|O(N)|O(N)|O(N)|Koleksiyonun her öğesine verilen işlevi uygular.|
|iteri|O(N)|O(N)|O(N)|-|-|Koleksiyonun her öğesine verilen işlevi uygular. İşleve geçirilen tamsayı, öğenin dizinini gösterir.|
|iteri2|O(N)|O(N)|-|-|-|Dizinleri iki dizideki eşleşen dizinden çekilen bir öğe çiftine verilen işlevi uygular. İşleve geçirilen tamsayı elementler dizinini gösterir. İki dizi aynı uzunlukta olmalıdır.|
|iter2|O(N)|O(N)|O(N)|-|-|Dizinleri iki dizideki eşleşen dizinden çekilen bir öğe çiftine verilen işlevi uygular. İki dizi aynı uzunlukta olmalıdır.|
|length|O(1)|O(N)|O(N)|-|-|Koleksiyondaki öğe sayısını döndürür.|
|map|O(N)|O(N)|O(1)|-|-|Öğeleri verilen işlevin dizinin her öğesine uygulanması sonucu olan bir koleksiyon oluşturur.|
|map2|O(N)|O(N)|O(1)|-|-|Öğeleri verilen işlevin iki koleksiyon karşılık gelen öğelerle için ikili uygulanması sonucu olan bir koleksiyon oluşturur. Giriş iki dizi aynı uzunlukta olmalıdır.|
|map3|-|O(N)|-|-|-|Öğeleri verilen işlevin koleksiyonların karşılık gelen öğelerle için aynı anda uygulanması sonucu olan bir koleksiyon oluşturur.|
|MAPI|O(N)|O(N)|O(N)|-|-|Öğeleri verilen işlevin dizinin her öğesine uygulanması sonucu olan bir dizi oluşturur. İşleve geçirilen tamsayı dizini dönüştürülmekte olan öğenin dizinini gösterir.|
|mapi2|O(N)|O(N)|-|-|-|Öğeleri verilen işlevi öğelerin dizinini geçirerek ikili iki koleksiyon karşılık gelen öğelerle için uygulanması sonucu olan bir koleksiyon oluşturur. Giriş iki dizi aynı uzunlukta olmalıdır.|
|max|O(N)|O(N)|O(N)|-|-|Koleksiyondaki kullanarak karşılaştırıldığında en büyük öğeyi döndürür [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) işleci.|
|maxBy|O(N)|O(N)|O(N)|-|-|Koleksiyondaki kullanarak karşılaştırıldığında en büyük öğeyi döndürür [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) üzerinde işlev sonucu.|
|maxElement|-|-|-|-|O (log N)|Küme için kullanılan sıralamaya göre kümedeki en büyük öğeyi döndürür.|
|min|O(N)|O(N)|O(N)|-|-|Koleksiyondaki kullanarak karşılaştırıldığında en düşük öğeyi döndürür [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) işleci.|
|minBy|O(N)|O(N)|O(N)|-|-|Koleksiyondaki kullanarak karşılaştırıldığında en düşük öğeyi döndürür [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) işlecinin işlev sonucu.|
|minElement|-|-|-|-|O (log N)|Küme için kullanılan sıralamaya göre kümedeki en düşük öğeyi döndürür.|
|ofArray|-|O(N)|O(1)|O(N)|O(N)|Belirtilen dizinin aynı öğeleri içeren bir koleksiyon oluşturur.|
|ofList|O(N)|-|O(1)|O(N)|O(N)|Belirtilen liste aynı öğeleri içeren bir koleksiyon oluşturur.|
|ofSeq|O(N)|O(N)|-|O(N)|O(N)|Belirli bir dizi aynı öğeleri içeren bir koleksiyon oluşturur.|
|ikili|-|-|O(N)|-|-|Giriş dizisi ve onun önceli öncül yalnızca ikinci öğe döndürülen ilk öğe dışında her öğesinin bir dizisi döndürür.|
|partition|O(N)|O(N)|-|O(N)|O(N)|Koleksiyonu iki koleksiyona ayırır. Birinci koleksiyon için belirli bir koşul döndüren öğeleri içeren `true`, ve ikinci koleksiyon için belirli bir koşul dönen öğeleri içeren `false`.|
|permute|O(N)|O(N)|-|-|-|Tüm öğeleri dizilmiş permütasyon göre bir dizi döndürür.|
|Çekme|O(N)|O(N)|O(N)|O (log N)|-|İşlevin bazı döndüğü ilk sonucu döndürerek ardışık öğeleri için verilen işlevi uygular. İşlev hiçbir zaman bazıları döndürürse `System.Collections.Generic.KeyNotFoundException` tetiklenir.|
|readonly|-|-|O(N)|-|-|Belirli bir dizi nesnesini temsil eden bir dizi nesnesi oluşturur. Bu işlem, bir cast türünü yeniden Bul olamaz ve orijinal sıranın bulunmamalıdır sağlar. Örneğin, bir dizi varsa, döndürülen dizi dizinin öğeleri döndürür, ancak döndürülen dizi nesnesi bir dizi türüne dönüştürülemiyor.|
|azaltın|O(N)|O(N)|O(N)|-|-|İşlevi, iş parçacığı hesaplama accumulator bağımsız değişken, koleksiyonun her öğesine uygular. Bu işlev ilk iki öğelerine işlevi uygulayarak başlatır, bu sonuç üçüncü öğe ve benzeri birlikte işleve geçirir. İşlev sonucunu döndürür.|
|reduceBack|O(N)|O(N)|-|-|-|İşlevi, iş parçacığı hesaplama accumulator bağımsız değişken, koleksiyonun her öğesine uygular. F Giriş işlevi ise ve i0... içindeki öğelerin çoğu, bu işleve f i0 hesaplar (...) (f,-1'de)).|
|remove|-|-|-|O (log N)|O (log N)|Bir öğeyi harita etki alanından kaldırır. Öğe yoksa hiçbir özel durum oluşturulur.|
|Çoğaltma|-|O(N)|-|-|-|Her öğeyi belirtilen değere ayarlar ile belirtilen uzunluktaki bir liste oluşturur.|
|Rev|O(N)|O(N)|-|-|-|Yeni liste öğeleri ters sırada döndürür.|
|Tarama|O(N)|O(N)|O(N)|-|-|İşlevi, iş parçacığı hesaplama accumulator bağımsız değişken, koleksiyonun her öğesine uygular. Bu işlem, ikinci bağımsız değişkeni ve listedeki ilk öğe işlevi uygulanır. İşleminin ardından bu sonuç ikinci öğe birlikte işleve vb. geçirir. Son olarak, işlem Ara sonuçlar ve nihai sonucu listesini döndürür.|
|scanBack|O(N)|O(N)|-|-|-|FoldBack işlemi benzer, ancak ara ve son sonuçları döndürür.|
|singleton|-|-|O(1)|-|O(1)|Yalnızca bir öğe verir bir dizisini döndürür.|
|set|O(1)|-|-|-|-|Bir dizideki bir öğe için belirtilen değere ayarlar.|
|Atla|-|-|O(N)|-|-|Temel alınan dizi N öğesini atlayan ve ardından kalan öğeleri dizisi üretir bir dizisini döndürür.|
|SkipWhile|-|-|O(N)|-|-|Yinelendiğinde temel alınan dizi öğelerini belirtilen koşul döndürür çalışırken, dizisi döndürür `true` ve ardından dizinin kalan öğeleri verir.|
|sort|Ortalama O (log N N)<br /><br />O(N^2) en kötü durumda|O (log N N)|O (log N N)|-|-|Koleksiyon öğesi değere göre sıralar. Öğeleri kullanılarak karşılaştırılır [karşılaştırma](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Ortalama O (log N N)<br /><br />O(N^2) en kötü durumda|O (log N N)|O (log N N)|-|-|Verilen projeksiyon sağlayan tuşlarını kullanarak verilen listeyi sıralar. Anahtarları kullanarak karşılaştırılır [karşılaştırma](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|Sortınplace|Ortalama O (log N N)<br /><br />O(N^2) en kötü durumda|-|-|-|-|Yerinde diziyi ve verilen karşılaştırma işlevini kullanarak bir dizinin öğeleri sıralar. Öğeleri kullanılarak karşılaştırılır [karşılaştırma](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy|Ortalama O (log N N)<br /><br />O(N^2) en kötü durumda|-|-|-|-|Yerinde diziyi ve verilen projeksiyon anahtarlarını kullanarak bir dizinin öğeleri sıralar. Öğeleri kullanılarak karşılaştırılır [karşılaştırma](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith|Ortalama O (log N N)<br /><br />O(N^2) en kötü durumda|-|-|-|-|Yerinde diziyi ve siparişi olarak verilen karşılaştırma işlevini kullanarak bir dizinin öğeleri sıralar.|
|sortWith|Ortalama O (log N N)<br /><br />O(N^2) en kötü durumda|O (log N N)|-|-|-|Sırada verilen karşılaştırma işlevini kullanarak ve yeni bir koleksiyon döndüren bir koleksiyonun öğeleri sıralar.|
|alt|O(N)|-|-|-|-|İNDİS ve uzunluk başlatarak belirtilen belirli alt aralığı içeren bir dizi oluşturur.|
|TOPLA|O(N)|O(N)|O(N)|-|-|Koleksiyondaki öğelerin toplamını döndürür.|
|sumBy|O(N)|O(N)|O(N)|-|-|Koleksiyonun her öğesine işlevi uygulayarak oluşturulan sonuçları toplamını döndürür.|
|Tail|-|O(1)|-|-|-|İlk öğesi olmayan listesi döndürür.|
|sınav zamanı|-|-|O(N)|-|-|Belirtilen sayı kadar dizisinin döndürür.|
|TakeWhile|-|-|O(1)|-|-|Yinelendiğinde temel alınan dizi öğelerini sayıları belirtilen koşul döndürür çalışırken, dizisi döndürür `true` ve daha fazla öğe döndürür.|
|ToArray|-|O(N)|O(N)|O(N)|O(N)|Sağlanan koleksiyondan bir dizi oluşturur.|
|ToList|O(N)|-|O(N)|O(N)|O(N)|Sağlanan koleksiyondan bir liste oluşturur.|
|toSeq|O(1)|O(1)|-|O(1)|O(1)|Sağlanan koleksiyondan bir dizi oluşturur.|
|Kes|-|-|O(1)|-|-|Bir dizi, numaralandırılan en fazla N öğeleri döndürür döner.|
|tryFind|O(N)|O(N)|O(N)|O (log N)|-|Belirli bir koşulu karşılayan bir öğe arar.|
|tryFindIndex|O(N)|O(N)|O(N)|-|-|Belirli bir koşulu karşılayan ve eşleşen öğenin dizinini döndüren ilk öğeyi arar veya `None` böyle bir öğe varsa.|
|tryFindKey|-|-|-|O (log N)|-|Belirli bir koşulu karşılayan ya da döndürür koleksiyonda ilk eşleme anahtarını döndürür `None` böyle bir öğe varsa.|
|tryPick|O(N)|O(N)|O(N)|O (log N)|-|İşlevin döndüğü ilk sonucu döndürerek ardışık öğeleri için verilen işlevi uygular `Some` bazı değeri. Böyle bir öğe var olup olmadığını döndürür işlemi `None`.|
|düzleştirme|-|-|O(N)|-|-|Verilen hesaplamayı oluşturan öğeleri içeren bir dizi döndürür.|
|birleşim|-|-|-|-|O (M &#42; log N)|İki kümenin birleşimini hesaplar.|
|unionMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Bir dizi kümenin birleşimini hesaplar.|
|sıkıştırmasını açın|O(N)|O(N)|O(N)|-|-|Çiftlerinin listesini iki liste halinde ayırır.|
|unzip3|O(N)|O(N)|O(N)|-|-|Bir liste Üçlü dizisini üç listeye böler.|
|Pencereli|-|-|O(N)|-|-|Girdi dizisinden çizilen öğeleri içeren kayan pencere ortaya çıkarır bir dizisini döndürür. Her pencere, yeni bir dizi olarak döndürülür.|
|Zip|O(N)|O(N)|O(N)|-|-|Listeye iki koleksiyon çifti birleştirir. İki liste eşit uzunlukta olmalıdır.|
|zip3|O(N)|O(N)|O(N)|-|-|Koleksiyonların bir listesi halinde Üçlü birleştirir. Listeleri eşit uzunlukta olmalıdır.|

## <a name="see-also"></a>Ayrıca bkz.

- [F# Türleri](fsharp-types.md)
- [F# Dili Başvurusu](index.md)
