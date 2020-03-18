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
ms.openlocfilehash: 07b5027d560a4caccc6c0a516c3f70c11df6be83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139912"
---
# <a name="understanding-speedup-in-plinq"></a>PLINQ'te Hızlandırmayı Anlama
PLINQ'nin birincil amacı, çok çekirdekli bilgisayarlarda sorgu temsilcilerini paralel olarak yürüterek LINQ to Objects sorgularının yürütülmesini hızlandırmaktır. PLINQ, bir kaynak koleksiyonundaki her öğenin işlenmesi bağımsız olduğunda ve tek tek temsilciler arasında paylaşılan bir durum söz konusu olmadığında en iyi performansı gösterir. Bu tür işlemler Linq to Objects ve PLINQ'da yaygındır ve genellikle "*nefis paralel*" olarak adlandırılır, çünkü birden çok iş parçacığı üzerinde zamanlamaya kolayca ödünç verirler. Ancak, tüm sorgular tamamen nefis paralel işlemlerden oluşmaz; çoğu durumda, bir sorgu paralelleştirileemeyen veya paralel yürütmeyi yavaşlatan bazı işleçler içerir. Ve tamamen nefis paralel sorguları bile, PLINQ hala veri kaynağı bölüm ve iş parçacıkları üzerinde çalışma zamanlama ve genellikle sorgu tamamlandığında sonuçları birleştirmek gerekir. Tüm bu işlemler paralelleştirmenin hesaplama maliyetine eklenir; paralelleştirme eklemenin bu *maliyetlerine genel gider*denir. PLINQ sorgusunda optimum performans elde etmek için amaç, nefis paralel olan parçaları en üst düzeye çıkarmak ve ek yükü gerektiren parçaları en aza indirmektir. Bu makalede, hala doğru sonuçlar verirken mümkün olduğunca verimli PLINQ sorguları yazmanıza yardımcı olacak bilgiler sağlar.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>PLINQ Sorgu Performansını Etkileyen Faktörler  
 Aşağıdaki bölümlerde paralel sorgu performansını etkileyen en önemli etkenlerden bazıları listelemektedir. Bunlar, tüm durumlarda sorgu performansını tahmin etmek için tek başlarına yeterli olmayan genel ifadelerdir. Her zaman olduğu gibi, temsili yapılandırmaları ve yükleri bir dizi bilgisayarlarda belirli sorguların gerçek performansını ölçmek önemlidir.  
  
1. Genel çalışmanın hesaplama maliyeti.  
  
     Hız elde etmek için, bir PLINQ sorgusu nun genel yükü dengelemek için yeterli nefis paralel çalışma olması gerekir. Çalışma, her temsilcinin hesaplama maliyeti, kaynak koleksiyondaki öğe sayısıyla çarpılırken ifade edilebilir. Bir işlemin paralelleştirilebildiği, hesaplama olarak ne kadar pahalı olursa, hızlandırma fırsatı da o kadar büyük olur. Örneğin, bir işlevin yürütülmesi bir milisaniye sürerse, 1000 öğenin üzerindeki sıralı bir sorgunun bu işlemi gerçekleştirmesi bir saniye sürerken, dört çekirdekli bir bilgisayardaki paralel sorgu yalnızca 250 milisaniye sürebilir. Bu, 750 milisaniyelik bir hız verir. İşlevher öğe için çalıştırmak için bir saniye gerekiyorsa, o zaman hız 750 saniye olacaktır. Temsilci çok pahalıysa, PLINQ kaynak koleksiyonunda yalnızca birkaç öğeyle önemli bir hız sağlayabilir. Tersine, önemsiz delegeler ile küçük kaynak koleksiyonları genellikle PLINQ için iyi adaylar değildir.  
  
     Aşağıdaki örnekte, queryA muhtemelen PLINQ için iyi bir adaydır ve Select işlevinin çok fazla iş içerdiğini varsayarak. queryB, Select deyiminde yeterli çalışma olmadığından ve paralelleştirmenin yükü hızın çoğunu veya tamamını dengeleyeceği için büyük olasılıkla iyi bir aday değildir.  
  
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
  
     Bu nokta önceki bölüme bariz bir corollary, iş daha eşzamanlı iş parçacıkları arasında bölünebilir, çünkü nefis paralel daha çekirdekli makinelerde daha hızlı çalıştırmak sorguları. Toplam hız lanma miktarı, sorgunun genel çalışmasının yüzde kaçının paralelleştirilebilir olduğuna bağlıdır. Ancak, tüm sorguların dört çekirdekli bir bilgisayardan sekiz çekirdekli bilgisayarda iki kat daha hızlı çalışacağını düşünmeyin. En iyi performans için sorguları alarken, çeşitli sayıda çekirdek içeren bilgisayarlarda gerçek sonuçları ölçmek önemlidir. Bu nokta #1 noktasıile ilgilidir: daha büyük veri kümelerinin daha büyük bilgi işlem kaynaklarından yararlanması gerekir.  
  
