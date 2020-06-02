---
title: Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: e2c5d612abb824c93c611514a836c811e6e65efe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288881"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
.NET Framework 4, çok iş parçacıklı ekleme ve kaldırma işlemlerini desteklemek için özel olarak tasarlanan beş yeni koleksiyon türü sunar. İş parçacığı güvenliği sağlamak için, bu yeni türler çeşitli verimli kilitleme ve kilitleme ücretsiz eşitleme mekanizmalarını kullanır. Eşitleme bir işleme ek yük ekler. Ek yük miktarı, kullanılan eşitleme türüne, gerçekleştirilen işlem türüne ve koleksiyona eşzamanlı olarak erişmeye çalışan iş parçacığı sayısı gibi diğer faktörlere bağlıdır.  
  
 Bazı senaryolarda, eşitleme ek yükü göz ardı edilebilir değildir ve çok iş parçacıklı türün bir dış kilit tarafından korunurken iş parçacığı açısından güvenli olmayan eşinden daha iyi bir şekilde ölçeklenebilmesini sağlar. Diğer senaryolarda, ek yük, iş parçacığı güvenli türünün aynı veya daha yavaş bir şekilde, bu tür iş parçacığı güvenli olmayan bir sürümüne göre çalışmasını ve ölçeklendirilmesine neden olabilir.  
  
 Aşağıdaki bölümlerde, iş parçacığı güvenli bir koleksiyonun ne zaman kullanıldığı, okuma ve yazma işlemleri etrafında Kullanıcı tarafından sağlanmış bir kilit olan iş parçacığı güvenli olmayan eşdeğerine karşı genel rehberlik sağlanmaktadır. Performans birçok etkene bağlı olarak farklılık gösterebileceğinden, kılavuz özel değildir ve tüm durumlarda geçerli değildir. Performans çok önemliyse, hangi koleksiyon türünün kullanılacağını belirlemenin en iyi yolu, temsili bilgisayar yapılandırmalarına ve yüklerine göre performansı ölçmaktır. Bu belge aşağıdaki terimleri kullanır:  
  
 *Saf üretici-tüketici senaryosu*  
 Verilen herhangi bir iş parçacığı öğe ekliyor veya kaldırıyor, ancak her ikisine birden değil.  
  
 *Karma üretici-tüketici senaryosu*  
 Verilen herhangi bir iş parçacığı, öğeleri ekleme ve kaldırma.  
  
 *PLINQ 'te hızlandırmayı*  
 Aynı senaryodaki diğer bir türe göre daha hızlı algoritmik performansı.  
  
 *Ölçeklenebilirlik*  
 Performans artışı, bilgisayardaki çekirdek sayısıyla orantılıdır. Ölçeklendirilen bir algoritma, iki çekirdekden daha fazla sekiz çekirdekli daha hızlı gerçekleştirilir.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue (T) ve Queue (T) karşılaştırması  
 Saf üretici-tüketici senaryolarında her öğe için işlem zamanının çok küçük (birkaç yönerge) olduğu durumlarda, <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> bir <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> dış kilidine sahip olan bir üzerinde ila büyüklükteki performans avantajları sunabilir. Bu senaryoda, <xref:System.Collections.Concurrent.ConcurrentQueue%601> ayrılmış bir iş parçacığının kuyruğa alınması ve ayrılmış bir iş parçacığının de de sıraya alınması durumunda en iyi şekilde çalışır. Bu kuralı zorunlu kılmaz, <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> birden fazla çekirdeğe sahip bilgisayarlardan daha hızlı bir şekilde daha hızlı işlem yapabilirsiniz.  
  
 İşlem süresi 500 FLOPS (kayan nokta işlemleri) veya daha fazla olduğunda, iki iş parçacığı kuralı için geçerli değildir <xref:System.Collections.Concurrent.ConcurrentQueue%601> , daha sonra çok iyi ölçeklenebilirlik vardır. <xref:System.Collections.Generic.Queue%601>Bu senaryoda iyi ölçeklenmez.  
  
 Karma üretici-tüketici senaryolarında, işleme süresi çok küçük olduğunda, bir <xref:System.Collections.Generic.Queue%601> dış kilit ölçeği bundan daha iyidir <xref:System.Collections.Concurrent.ConcurrentQueue%601> . Ancak, işleme süresi 500 kat veya daha uzun bir süre içinde olduğunda, <xref:System.Collections.Concurrent.ConcurrentQueue%601> daha sonra ölçeklendirir.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack ile yığın karşılaştırması  
 Saf üretici-tüketici senaryolarında, işlem süresi çok küçük olduğunda <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> ve bir <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> dış kilit varsa, büyük olasılıkla bir ayrılmış gönderme iş parçacığı ve ayrılmış bir kayan iş parçacığı ile aynı şekilde çalışır. Ancak, iş parçacıklarının sayısı arttıkça her iki tür de daha fazla çekişme nedeniyle yavaşlar ve <xref:System.Collections.Generic.Stack%601> bundan daha iyi çalışabilir <xref:System.Collections.Concurrent.ConcurrentStack%601> . İşlem süresi 500 kat veya daha uzun bir süre içinde olduğunda her iki tür de aynı fiyata göre ölçeklendirilir.  
  
 Karma üretici-tüketici senaryolarında <xref:System.Collections.Concurrent.ConcurrentStack%601> hem küçük hem de büyük iş yükleri için daha hızlıdır.  
  
 Ve kullanımı, <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> erişim sürelerini önemli ölçüde hızlandırabilir.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary ve sözlük karşılaştırması  
 Genel olarak, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> birden çok iş parçacığından aynı anda anahtar veya değer eklediğiniz ve güncelleştirdiğiniz herhangi bir senaryoda bir kullanın. Sık sık güncelleştirmeler ve görece birkaç okuma içeren senaryolarda, genellikle daha fazla <xref:System.Collections.Concurrent.ConcurrentDictionary%602> avantaj sunar. Birçok okuma ve birçok güncelleştirme içeren senaryolarda, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> genellikle herhangi bir sayıda çekirdeği olan bilgisayarlarda önemli ölçüde daha hızlıdır.  
  
 Sık sık güncelleştirmeler içeren senaryolarda, içindeki eşzamanlılık derecesini artırabilir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ve daha fazla çekirdeğe sahip bilgisayarlarda performansın artmasının yapılıp yapılmayacağını görmek için ölçebilir. Eşzamanlılık düzeyini değiştirirseniz, genel işlemlerden mümkün olduğunca kaçının.  
  
 Yalnızca anahtar veya değerleri okuyorsanız, <xref:System.Collections.Generic.Dictionary%602> Sözlük hiçbir iş parçacığı tarafından değiştirilmemişse hiçbir eşitleme gerekmediğinden, daha hızlıdır.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 Saf üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> muhtemelen diğer eşzamanlı koleksiyon türlerinden daha yavaş çalışacak.  
  
 Karma üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentBag%601> genellikle büyük ve küçük iş yükleri için diğer eş zamanlı koleksiyon türünden daha hızlı ve daha ölçeklenebilir olur.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Sınırlama ve engelleme semantiği gerektiğinde, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> büyük olasılıkla herhangi bir özel uygulamadan daha hızlı gerçekleşir. Ayrıca zengin iptal, numaralandırma ve özel durum işlemeyi da destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı güvenli Koleksiyonlar](index.md)
- [Paralel programlama](../../parallel-programming/index.md)
