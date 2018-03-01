---
title: "PLINQ'te Hızlandırmayı Anlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7d94a1fa4c559552a32140fd172c0c62e033f7a8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="understanding-speedup-in-plinq"></a>PLINQ'te Hızlandırmayı Anlama
PLINQ birincil amacı, çok çekirdekli bilgisayarlarda paralel sorgu temsilcileri yürüterek nesneleri sorgularında LINQ yürütme hızlandırmak olmaktır. Kaynak koleksiyondaki her öğe işleme bağımsız duruma sahip olmayan paylaşılan arasında tek tek temsilcileri söz konusu olduğunda PLINQ en iyi şekilde çalışır. Bu tür işlemler LINQ nesneleri ve PLINQ için ortak olan ve genellikle denir "*delightfully paralel*" bunlar kendilerini kolayca üzerinde birden çok iş parçacıklarını zamanlama için ödünç vermek için. Ancak, tüm sorguları tamamen delightfully paralel işlemleri oluşur; Çoğu durumda, bir sorgu, ya da paralel birkaç ölçeklendirin olamaz veya paralel yürütme yavaş bazı işleçleri içerir. Ve tamamen delightfully paralel bile sorgular ile PLINQ gerekir hala veri kaynağı bölüm ve iş parçacığı üzerinde çalışması zamanlamak ve sorgu tamamlandığında genellikle birleştirme sonuçları. Bu işlemler paralelleştirme hesaplama maliyetine ekleyin; paralelleştirme ekleme, bu maliyetlerini adlı *yükünü*. PLINQ sorgusunda en iyi performansı elde etmek için delightfully paralel bölümleri en üst düzeye çıkarmak ve ek yükü gerektiren bölümleri en aza indirmek için belirtilir. Bu makale, hala doğru sonuçlar verir sırasında olabildiğince etkili PLINQ sorguları yazmanıza yardımcı olacak bilgiler sağlar.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>PLINQ sorgu performansını etkileyen faktörler  
 Aşağıdaki bölümlerde listelenmiştir bazı en önemli faktörlerin etkisi paralel sorgu performans. Tüm durumlarda sorgu performansı tahmin etmek yeterli değil, kendilerini tarafından genel deyimleri bunlar. Her zaman olduğu gibi bir dizi temsilcisi yapılandırmaları ve yükleri ile olan bilgisayarlarda belirli sorgu gerçek performansını ölçmek önemlidir.  
  
1.  Genel İş hesaplama maliyeti.  
  
     Speedup elde etmek için bir PLINQ sorgusu yeterli delightfully paralel iş yükünü dengelemek için olması gerekir. İş kaynak koleksiyondaki öğe sayısı ile çarpılır her temsilci hesaplama maliyeti olarak ifade edilebilir. Bir işlem, daha pkı'ya paralel birkaç ölçeklendirin varsayarak, pahalıdır, büyük fırsat speedup için. Örneğin, bir işlev yürütmek için bir milisaniyelik alırsa, paralel sorgu ancak farklı bir bilgisayarda dört çekirdek ile 1000'den öğeleri bu işlemi gerçekleştirmek için bir saniye sürer sıralı bir sorgu yalnızca 250 milisaniye alabilir. 750 milisaniye speedup verir. Her öğe için yürütmek bir saniye işlevi gerekli olursa speedup 750 saniye olacaktır. Temsilci çok pahalı ise, PLINQ öğeleriyle yalnızca birkaç kaynak koleksiyondaki önemli speedup sunabilir. Buna karşılık, Önemsiz temsilciler küçük kaynak koleksiyonlarla genellikle PLINQ için iyi bir aday değildir.  
  
     Aşağıdaki örnekte, queryA büyük olasılıkla bir iyi Select işlevi çok fazla iş içerdiğini varsayarak PLINQ adaydır. queryB iyi bir aday paralelleştirme yükü çoğu veya tümü speedup uzaklığı ve Select deyiminde yeterli iş olmadığından büyük olasılıkla değil.  
  
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
  
2.  (Paralellik derecesini) sisteminde mantıksal çekirdeklerinin sayısı.  
  
     Bu noktadan önceki bölüme belirgin bir corollary, iş daha fazla eşzamanlı iş parçacıkları arasında bölünebilir çünkü delightfully paralel sorgular makinelerde daha fazla çekirdeğiyle daha hızlı çalışır. Speedup genel miktarını sorgunun genel iş yüzdesini paralelleştirilebilir olduğuna bağlıdır. Ancak, tüm sorguları iki kez olarak çalışacağını varsayın değil hızlı bir bilgisayarda sekiz çekirdeği dört çekirdek bilgisayar olarak. En iyi performans için sorgular ayarlama, çeşitli sayıda çekirdek olan bilgisayarlarda gerçek sonuçları ölçmek önemlidir. Bu noktaya #1 işaret edecek şekilde ilişkilidir: büyük veri kümeleri, daha fazla bilgi işlem kaynakları yararlanmak için gereklidir.  
  