3. Operasyonların sayısı ve türü.  
  
     PLINQ, kaynak dizideki öğelerin sırasını korumak için gerekli olan durumlar için AsOrdered işleci sağlar. Sipariş ile ilişkili bir maliyet vardır, ancak bu maliyet genellikle mütevazı. GroupBy ve Join işlemleri de aynı şekilde ek yükü ne durumdadır. PLINQ, kaynak koleksiyonundaki öğeleri herhangi bir sırada işlemesine ve hazır olur olmaz bir sonraki işleceye geçirmesine izin verildiğinde en iyi performansı gösterir. Daha fazla bilgi için [PLINQ'da Sipariş Koruma'ya](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)bakın.  
  
4. Sorgu yürütme biçimi.  
  
     Bir sorgunun sonuçlarını ToArray veya ToList'i arayarak saklıyorsanız, tüm paralel iş parçacıklarının sonuçlarıtek bir veri yapısında birleştirilmelidir. Bu kaçınılmaz bir hesaplama maliyeti içerir. Aynı şekilde, sonuçları foreach (Visual Basic'teki her biri için) döngü kullanarak yinelerseniz, alt iş parçacığının sonuçlarının da sayısaliş iş parçacığına serileştirilmesi gerekir. Ancak, her iş parçacığının sonucuna göre bazı eylem gerçekleştirmek istiyorsanız, birden çok iş parçacığı üzerinde bu işi gerçekleştirmek için ForAll yöntemini kullanabilirsiniz.  
  
5. Birleştirme seçeneklerinin türü.  
  
     PLINQ, çıktısını arabelleğe alacak şekilde yapılandırılabilir ve tüm sonuç kümesi üretildikten sonra parçalar halinde veya tek seferde üretilebilir veya tek tek sonuçları üretildikçe aktarabilir. Eski sonuçlar genel yürütme süresini azaltmış ve ikincisi verim öğeleri arasındaki gecikme süresinin azalmasına neden olur.  Birleştirme seçenekleri her zaman genel sorgu performansı üzerinde önemli bir etkiye sahip olmasa da, kullanıcının sonuçları görmek için ne kadar beklemesi gerektiğini denetlediği için algılanan performansı etkileyebilir. Daha fazla bilgi için [PLINQ'daki Seçenekleri Birleştir'e](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)bakın.  
  
6. Bir tür bölümleme.  
  
     Bazı durumlarda, dizine eklenebilir kaynak koleksiyonu üzerinde plinq sorgusu dengesiz bir iş yükü neden olabilir. Bu durumda, özel bir bölümleyici oluşturarak sorgu performansını artırmak mümkün olabilir. Daha fazla bilgi [için PLINQ ve TPL için Özel Bölümleyiciler'e](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)bakın.  
  
## <a name="when-plinq-chooses-sequential-mode"></a>PLINQ Sıralı Modu Seçtiğinde  
 PLINQ her zaman sorgunun sırayla çalıştırılacaya kadar en az bir sorguyu yürütmeyi dener. PLINQ, kullanıcı temsilcilerinin hesaplama açısından ne kadar pahalı olduğuna veya giriş kaynağının ne kadar büyük olduğuna bakmasa da, belirli sorgu "şekilleri" arar. Özellikle, sorgu işleçleri veya genellikle paralel modda daha yavaş yürütmek için bir sorgu neden işleçleri kombinasyonları arar. Bu şekilleri bulduğunda, PLINQ varsayılan olarak sıralı moda geri düşer.  
  
 Ancak, belirli bir sorgunun performansını ölçtükten sonra, gerçekte paralel modda daha hızlı çalıştığını belirleyebilirsiniz. Bu gibi durumlarda, <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> plinq <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> sorguparalelleştirmek için talimat yöntemi ile bayrağı kullanabilirsiniz. Daha fazla bilgi için [bkz: PLINQ'da Yürütme Modunu belirtin.](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 Aşağıdaki liste plinq varsayılan olarak sıralı modda yürütecek sorgu şekilleri açıklanır:  
  
- Özgün endeksleri kaldıran veya yeniden düzenleyen bir sipariş veya filtreleme işlecinden sonra Select, indexdWhere, indexdSelectMany veya ElementAt yan tümcesi içeren sorgular.  
  
- Take, TakeWhile, Skip, SkipWhile işleci ve kaynak dizisindeki endekslerin özgün sırada olmadığı sorgular.  
  
- Veri kaynaklarından biri özgün olarak sıralanmış bir diziye sahip değilse ve diğer veri kaynağı dizinlenebilir (örneğin, bir dizi veya IList(T)) yoksa Zip veya SequenceEquals içeren sorgular.  
  
- Dizine eklenebilir veri kaynaklarına uygulanmadığı sürece Concat içeren sorgular.  
  
- Dizinlenebilir bir veri kaynağına uygulanmadığı sürece Ters içeren sorgular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
