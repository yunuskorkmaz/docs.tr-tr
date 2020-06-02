---
title: PLINQ'te Hızlandırmayı Anlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
ms.openlocfilehash: 627f1327a9fe87fc226dfbb40df50ec4855edfb9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284903"
---
# <a name="understanding-speedup-in-plinq"></a>PLINQ'te Hızlandırmayı Anlama
PLıNQ 'in birincil amacı, çok çekirdekli bilgisayarlarda sorgu temsilcilerini paralel olarak yürüterek LINQ to Objects sorgularının yürütülmesini hızlandırmaya yönelik olur. PLıNQ, bir kaynak koleksiyondaki her öğenin işlenmesi bağımsız temsilciler arasında herhangi bir paylaşılan durum olmadan bağımsız olduğunda en iyi şekilde çalışır. Bu gibi işlemler LINQ to Objects ve PLıNQ ' de ortaktır ve genellikle birden çok iş parçacığında zamanlamaya göre kolayca bir şekilde çalıştıkları için "*delightfully Parallel*" olarak adlandırılır. Ancak, tüm sorgular tamamen eş dışı paralel işlemlerden oluşamaz; Çoğu durumda, bir sorgu paralelleştirilmedi veya paralel yürütmeyi yavaşlatabilecek bazı işleçleri içerir. Tamamen de tamamen paralel olan sorgularda, PLıNQ hala veri kaynağını bölümleyip iş parçacıkları üzerinde işi zamanlamaya ve genellikle sorgu tamamlandığında sonuçları birleştirmelidir. Tüm bu işlemler paralelleştirme hesaplama maliyetine ekler; paralel hale getirme ekleme maliyetlerine *ek yük*denir. Bir PLıNQ sorgusunda en iyi performansı elde etmek için, amaç paralel olan parçaları en üst düzeye çıkarmaktır ve ek yük gerektiren parçaları en aza indirmektir. Bu makalede, doğru sonuçları sunarken mümkün olduğunca verimli olan PLıNQ sorgularını yazmanıza yardımcı olacak bilgiler sağlanmaktadır.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>PLıNQ sorgu performansını etkileyen faktörler  
 Aşağıdaki bölümlerde, paralel sorgu performansını etkileyen en önemli faktörlerin bazıları listelenmiştir. Bunlar, her durumda sorgu performansını tahmin etmek için yeterli olmayan genel deyimlerdir. Her zaman olduğu gibi, bilgisayarlardaki belirli sorguların gerçek performansını, bir dizi temsili yapılandırması ve yükleri ile ölçmek önemlidir.  
  
