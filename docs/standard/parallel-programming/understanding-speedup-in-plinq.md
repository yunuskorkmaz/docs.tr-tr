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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26128e5d707d3f331dc2b691f5a5f798bdf84c25
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322998"
---
# <a name="understanding-speedup-in-plinq"></a>PLINQ'te Hızlandırmayı Anlama
PLINQ birincil amacı, çok çekirdekli bilgisayarlarda paralel sorgu temsilcileri yürüterek Plınq sorgularının LINQ yürütülmesini hızlandırmak sağlamaktır. Kaynak koleksiyondaki her öğe işlenmesini bağımsız olarak, paylaşılan durumu olmadan arasında bireysel temsilciler dahil olduğunda PLINQ en iyi şekilde çalışır. Bu işlemler LINQ nesneleri ve PLINQ için ortak olan ve genellikle denir "*delightfully paralel*" çünkü bunlar kendilerini kolayca birden çok iş parçacığında zamanlamaya uygun. Ancak, tüm sorguları tamamen delightfully paralel işlemleri oluşur; Çoğu durumda, bir sorgu, ya da paralelleştirildi olamaz veya paralel yürütme yavaş, bazı işleçler içerir. Ve tamamen delightfully paralel bile sorgular ile PLINQ gerekir yine de veri kaynağının bölüm ve iş parçacıkları üzerinde iş zamanlama ve sorgu tamamlandığında genellikle sonuçları birleştirin. Tüm bu işlemler, paralelleştirme hesaplama maliyetine ekleyin; Bu maliyetler paralelleştirme ekleme adlı *yükü*. PLINQ sorgusunda en iyi performansı elde etmek için delightfully paralel bölümleri en üst düzeye çıkarmak ve getirdiği ek yüke gerek bölümleri en aza indirmek için hedeftir. Bu makalede, mümkün olduğunca etkili doğru sonuçları hala sonuçlanmıyor sırasında PLINQ sorguları yazmanıza yardımcı olacak bilgiler sağlar.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>PLINQ sorgu performansını etkileyen faktörler  
 Aşağıdaki bölümlerde listelenmiştir bazı en önemli olan faktör, paralel sorgu performansı etkileyebilir. Tüm durumlarda sorgu performansını tahmin etmek yeterli değil, kendileri tarafından genel deyimleri şunlardır. Her zaman olduğu gibi bir dizi temsili yapılandırmaları ve yükü ile gerçek bilgisayarlarda belirli sorguların performansını ölçmek önemlidir.  
  
1. Genel İş hesaplama maliyeti.  
  
     Hızlandırmayı elde etmek için yeterli delightfully paralel iş yükünü dengelemek için bir PLINQ sorgusu olmalıdır. İş hesaplama maliyeti kaynak koleksiyondaki öğe sayısını çarpılmasıyla her temsilci olarak ifade edilebilir. Bir işlem, daha fazla hesaplama açısından paralelleştirilebilir varsayarak, pahalıdır, büyük hızlandırmayı fırsat tanır. Örneğin, bir işlevi yürütmek için bir milisaniyeden kısa alırsa, paralel sorgu ise dört çekirdek içeren bir bilgisayarda 1000'den öğeleri bu işlemi gerçekleştirmek için bir saniye sürecek sıralı bir sorgu yalnızca 250 milisaniye alabilir. Bu, bir hızlandırmayı 750 milisaniye olarak verir. Ardından işlev her öğe için bir saniyede gerekirse hızlandırmayı 750 saniye olacaktır. Ardından temsilci çok pahalı ise, PLINQ kaynak koleksiyondaki yalnızca birkaç öğeleri ile önemli hızlandırmayı sağlayabilir. Buna karşılık, küçük kaynak koleksiyonlarla Önemsiz temsilcileri genellikle PLINQ için iyi adaylar değildir.  
  
     Aşağıdaki örnekte, queryA büyük olasılıkla, Select işlevi birçok iş içerdiğini varsayarak, PLINQ için iyi bir aday olan. queryB iyi bir aday paralelleştirme yükü çoğunu veya tümünü hızlandırmayı uzaklığı ve Select deyiminde yeterli iş olmadığından büyük olasılıkla değil.  
  
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
  
2. ' % S'sistemde (çalıştırılır. paralellik derecesini) mantıksal çekirdek sayısı.  
  
     Bu noktaya belirgin bir corollary önceki bölüme, daha fazla eşzamanlı iş parçacıkları arasında iş ayrılabilir çünkü delightfully paralel sorgular makinelerde ile daha fazla çekirdek daha hızlı çalışır. Toplam miktarı hızlandırmayı sorgunun genel iş yüzdesini paralelleştirilebilir olduğuna bağlıdır. Ancak, tüm sorgular kat çalıştırılır varsaymayın dört ana bilgisayarla sekiz çekirdeği bilgisayarında hızlı. Sorgular için en iyi performans ayarlama, çeşitli sayıda çekirdek olan bilgisayarlarda gerçek sonuçlar ölçmek önemlidir. Bu noktaya #1 işaret edecek şekilde ilişkilidir: büyük veri kümeleri, daha büyük bilgi işlem kaynakları yararlanmak için gereklidir.  
  
