---
title: Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 5a0abef6de9f932f44fc7e3239b98c3a27846580
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711226"
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
 Her öğe için işlem zamanının çok küçük (birkaç yönerge) olduğu saf üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, dış kilidi olan bir <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> üzerinde ila büyüklükteki performans avantajları sağlayabilir. Bu senaryoda, bir adanmış iş parçacığı sıraya alınırken ve ayrılmış bir iş parçacığının de de sıraya alınması durumunda <xref:System.Collections.Concurrent.ConcurrentQueue%601> en iyi şekilde çalışır. Bu kuralı zorunlu kılmaz, <xref:System.Collections.Generic.Queue%601> birden fazla çekirdeğe sahip bilgisayarlarda <xref:System.Collections.Concurrent.ConcurrentQueue%601> biraz daha hızlı bir şekilde çalışabilir.  
  
 İşlem süresi 500 FLOPS (kayan nokta işlemleri) veya daha fazla olduğunda, iki iş parçacığı kuralı <xref:System.Collections.Concurrent.ConcurrentQueue%601>için geçerli değildir ve bu da çok iyi ölçeklenebilirlik sağlar. <xref:System.Collections.Generic.Queue%601> Bu senaryoda iyi ölçeklenmez.  
  
 Karma üretici-tüketici senaryolarında, işleme süresi çok küçükse, dış kilit içeren bir <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> daha iyi ölçeklendirir. Ancak, işleme süresi 500 kat veya daha uzun bir süre içinde olduğunda <xref:System.Collections.Concurrent.ConcurrentQueue%601> daha iyi şekilde ölçeklendirilir.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack ile yığın karşılaştırması  
 Saf üretici-tüketici senaryolarında, işlem süresi çok küçük olduğunda <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> ve dış kilidi olan <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>, büyük olasılıkla bir adanmış iletme iş parçacığı ve ayrılmış bir kayan iş parçacığı ile aynı şekilde gerçekleştirilir. Ancak, iş parçacıklarının sayısı arttıkça, daha fazla çekişme nedeniyle her iki tür de yavaşlar ve <xref:System.Collections.Generic.Stack%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>daha iyi çalışabilir. İşlem süresi 500 kat veya daha uzun bir süre içinde olduğunda her iki tür de aynı fiyata göre ölçeklendirilir.  
  
 Karma üretici-tüketici senaryolarında <xref:System.Collections.Concurrent.ConcurrentStack%601> hem küçük hem de büyük iş yükleri için daha hızlıdır.  
  
 <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> ve <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> kullanımı, erişim sürelerini önemli ölçüde hızlandırabilir.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary ve sözlük karşılaştırması  
 Genel olarak, birden fazla iş parçacığından aynı anda anahtar veya değer eklediğiniz ve güncelleştirdiğiniz herhangi bir senaryoda <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> kullanın. Sık sık güncelleştirmeler ve görece birkaç okuma içeren senaryolarda <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, genellikle daha fazla avantaj sunar. Birçok okuma ve birçok güncelleştirme içeren senaryolarda <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, genellikle çok sayıda çekirdeği olan bilgisayarlarda önemli ölçüde daha hızlıdır.  
  
 Sık güncelleştirmeleri içeren senaryolarda, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> eşzamanlılık derecesini artırabilir ve daha fazla çekirdeğe sahip bilgisayarlarda performansın yükselmediğini görmek için ölçebilir. Eşzamanlılık düzeyini değiştirirseniz, genel işlemlerden mümkün olduğunca kaçının.  
  
 Yalnızca anahtar veya değerleri okuyorsanız, sözlük hiçbir iş parçacığı tarafından değiştirilmemişse hiçbir eşitleme gerekmediği için <xref:System.Collections.Generic.Dictionary%602> daha hızlıdır.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 Saf üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> muhtemelen diğer eşzamanlı koleksiyon türlerinden daha yavaş çalışır.  
  
 Karma üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentBag%601> hem büyük hem de küçük iş yükleri için diğer eş zamanlı koleksiyon türünden daha hızlı ve daha ölçeklenebilir olur.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Sınırlama ve engelleme semantiğinin gerekli olduğu durumlarda <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>, büyük olasılıkla herhangi bir özel uygulamadan daha hızlı gerçekleştirilir. Ayrıca zengin iptal, numaralandırma ve özel durum işlemeyi da destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
- [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
