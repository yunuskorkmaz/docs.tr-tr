---
title: F# Koleksiyon Türleri
description: "F # koleksiyon türleri ve bunlar .NET Framework'teki koleksiyonu türlerinden farklılıklar hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: a94dc300d984ca31baf1eb7d1073e23b51ebd030
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="f-collection-types"></a>F# Koleksiyon Türleri

Bu konuda inceleyerek, belirli bir gereksinimi hangi F # koleksiyon türü en iyi uyan belirleyebilirsiniz. Bu koleksiyon türleri de gibi .NET Framework koleksiyon türlerinde farklı `System.Collections.Generic` ad alanı, F # koleksiyon türleri nesne yönelimli bir perspektif yerine işlevsel programlama perspektif tasarlanmış olmasıdır. Daha açık belirtmek gerekirse, yalnızca dizi koleksiyon değişebilir öğeleri içeriyor. Bu nedenle, bir koleksiyon değiştirdiğinizde, özgün koleksiyonunu değiştirilmesine yerine değiştirilmiş koleksiyon öğesinin bir örneğini oluşturur.

Koleksiyon türleri de nesneleri depolandığı veri yapısı türünde farklılık gösterir. Karma tabloları, bağlı listeler ve dizi gibi veri yapılarını farklı performans özellikleri ve kullanılabilir işlemleri farklı bir kümesi vardır.


## <a name="f-collection-types"></a>F# Koleksiyon Türleri
Aşağıdaki tabloda, F # koleksiyon türleri gösterilmektedir.