1. Genel çalışmanın hesaplama maliyeti.  
  
     Bir PLıNQ sorgusunun daha hızlı bir şekilde elde edilebilmesi için, ek yükü kaydırarak çok fazla sayıda paralel iş olması gerekir. İş, her temsilcinin hesaplama maliyeti olarak kaynak koleksiyondaki öğelerin sayısıyla çarpılarak ifade edilebilir. Bir işlemin paralelleştirilmesine ne olduğunu varsayarsak, daha fazla hesaplama, daha iyi hale getirilmiş bir fırsattır. Örneğin, bir işlevin yürütülmesi için bir milisaniyelik sürerse 1000 öğeden oluşan sıralı bir sorgu bu işlemi gerçekleştirmek için bir saniye sürer, ancak dört çekirdekli bir bilgisayardaki paralel sorgu yalnızca 250 milisaniyeye sahip olur. Bu, 750 milisaniyeden daha hızlı bir hızlandırın verir. İşlevin her öğe için bir saniyede yürütülmesi gerekiyorsa, bu durumda hızlı bir süre 750 saniye olur. Temsilci çok pahalıdır, PLıNQ, kaynak koleksiyondaki yalnızca birkaç öğeyle önemli bir hızlı işlem sunabilir. Buna karşılık, önemsiz temsilcilerle küçük kaynak koleksiyonları genellikle PLıNQ için iyi adaylardır.  
  
     Aşağıdaki örnekte, select işlevinin çok sayıda iş içerdiği varsayılarak, queryA PLıNQ için iyi bir adaydır. Select ifadesinde yeterli iş olmadığından ve paralelleştirme yükünün en fazla ya da tüm hızlı bir şekilde kaydırılacağı için queryB büyük olasılıkla iyi bir aday değildir.  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
    ```  
  
2. Sistemdeki mantıksal çekirdek sayısı (paralellik derecesi).  
  
     Bu nokta, önceki bölümde yer alan ve daha fazla çekirdeğe sahip makinelerde daha hızlı bir şekilde paralel şekilde çalışan sorgular daha fazla eş zamanlı iş parçacığı arasında ayrılamadığından, daha fazla çekirdeğe sahip olan çok daha açık bir eş olabilir. Toplam hızlı çalışma miktarı, sorgunun genel işinin toplam yüzdesine paralelleştirilebilir. Ancak, tüm sorguların dört çekirdekli bilgisayar olarak sekiz çekirdekli bir bilgisayarda hızlı bir şekilde çalışacağını varsaymayın. En iyi performans için sorguları ayarlamaya çalışırken, gerçek sonuçların çeşitli çekirdekler içeren bilgisayarlarda ölçülmesi önemlidir. Bu nokta #1 nokta ile ilgilidir: daha büyük bilgi işlem kaynaklarından yararlanmak için daha büyük veri kümeleri gereklidir.  
  
3. İşlem sayısı ve türü.  
  
     PLıNQ, kaynak dizideki öğelerin sırasını korumak için gerekli olduğu durumlar için Asorimli işleci sağlar. Sıralamaya ilişkin bir maliyet vardır, ancak bu maliyet genellikle Modest 'dir. GroupBy ve JOIN işlemleri aynı şekilde ek yüke neden olur. PLıNQ, kaynak koleksiyondaki öğeleri herhangi bir sırada işlemeye izin verildiğinde en iyi şekilde çalışır ve bunları bir sonraki işleçle uygun hale gelir. Daha fazla bilgi için bkz. [PLıNQ 'Te sıra koruma](order-preservation-in-plinq.md).  
  
4. Sorgu yürütme biçimi.  
  
     ToArray veya ToList çağırarak bir sorgunun sonuçlarını depoluyorsanız, tüm paralel iş parçacıklarından elde edilen sonuçlar tek veri yapısına birleştirilmelidir. Bu, kaçınılmaz bir hesaplama maliyeti içerir. Benzer şekilde, bir foreach (her biri Visual Basic) döngüsünde sonuçları yinelemek istiyorsanız, çalışan iş parçacıklarının sonuçlarının Numaralandırıcı iş parçacığı üzerinde serileştirilmesi gerekir. Ancak, her iş parçacığının sonucunu temel alan bazı eylemler gerçekleştirmek istiyorsanız, bu işi birden çok iş parçacığı üzerinde gerçekleştirmek için ForAll metodunu kullanabilirsiniz.  
  
5. Birleştirme seçeneklerinin türü.  
  
     PLıNQ, çıktısını arabelleğe almak için yapılandırılabilir ve tüm sonuç kümesi üretildikten sonra tek seferde veya her seferinde bir kez oluşturulur. Daha önce, genel yürütme süresi azalır ve ikinci sonuçlar, diğer bir deyişle, diğer bir deyişle, sonuçlandırılan öğeler arasında  Birleştirme seçenekleri her zaman genel sorgu performansı üzerinde önemli bir etkiye sahip olmasa da, bir kullanıcının sonuçları görmeyi beklemesi gereken süreyi denetlemediğinden, algılanan performansı etkileyebilir. Daha fazla bilgi için bkz. [PLıNQ 'Te birleştirme seçenekleri](merge-options-in-plinq.md).  
  
6. Bölümleme türü.  
  
     Bazı durumlarda, Dizin oluşturamayacak bir kaynak koleksiyonu üzerinde PLıNQ sorgusu, dengesiz bir iş yüküne neden olabilir. Bu gerçekleştiğinde, özel bir bölümleyici oluşturarak sorgu performansını artırabilirsiniz. Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>PLıNQ sıralı modu seçtiğinde  
 PLıNQ, sorgu sırayla çalışır şekilde her zaman bir sorguyu en az hızlı bir şekilde yürütmeye çalışır. PLıNQ, Kullanıcı temsilcilerinin ne kadar pahalı olduğunu veya giriş kaynağının ne kadar büyük olduğunu fark etmez, bazı sorgu "şekillerini" arar. Özellikle, genellikle bir sorgunun paralel modda daha yavaş yürütülmesine neden olan sorgu işleçlerini veya işleç birleşimlerini arar. Böyle bir şekil bulduğunda, PLıNQ varsayılan olarak sıralı moda geri döner.  
  
 Ancak, belirli bir sorgunun performansını ölçdikten sonra, aslında paralel modda daha hızlı çalıştığını belirleyebilirsiniz. Bu gibi durumlarda, <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> sorguyu paralel hale getirmek için PLINQ 'a yönlendirmek üzere yöntemi aracılığıyla bayrağını kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ 'Te yürütme modunu belirtme](how-to-specify-the-execution-mode-in-plinq.md).  
  
 Aşağıdaki listede, PLıNQ 'ın varsayılan olarak sıralı modda yürütüleceği sorgu şekilleri açıklanmaktadır:  
  
- Bir SELECT, Indexed WHERE, Indexed SelectMany veya ElementAt yan tümcesi içeren sorgular, özgün dizinleri kaldırmış veya yeniden düzenlenmiş bir sıralama veya filtreleme işlecinden sonra.  
  
- Al, TakeWhile, Skip, SkipWhile operatörü ve kaynak dizideki dizinlerin özgün sırada olmadığı sorgular.  
  
- ZIP veya SequenceEquals içeren sorgular, veri kaynaklarından biri özgün olarak sıralanmış bir dizine sahip olmadığı ve diğer veri kaynağı dizinlenebilir (yani bir dizi veya IList (T)).  
  
- Dizine eklenebilir veri kaynaklarına uygulanmadığı takdirde Concat içeren sorgular.  
  
- Dizine eklenebilir bir veri kaynağına uygulanmadıysa ters içeren sorgular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