3. Sayısı ve işlemleri bir tür.  
  
     PLINQ kaynak dizisindeki öğelerin sırasını korumak için gerekli olduğu durumları metodu AsOrdered işleci sağlar. Sıralama ile ilişkilendirilmiş bir maliyet yoktur, ancak bu maliyet genellikle daha düşüktür. GroupBy ve birleştirme işlemlerinin benzer şekilde zahmetine. Herhangi bir sırada kaynak koleksiyondaki öğe işleme ve hazır olduğunda hemen sonra geçirileceğini sonraki işlecine izin verilmediği halde PLINQ en iyi şekilde çalışır. Daha fazla bilgi için [plınq'te sıra koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4. Sorgu yürütme formu.  
  
     ToArray veya ToList çağırarak bir sorgunun sonuçlarını depoluyorsanız tüm paralel iş parçacıkları sonuçlardan tek bir veri yapısına birleştirilmesi gerekir. Bu, bir kaçınılmaz hesaplama maliyetini kapsar. Benzer şekilde, bir (For Each Visual Basic'te) foreach döngüsü kullanarak sonuçları yineleme, çalışan iş parçacıkları sonuçlardan Numaralandırıcı parçacığına serileştirilecek gerekir. Ancak, yalnızca her bir iş parçacığı sonucuna dayalı bazı eylemler gerçekleştirmek istiyorsanız, birden çok iş parçacığı üzerinde bu işi gerçekleştirmek için ForAll yöntemini kullanabilirsiniz.  
  
5. Birleştirme seçeneklerini türü.  
  
     PLINQ çıktısını arabelleğe ve bunlar üretilen gibi sonuç kümesinin tamamı, veya başka stream tek sonuçları üretilen sonra öbekleri veya tümünü tek seferde, üretmek için yapılandırılabilir. Önceki sonuç azalan toplam yürütme süresi ve ikinci sonucunu veriyor öğeler arasında düşük gecikme olur.  Birleştirme seçeneklerini her zaman önemli bir etkiye genel sorgu performansı üzerindeki değil olsa da, bunlar ne bir kullanıcı denetimi çünkü bunlar algılanan performansını etkileyebilir sonuçlarını görmek için beklemeniz gerekir. Daha fazla bilgi için [plınq'te Birleştirme Seçenekleri](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6. Bölümleme türü.  
  
     Bazı durumlarda, dizinlenebilir kaynak koleksiyonu üzerinden bir PLINQ sorgusu bir dengesiz iş yüküne neden olabilir. Bu durumda, özel bir bölümleyici oluşturarak sorgu performansını artırmanın mümkün olabilir. Daha fazla bilgi için [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>PLINQ sıralı modu ne zaman seçer  
 PLINQ sorgusu sıralı olarak çalışır en az kadar hızlı bir sorgu yürütme her zaman dener. PLINQ ne hesaplama açısından aramaz ancak kullanıcı temsilcileri pahalıdır veya nasıl büyük giriş kaynağı olan belirli sorgu "şekiller." arayın Özellikle, sorgu işleçleri veya genellikle bir sorgu paralel modunda daha yavaş çalışmasına neden işleçleri birleşimleri için arar. Tür şekilleri bulduğunda, varsayılan olarak PLINQ sıralı moduna geri döner.  
  
 Ancak, belirli bir sorgu performansını ölçme sonra bunun gerçekten daha hızlı bir şekilde paralel modunda çalıştığından belirlemek. Bu gibi durumlarda kullanabilirsiniz <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> aracılığıyla bayrak <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> PLINQ'nun sorguyu paralelleştirmek için istemek için yöntemi. Daha fazla bilgi için [nasıl yapılır: PLINQ'te yürütme modunu belirtme](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Aşağıdaki listede, varsayılan olarak PLINQ sıralı modunda yürütülür sorgu şekiller açıklanmaktadır:  
  
-   Bir Select içeren sorgular dizini, dizinlenmiş SelectMany veya kaldırıldı veya özgün dizinleri yeniden düzenlenmiş olan bir sıralama veya filtreleme işleci sonra ElementAt yan tümcesi.  
  
-   SkipWhile işleci bir Al ' TakeWhile, Atla içeren ve dizinleri kaynak dizisindeki özgün sırayla olmadığı sorgular.  
  
-   ZIP veya SequenceEquals, veri kaynaklarından biri özgün sıralı bir dizine sahip ve diğer veri kaynağı dizinlenebilir sürece içeren sorgular (yani bir dizi veya IList(T)).  
  
-   Concat, dizinlenebilir veri kaynaklarına uygulanır sürece içeren sorgular.  
  
-   Tersine, bir dizine veri kaynağına uygulanan sürece içeren sorgular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