|Tür|Açıklama|İlgili bağlantılar|
|----|-----------|-------------|
|[Liste](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Bir sıralı, sabit dizi öğeleri aynı türde. Bağlantılı bir liste olarak uygulanır.|[Listeler](lists.md)<br /><br />[List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Dizi](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Tümü aynı türde ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı, değişebilir bir koleksiyonu.|[Diziler](arrays.md)<br /><br />[Dizi Modülü](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2D Modülü](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3D Modülü](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[Seq](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Bir türdeki tüm öğeleri mantıksal bir dizi. Veri koleksiyonunu sıralı büyük, varsa ancak mutlaka tüm öğeleri kullanılacak beklemeyen sıraları özellikle yararlı olur. Tek tek sırası öğeleri yalnızca olarak hesaplanan bir sıralı listesini daha iyi gerçekleştirebilirsiniz değilse şekilde tüm öğeleri kullanılır gerekli. Sıraları temsil ettiği `seq<'T>` türü olan bir diğer ad için `IEnumerable<T>`. Bu nedenle, uygulayan bir .NET Framework türü `System.Collections.Generic.IEnumerable<'T>` bir dizi olarak kullanılabilir.|[Diziler](sequences.md)<br /><br />[Seq Modülü](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[eşleme](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Öğe değişmez bir sözlük. Öğeler anahtar ile erişilir.|[Map Modülü](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[ayarlama](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Karşılaştırma olduğu F # Yapısal karşılaştırma işlevi, büyük olasılıkla uygulamaları kullanan ikili ağaçları temelinde bir değişmez kümesi `System.IComparable` anahtar değerleri arabirimde.|[Set Modülü](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tablo işlevleri
Bu bölümde, F # koleksiyon türleri üzerinde kullanılabilir işlevlerini karşılaştırılmaktadır. Burada N ilk koleksiyon boyutunu ve M ikinci koleksiyon varsa boyutudur işlevi hesaplama karmaşıklığını verilir. Bir tire (-) gösteren koleksiyonda bu işlev kullanılamıyor. Dizileri gevşek değerlendirildiği için hemen döndürdüğünden hala numaralandırıldığı zaman sırası performansını etkiler ancak bir işlev Seq.distinct gibi O(1) olabilir.



|İşlev|Dizi|List|Sırası|eşleme|ayarlama|Açıklama|
|--------|-----|----|--------|---|---|-----------|
|ekleme|O(M)|O(N)|O(N)|-|-|İlk koleksiyonun ikinci koleksiyon öğeleri tarafından takip öğelerini içeren yeni bir koleksiyon döndürür.|
|add|-|-|-|O (günlük N)|O (günlük N)|Yeni bir koleksiyon eklenen öğeyi döndürür.|
|Ortalama|O(N)|O(N)|O(N)|-|-|Koleksiyondaki öğelerin ortalamasını döndürür.|
|averageBy|O(N)|O(N)|O(N)|-|-|Her öğeye uygulanan sağlanan işlev sonuçlarını ortalamasını döndürür.|
|blit|O(N)|-|-|-|-|Bir dizi bölümüne kopyalar.|
|önbellek|-|-|O(N)|-|-|Hesaplar ve bir dizi öğelerini depolar.|
|atama|-|-|O(N)|-|-|Öğelerini belirtilen türe dönüştürür.|
|seçin|O(N)|O(N)|O(N)|-|-|Verilen işlevi uygular `f` her öğeye `x` listesi. İşlevin döndüğü her öğe için sonuçları içeren listesini döndürür `Some(f(x))`.|
|TOPLA|O(N)|O(N)|O(N)|-|-|Verilen işlevi koleksiyonun her öğesine uygular, tüm sonuçları art arda ekler ve birleşik listesini döndürür.|
|compareWith|-|-|O(N)|-|-|Öğe belirtilen karşılaştırma işlevini kullanarak iki sıraları karşılaştırır.|
|concat|O(N)|O(N)|O(N)|-|-|Verilen numaralandırması-in-numaralandırmalar tek bir birleştirilmiş numaralandırma olarak birleştirir.|
|içerir|-|-|-|-|O (günlük N)|Belirtilen öğe kümesi içeriyorsa, true döndürür.|
|containsKey|-|-|-|O (günlük N)|-|Bir öğenin bir harita etki alanında olup olmadığını sınar.|
|count|-|-|-|-|O(N)|Kümedeki öğelerin sayısını döndürür.|
|countBy|-|-|O(N)|-|-|Her bir dizi öğesine bir anahtar üretme işlevini uygular ve benzersiz anahtarlar ve bunların özgün dizideki yineleme sayısı verir bir dizi döndürür.|
|copy|O(N)|-|O(N)|-|-|Koleksiyon kopyalar.|
|oluşturma|O(N)|-|-|-|-|Tüm başlangıçta belirtilen değere eşit olan tüm öğeleri dizisi oluşturur.|
|gecikme|-|-|O(1)|-|-|Yerleşik bir dizi bir dizi verilen gecikmeli belirtiminden döndürür.|
|difference|-|-|-|-|O (M &#42; günlük N)|İlk kümeden kaldırılmış ikinci kümenin öğeleri ile yeni bir küme döndürür.|
|Farklı|||O(1)&AMP;#42;|||Genel karma ve eşitlik karşılaştırmaları girdileri göre yinelenen girdi içermeyen bir dizi döndürür. Bir öğe sırasını birden çok kez oluşursa sonraki oluşumlar çıkarılır.|
|distinctBy|||O(1)&AMP;#42;|||Verilen anahtar üretme işlevi döndürür anahtarlar genel karma ve eşitlik karşılaştırmaları göre yinelenen girdi içermeyen bir dizi döndürür. Bir öğe sırasını birden çok kez oluşursa sonraki oluşumlar çıkarılır.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Boş bir koleksiyon oluşturur.|
|var|O(N)|O(N)|O(N)|O (günlük N)|O (günlük N)|Belirtilen koşulun dizisi herhangi bir öğe karşılayıp karşılamadığını sınar.|
|exists2|O(Min(N,M))|-|O(Min(N,M))|||Belirtilen koşulun giriş dizilerini karşılık gelen öğelerinin herhangi bir çifti karşılayıp karşılamadığını sınar.|
|fill|O(N)|||||Dizideki öğeler çeşitli verilen değere ayarlar.|
|filtre|O(N)|O(N)|O(N)|O(N)|O(N)|Yalnızca belirtilen koşulun döndüğü koleksiyon öğelerini içeren yeni bir koleksiyon döndürür `true`.|
|find|O(N)|O(N)|O(N)|O (günlük N)|-|Verilen işlevin döndüğü ilk öğeyi döndürür `true`. Döndürür `System.Collections.Generic.KeyNotFoundException` böyle bir öğe varsa.|
|findIndex|O(N)|O(N)|O(N)|-|-|Verilen karşılaştırma belirtimini dizideki ilk öğenin dizinini döndürür. Başlatır `System.Collections.Generic.KeyNotFoundException` herhangi bir öğe koşulu uymazsa.|
|findKey|-|-|-|O (günlük N)|-|Koleksiyondaki her eşleme üzerinde işlevi değerlendirir ve işlevin döndüğü ilk eşleme anahtarını döner `true`. Böyle bir öğe varsa, bu işlev başlatır `System.Collections.Generic.KeyNotFoundException`.|
|fold|O(N)|O(N)|O(N)|O(N)|O(N)|Her öğesine accumulator bağımsız değişken hesaplama iş parçacığı koleksiyonunun işlevi uygular. Giriş işlevi f ve öğeleri i0... iN varsa, bu işlevi (... f hesaplar (f s i0)...) .|
|fold2|O(N)|O(N)|-|-|-|Bir işlev accumulator bağımsız değişken hesaplama iş parçacığı iki koleksiyonların karşılık gelen öğelere uygulanır. Koleksiyonların boyutunun aynı olması gerekir. Giriş işlevi f ve öğeleri i0... iN ve j0... jN, bu işlevi (... f hesaplar (f s i0 j0)...) İçinde jN.|
|foldBack|O(N)|O(N)|-|O(N)|O(N)|Her öğesine accumulator bağımsız değişken hesaplama iş parçacığı koleksiyonunun işlevi uygular. Giriş işlevi f ve öğeleri i0... iN varsa, bu işlev f i0 hesaplar (... (f s)).|
|foldBack2|O(N)|O(N)|-|-|-|Bir işlev accumulator bağımsız değişken hesaplama iş parçacığı iki koleksiyonların karşılık gelen öğelere uygulanır. Koleksiyonların boyutunun aynı olması gerekir. Giriş işlevi f ve öğeleri i0... iN ve j0... jN, bu işlev f i0 j0 hesaplar (... (f jN s)).|
|forall|O(N)|O(N)|O(N)|O(N)|O(N)|Tüm koleksiyon öğelerini belirtilen koşulun karşılamak olup olmadığını sınar.|
|forall2|O(N)|O(N)|O(N)|-|-|Tüm ilgili koleksiyonun öğelerini belirtilen koşulun Eşli karşılamak olup olmadığını sınar.|
|Get / n.|O(1)|O(N)|O(N)|-|-|Bir öğenin dizinini verilen koleksiyonundan döndürür.|
|HEAD|-|O(1)|O(1)|-|-|Koleksiyon ilk öğesi döndürür.|
|Init|O(N)|O(N)|O(1)|-|-|Boyutu ve öğeleri hesaplamak için oluşturucu işlevi verilen bir koleksiyon oluşturur.|
|initInfinite|-|-|O(1)|-|-|Bir sıra oluşturur, yinelendiğinde verilen işlevi çağırarak art arda öğeleri döndürür.|
|INTERSECT|-|-|-|-|O (günlük N &#42; günlük M)|İki kümenin kesişimini hesaplar.|
|intersectMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Bir dizi kümenin kesişimini hesaplar. Dizi boş olmamalıdır.|
|IsEmpty|O(1)|O(1)|O(1)|O(1)|-|Döndürür `true` koleksiyonu boş ise.|
|isProperSubset|-|-|-|-|O (M &#42; günlük N)|Döndürür `true` ilk kümenin tüm öğeleri ikinci kümesinde yer alan ve en az bir öğe ikinci kümenin ilk kümesinde değil.|
|isProperSuperset|-|-|-|-|O (M &#42; günlük N)|Döndürür `true` ikinci kümenin tüm öğeleri ilk kümesinde yer alan ve ikinci kümede ilk kümenin en az bir öğe değil.|
|isSubset|-|-|-|-|O (M &#42; günlük N)|Döndürür `true` ilk kümenin tüm öğeleri ikinci kümede ise.|
|isSuperset|-|-|-|-|O (M &#42; günlük N)|Döndürür `true` ikinci kümenin tüm öğeleri ilk kümesinde ise.|
|Iter|O(N)|O(N)|O(N)|O(N)|O(N)|Verilen işlevi koleksiyonun her öğesine uygular.|
|iteri|O(N)|O(N)|O(N)|-|-|Verilen işlevi koleksiyonun her öğesine uygular. İşleve geçirilen tamsayı öğenin dizinini belirtir.|
|iter2|O(N)|O(N)|-|-|-|İki dizilerde dizinlerini eşleşen çizilir öğe çiftlerine verilen işlevi uygular. İşleve geçirilen tamsayı öğelerin dizinini belirtir. İki dizi aynı uzunlukta olmalıdır.|
|iter2|O(N)|O(N)|O(N)|-|-|İki dizilerde dizinlerini eşleşen çizilir öğe çiftlerine verilen işlevi uygular. İki dizi aynı uzunlukta olmalıdır.|
|length|O(1)|O(N)|O(N)|-|-|Koleksiyondaki öğe sayısını döndürür.|
|map|O(N)|O(N)|O(1)|-|-|Öğeleri verilen işlevi dizinin her öğeye uygulayarak sonucu olan bir koleksiyon oluşturur.|
|map2|O(N)|O(N)|O(1)|-|-|Verilen işlevin iki koleksiyon karşılık gelen öğelerine Eşli uygulama sonuçlarını öğeleri olan bir koleksiyon oluşturur. İki giriş dizisi aynı uzunlukta olmalıdır.|
|map3|-|O(N)|-|-|-|Verilen işlevin üç koleksiyonları karşılık gelen öğelerine aynı anda uygulama sonuçlarını öğeleri olan bir koleksiyon oluşturur.|
|MAPI|O(N)|O(N)|O(N)|-|-|Öğeleri verilen işlevi dizinin her öğeye uygulayarak sonucu olan bir dizi oluşturur. İşleve geçirilen tamsayı dizini dönüştürülmekte olan öğenin dizinini gösterir.|
|mapi2|O(N)|O(N)|-|-|-|Öğeleri verilen işlevin iki koleksiyondaki öğelerin dizinini geçirerek ikili karşılık gelen öğelere uygulanan sonucu olan bir koleksiyon oluşturur. İki giriş dizisi aynı uzunlukta olmalıdır.|
|max|O(N)|O(N)|O(N)|-|-|Koleksiyondaki kullanarak karşılaştırıldığında en büyük öğeyi döndürür [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) işleci.|
|maxBy|O(N)|O(N)|O(N)|-|-|Koleksiyondaki kullanarak karşılaştırıldığında en büyük öğeyi döndürür [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) işlevi sonuç üzerinde.|
|maxElement|-|-|-|-|O (günlük N)|Küme için kullanılan en büyük öğeyi sıralama göre kümesindeki döndürür.|
|min|O(N)|O(N)|O(N)|-|-|Kullanarak karşılaştırıldığında koleksiyonunda en az öğeyi döndürür [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) işleci.|
|minBy|O(N)|O(N)|O(N)|-|-|Kullanarak karşılaştırıldığında koleksiyonunda en az öğeyi döndürür [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) işlevi sonuç üzerinde işleci.|
|minElement|-|-|-|-|O (günlük N)|Küme için kullanılan sıralama göre belirlenen en düşük öğesinde döndürür.|
|ofArray|-|O(N)|O(1)|O(N)|O(N)|Verilen dizi öğelerinin aynısını içeren bir koleksiyon oluşturur.|
|ofList|O(N)|-|O(1)|O(N)|O(N)|Verilen liste öğelerinin aynısını içeren bir koleksiyon oluşturur.|
|ofSeq|O(N)|O(N)|-|O(N)|O(N)|Belirli bir dizi öğelerinin aynısını içeren bir koleksiyon oluşturur.|
|Eşli|-|-|O(N)|-|-|Giriş dizisi ve onun önceli öncül yalnızca ikinci öğe döndürülen ilk öğe dışında her öğe bir dizi döndürür.|
|partition|O(N)|O(N)|-|O(N)|O(N)|İki koleksiyon koleksiyonu ayırır. İlk koleksiyonun belirtilen koşulun döndüğü öğeleri içeren `true`, ve ikinci koleksiyon belirtilen koşulun döndüğü öğeleri içeren `false`.|
|permute|O(N)|O(N)|-|-|-|Tüm öğeleri belirtilen sıralamaya göre dizilmiş bir dizi döndürür.|
|çekme|O(N)|O(N)|O(N)|O (günlük N)|-|Verilen işlevin işlevi bazı döndüğü ilk sonucu döndürerek ardışık öğelere uygulanır. İşlev hiçbir zaman bazıları döndürürse `System.Collections.Generic.KeyNotFoundException` tetiklenir.|
|readonly|-|-|O(N)|-|-|Belirli bir dizi nesnesini temsil bir dizi nesnesi oluşturur. Bu işlem bir cast türünü olamaz ve yeniden Bul özgün sırası mutate sağlar. Örneğin, bir dizi verilmişse, döndürülen dizi dizinin öğeleri döndürür, ancak bir dizi döndürülen dizi nesnesine atanamaz.|
|Azaltma|O(N)|O(N)|O(N)|-|-|Her öğesine accumulator bağımsız değişken hesaplama iş parçacığı koleksiyonunun işlevi uygular. Bu işlev ilk iki öğelerine işlevi uygulayarak başlatır ve işlevine üçüncü öğesi vb. yanı sıra bu sonucu geçirir. İşlev son sonucu döndürür.|
|reduceBack|O(N)|O(N)|-|-|-|Her öğesine accumulator bağımsız değişken hesaplama iş parçacığı koleksiyonunun işlevi uygular. Giriş işlevi f ve öğeleri i0... iN varsa, bu işlev f i0 hesaplar (... (f,-1'de)).|
|remove|-|-|-|O (günlük N)|O (günlük N)|Bir öğenin harita etki alanından kaldırır. Öğe yoksa hiçbir özel durum oluşturulur.|
|Çoğaltma|-|O(N)|-|-|-|Verilen değere ayarlanmış her öğesi ile belirtilen uzunluktaki bir liste oluşturur.|
|Rev|O(N)|O(N)|-|-|-|Yeni bir liste öğeleri ters sırada döndürür.|
|Tarama|O(N)|O(N)|O(N)|-|-|Her öğesine accumulator bağımsız değişken hesaplama iş parçacığı koleksiyonunun işlevi uygular. Bu işlem işlevi ikinci bağımsız değişken ve listedeki ilk öğeye için geçerlidir. İşlemi daha sonra bu sonucu ikinci öğe birlikte işleve vb. geçirir. Son olarak, işlemi Ara sonuçların ve son sonucu döndürür.|
|scanBack|O(N)|O(N)|-|-|-|FoldBack işlemi benzer ancak ara ve nihai sonuçları döndürür.|
|singleton|-|-|O(1)|-|O(1)|Yalnızca bir öğe verir bir dizi döndürür.|
|set|O(1)|-|-|-|-|Dizi bir öğe belirtilen değere ayarlar.|
|Atla|-|-|O(N)|-|-|Temel alınan dizi N öğelerini atlar ve kalan öğeleri dizisi üretir bir dizi döndürür.|
|SkipWhile|-|-|O(N)|-|-|Yinelendiğinde temel sıralı öğelerini belirtilen koşul döndürür iken, dizisi döndürür `true` ve kalan öğeleri dizisi üretir.|
|sort|O (N günlüğü N) ortalama<br /><br />O(N^2) en kötü durum|O (N günlüğü N)|O (N günlüğü N)|-|-|Koleksiyon öğesi değeriyle sıralar. Öğeleri kullanarak karşılaştırılır [karşılaştırmak](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|O (N günlüğü N) ortalama<br /><br />O(N^2) en kötü durum|O (N günlüğü N)|O (N günlüğü N)|-|-|Verilen projeksiyon sağlar tuşlarını kullanarak verilen listeyi sıralar. Anahtarları kullanarak karşılaştırılır [karşılaştırmak](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|Sortınplace|O (N günlüğü N) ortalama<br /><br />O(N^2) en kötü durum|-|-|-|-|Dizi öğelerini yerinde diziyi ve verilen karşılaştırma işlevini kullanarak sıralar. Öğeleri kullanarak karşılaştırılır [karşılaştırmak](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy|O (N günlüğü N) ortalama<br /><br />O(N^2) en kötü durum|-|-|-|-|Yerinde diziyi ve verilen projeksiyon anahtarları kullanarak bir dizinin öğeleri sıralar. Öğeleri kullanarak karşılaştırılır [karşılaştırmak](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith|O (N günlüğü N) ortalama<br /><br />O(N^2) en kötü durum|-|-|-|-|Yerinde diziyi ve siparişi olarak verilen karşılaştırma işlevini kullanarak bir dizinin öğeleri sıralar.|
|sortWith|O (N günlüğü N) ortalama<br /><br />O(N^2) en kötü durum|O (N günlüğü N)|-|-|-|Verilen karşılaştırma işlevini sıra gibi kullanarak ve yeni koleksiyonu döndüren bir koleksiyonun öğelerini sıralar.|
|Sub|O(N)|-|-|-|-|Dizin ve uzunluk başlatarak belirtilen verilen alt aralığı içeren bir dizi oluşturur.|
|TOPLA|O(N)|O(N)|O(N)|-|-|Koleksiyondaki öğelerin toplamını döndürür.|
|sumBy|O(N)|O(N)|O(N)|-|-|İşlevi koleksiyonun her öğeye uygulayarak oluşturulan sonuçların toplamını döndürür.|
|Tail|-|O(1)|-|-|-|İlk öğe olmadan listesini döndürür.|
|Al|-|-|O(N)|-|-|Belirtilen bir sayısı kadar sıradaki döndürür.|
|TakeWhile|-|-|O(1)|-|-|Yinelendiğinde temel sıralı sayıları öğelerini belirtilen koşul döndürür iken, dizisi döndürür `true` ve daha fazla öğe döndürür.|
|ToArray|-|O(N)|O(N)|O(N)|O(N)|Bir dizi verilen koleksiyondan oluşturur.|
|ToList|O(N)|-|O(N)|O(N)|O(N)|Belirtilen koleksiyonda bir liste oluşturur.|
|toSeq|O(1)|O(1)|-|O(1)|O(1)|Belirtilen koleksiyonda bir sıra oluşturur.|
|kesme|-|-|O(1)|-|-|Bir dizi, numaralandırıldığı N öğeleri birden fazla zaman döndürür döndürür.|
|tryFind|O(N)|O(N)|O(N)|O (günlük N)|-|Belirli bir koşul karşılayan bir öğe arar.|
|tryFindIndex|O(N)|O(N)|O(N)|-|-|Belirli bir koşul karşılayan ve eşleşen bir öğe dizinini döndürür ilk öğe arar veya `None` böyle bir öğe varsa.|
|tryFindKey|-|-|-|O (günlük N)|-|Verilen karşılaştırma belirtimini ya da döndürür koleksiyondaki ilk eşleme anahtarını döndürür `None` böyle bir öğe varsa.|
|tryPick|O(N)|O(N)|O(N)|O (günlük N)|-|Verilen işlevin işlevin döndüğü ilk sonucu döndürerek ardışık öğelere uygulanır `Some` için bir değer. Böyle bir öğe var olup olmadığını döndürür işlemi `None`.|
|unfold|-|-|O(N)|-|-|Verilen hesaplamayı oluşturur öğelerini içeren bir dizi döndürür.|
|birleşim|-|-|-|-|O (M &#42; günlük N)|İki kümenin birleşimini hesaplar.|
|unionMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Bir dizi kümenin birleşimini hesaplar.|
|sıkıştırmasını açın|O(N)|O(N)|O(N)|-|-|Çiftlerinin listesini iki listeye böler.|
|unzip3|O(N)|O(N)|O(N)|-|-|Üçlü listesini üç listeye böler.|
|Pencereli|-|-|O(N)|-|-|Giriş dizisinden alınan öğeleri içeren kayan pencere veren bir dizi döndürür. Her pencere yeni bir dizi olarak döndürülür.|
|Zip|O(N)|O(N)|O(N)|-|-|Bir liste iki koleksiyonlara çiftleri birleştirir. İki liste eşit uzunlukta olması gerekir.|
|zip3|O(N)|O(N)|O(N)|-|-|Üçlü üç koleksiyonları bir liste halinde birleştirir. Listeler eşit uzunlukta olması gerekir.|

## <a name="see-also"></a>Ayrıca Bkz.
[F# Türleri](fsharp-types.md)

[F# Dili Başvurusu](index.md)