3.  Sayısı ve işlemleri tür.  
  
     PLINQ AsOrdered işleci kaynak sıradaki öğelerin sırasını korumak için gerekli olduğu durumlar için sağlar. Sıralama ile ilişkili bir maliyeti yoktur, ancak bu maliyet genellikle düşüktür. GroupBy ve birleştirme işlemlerinin benzer şekilde zahmetine. Herhangi bir sırada kaynak koleksiyondaki öğelerin işlemek ve yükleyebileceğinizden hazır olduğunuzda İleri işleci bunları geçirmek için izin verildiğinde PLINQ en iyi şekilde çalışır. Daha fazla bilgi için bkz: [plınq'te sıra koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4.  Sorgu yürütme formu.  
  
     Bir sorgunun sonuçlarını ToArray veya ToList çağırarak depoluyorsanız tüm paralel iş parçacıklarını sonuçlarından tek veri yapısına birleştirilmesi gerekir. Bu kaçınılmaz hesaplama maliyet içerir. (Her biri için Visual Basic) foreach döngüsü kullanarak sonuçları yinelemek varsa, benzer şekilde, çalışan iş parçacığı sonuçlarından Numaralandırıcı iş parçacığı serileştirilmesi gerekir. Ancak yalnızca her bir iş parçacığı sonucundan temel bazı eylemleri gerçekleştirmek istiyorsanız, bu iş üzerinde birden çok iş parçacığı gerçekleştirmek için ForAll yöntemi kullanabilirsiniz.  
  
5.  Birleştirme seçeneklerini türü.  
  
     PLINQ çıktısını arabelleğe ve bunlar üretilen gibi tüm sonuç kümesi, veya başka akış tek tek sonuçları üretilen sonra öbekleri veya tümünü bir defada onu üretmek için yapılandırılabilir. Eski azalmasına genel yürütme süresi ve ikinci sonuçları verdiğini öğeler arasında azalmasına gecikme sonucudur.  Birleştirme seçeneklerini her zaman büyük bir etkisi genel sorgu performansı üzerinde değil olsa da, ne kadar kullanıcı kontrol çünkü bunlar algılanan performansı etkileyebilir sonuçları görmek için beklemeniz gerekir. Daha fazla bilgi için bkz: [plınq'te Birleştirme Seçenekleri](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6.  Bölümleme türü.  
  
     Bazı durumlarda, bir PLINQ sorgusu bir dizine kaynak koleksiyonu üzerinden bir dengesiz iş yükü neden olabilir. Bu durumda, özel bir bölümleyici oluşturarak sorgu performansını artırmak olabilir. Daha fazla bilgi için bkz: [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>PLINQ sıralı modu zaman seçer  
 PLINQ sorgu sırayla çalışır gibi en az olarak hızlı bir sorguyu yürütmek her zaman deneyecek. PLINQ ne pkı'ya aramaz rağmen pahalı kullanıcı temsilcileri veya ne kadar büyük giriş kaynağı olduğundan, "şekiller." için belirli sorgu arayın Özellikle, sorgu işleçleri veya genel olarak daha yavaş paralel modunda yürütülmek bir sorgu neden işleçleri birleşimleri arar. Tür şekilleri bulduğunda, varsayılan olarak PLINQ sıralı moduna geri döner.  
  
 Ancak, belirli bir sorgu performansını ölçmek sonra gerçekte daha hızlı paralel modunda çalıştığını belirlemek. Bu gibi durumlarda kullandığınız <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> aracılığıyla bayrak <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> sorguyu paralel hale PLINQ istemek üzere yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: PLINQ'te yürütme modunu belirtme](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Aşağıdaki listede varsayılan olarak PLINQ sıralı modunda yürütülür sorgu şekilleri açıklanmaktadır:  
  
-   Bir Select içeren sorgular dizine nerede, dizinli SelectMany veya kaldırılan veya özgün dizinlerini düzenlenmeyecek bir sıralama veya filtreleme işleç sonra ElementAt yan tümcesi.  
  
-   SkipWhile işleci bir Al ' TakeWhile, Atla içeren ve burada dizinlerini kaynak sıradaki özgün sırayla değil sorgular.  
  
-   ZIP veya SequenceEquals, veri kaynaklarından biri başlangıçta sıralı bir dizine sahip ve başka bir veri kaynağını dizine sürece içeren sorgular (yani bir dizi veya IList(T)).  
  
-   Concat, dizine veri kaynaklarına uygulanır sürece içeren sorgular.  
  
-   Bir dizine veri kaynağına uygulanan sürece içeren sorgular ters.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
