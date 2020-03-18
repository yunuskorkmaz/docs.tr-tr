---
title: Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 5a0abef6de9f932f44fc7e3239b98c3a27846580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711226"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
.NET Framework 4, çok iş parçacığı ekleme ve kaldırma işlemlerini desteklemek için özel olarak tasarlanmış beş yeni toplama türü sunar. İş parçacığı güvenliğini sağlamak için, bu yeni türler çeşitli verimli kilitleme ve kilitsiz eşitleme mekanizmaları kullanır. Eşitleme, bir işlem için ek yükü ekler. Ek yükün miktarı, kullanılan eşitleme türüne, gerçekleştirilen işlemlerin türüne ve koleksiyona aynı anda erişmeye çalışan iş parçacığı sayısı gibi diğer etkenlere bağlıdır.  
  
 Bazı senaryolarda, eşitleme yükü ihmal edilebilir ve çok iş parçacığı türünün önemli ölçüde daha hızlı çalışmasını ve harici bir kilitle korunduğunda iş parçacığı güvenli olmayan eşdeğerinden çok daha iyi ölçeklenmesine olanak tanır. Diğer senaryolarda, ek yükü iş parçacığı güvenli türü gerçekleştirmek ve aynı veya hatta daha yavaş türü harici kilitli, iş parçacığı güvenli olmayan sürümü daha ilgili ölçeklendirmek neden olabilir.  
  
 Aşağıdaki bölümler, okuma ve yazma işlemlerinin etrafında kullanıcı tarafından sağlanan kilit olan iş parçacığı güvenli olmayan eşdeğeri ile iş parçacığı güvenli bir koleksiyonun ne zaman kullanılacağı hakkında genel rehberlik sağlar. Performans birçok etkene bağlı olarak değişebileceğinden, kılavuz belirli değildir ve her koşulda mutlaka geçerli değildir. Performans çok önemliyse, hangi toplama türünü kullanacağımı belirlemenin en iyi yolu temsili bilgisayar yapılandırmalarına ve yüklerine göre performansı ölçmektir. Bu belge aşağıdaki terimleri kullanır:  
  
 *Saf üretici-tüketici senaryosu*  
 Verilen herhangi bir iş parçacığı öğeleri ekleyerek veya kaldırıyor, ancak her ikisi de değil.  
  
 *Karışık üretici-tüketici senaryosu*  
 Verilen herhangi bir iş parçacığı hem ekleme ve öğeleri kaldırma.  
  
 *Speedup*  
 Aynı senaryoda başka bir türe göre daha hızlı algoritmik performans.  
  
 *Ölçeklenebilir -lik*  
 Bilgisayardaki çekirdek sayısıyla orantılı performans artışı. Ölçeklendirilen bir algoritma sekiz çekirdeküzerinde iki çekirdekten daha hızlı çalışır.  
  
## <a name="concurrentqueuet-vs-queuet"></a>Eşzamanlı Sıra(T) ile Sıra(T)  
 Saf üretici-tüketici senaryolarında, her öğe için işlem süresi çok küçük <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> (birkaç talimatlar), daha <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sonra harici bir kilit olan bir üzerinde mütevazı performans yararları sunabilir. Bu senaryoda, <xref:System.Collections.Concurrent.ConcurrentQueue%601> özel bir iş parçacığı sıraya girdiğinde ve özel bir iş parçacığı sıraya eklendiğinde en iyi performansı gösterir. Bu kuralı uygulamazsanız, <xref:System.Collections.Generic.Queue%601> birden çok çeki <xref:System.Collections.Concurrent.ConcurrentQueue%601> olan bilgisayarlarda biraz daha hızlı performans gösterebilir.  
  
 İşlem süresi 500 FLOP (kayan nokta işlemleri) veya daha fazla olduğunda, iki <xref:System.Collections.Concurrent.ConcurrentQueue%601>iş parçacığı kuralı , daha sonra çok iyi ölçeklenebilirlik vardır geçerli değildir. <xref:System.Collections.Generic.Queue%601>bu senaryoda iyi ölçeklendirmeyapmaz.  
  
 Karışık üretici-tüketici senaryolarında, işlem süresi çok küçük <xref:System.Collections.Generic.Queue%601> olduğunda, harici kilit ölçeklere sahip olan bir ölçekdaha <xref:System.Collections.Concurrent.ConcurrentQueue%601> vardır. Ancak, işlem süresi 500 FLOP veya daha <xref:System.Collections.Concurrent.ConcurrentQueue%601> fazla olduğunda, o zaman ölçekler daha iyi.  
  
## <a name="concurrentstack-vs-stack"></a>EşzamanlıStack vs Stack  
 Saf üretici-tüketici senaryolarında, işleme süresi çok <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> küçük <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> olduğunda, o zaman ve harici bir kilit muhtemelen bir özel itme iş parçacığı ve özel bir haşhaş iplik ile yaklaşık aynı gerçekleştirecektir. Ancak, iş parçacığı sayısı arttıkça, her iki tür de <xref:System.Collections.Generic.Stack%601> artan çekişme <xref:System.Collections.Concurrent.ConcurrentStack%601>nedeniyle yavaşlar ve .'den daha iyi performans gösterebilir. İşlem süresi 500 FLOP veya daha fazla olduğunda, her iki tür de yaklaşık aynı hızda ölçeklenir.  
  
 Karışık üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentStack%601> hem küçük hem de büyük iş yükleri için daha hızlıdır.  
  
 Ve kullanımı <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> büyük <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> ölçüde erişim sürelerini hızlandırabilir.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>EşzamanlıSözlük vs Sözlük  
 Genel olarak, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> anahtarları veya değerleri aynı anda birden çok iş parçacığından eklediğiniz ve güncellediğiniz herhangi bir senaryoda kullanın. Sık sık güncelleştirmeler ve nispeten az <xref:System.Collections.Concurrent.ConcurrentDictionary%602> okuma içeren senaryolarda, genellikle mütevazı faydalar sunar. Çok okuma ve çok güncelleştirmeiçeren senaryolarda, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> genellikle herhangi bir sayıda çekirdek olan bilgisayarlarda önemli ölçüde daha hızlıdır.  
  
 Sık güncelleştirmeler içeren senaryolarda, eşzamanlılık derecesini artırabilir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ve daha fazla çekirdek olan bilgisayarlarda performansın artıp artmadığını görmek için ölçebilirsiniz. Eşzamanlılık düzeyini değiştirirseniz, genel işlemlerden mümkün olduğunca kaçının.  
  
 Yalnızca anahtar veya değerleri okuyorsanız, sözlük herhangi <xref:System.Collections.Generic.Dictionary%602> bir iş parçacığı tarafından değiştirilmiyorsa eşitleme gerekmediği için daha hızlıdır.  
  
## <a name="concurrentbag"></a>Concurrentbag  
 Saf üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> büyük olasılıkla diğer eşzamanlı toplama türlerine göre daha yavaş gerçekleştirecektir.  
  
 Karışık üretici-tüketici senaryolarında, <xref:System.Collections.Concurrent.ConcurrentBag%601> genellikle hem büyük hem de küçük iş yükleri için diğer eşzamanlı toplama türünden çok daha hızlı ve daha ölçeklenebilir.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Sınırlama ve engelleme semantik gerektiğinde, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> büyük olasılıkla herhangi bir özel uygulama daha hızlı gerçekleştirecektir. Ayrıca zengin iptal, numaralandırma ve özel durum işleme destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş Parçacığı Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
- [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
