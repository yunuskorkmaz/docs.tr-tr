---
title: BlockingCollection Genel Bakışı
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 257435516b38d0e4389b7feceba68371bcc8f90e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616558"
---
# <a name="blockingcollection-overview"></a>BlockingCollection Genel Bakışı
<xref:System.Collections.Concurrent.BlockingCollection%601> Aşağıdaki özellikleri sağlayan bir iş parçacığı güvenli koleksiyon sınıfı şöyledir:  
  
-   Üretici-tüketici deseninin bir uygulaması.  
  
-   Eş zamanlı ekleme ve birden çok iş parçacığından öğelerinin sürüyor.  
  
-   İsteğe bağlı kapasite üst sınırı.  
  
-   Koleksiyon boş ya da tam olduğunda engelleme ekleme ve kaldırma işlemleri.  
  
-   Ekleme ve kaldırma ", engelleme yapmadığından veya belirli bir süre kadar engelleme işlemleri deneyin".  
  
-   Uygulayan herhangi bir koleksiyon türü yalıtır <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
-   İptal belirteçleri ile iptal etme.  
  
-   Sabit listesi ile iki tür `foreach` (`For Each` Visual Basic'te):  
  
    1.  Salt okunur sabit listesi.  
  
    2.  Bunlar tıklamanızdır öğeleri kaldırır numaralandırması.  
  
## <a name="bounding-and-blocking-support"></a>Sınırlama ve engelleme desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601> sınırlama ve engelleme destekler. Yol sınırlama koleksiyonunun kapasite üst sınırı ayarlayabilirsiniz. Sınırlayıcı bellek koleksiyonda en büyük boyutunu denetlemenizi sağlar ve alıcı iş parçacığı önceden tablasından taşınmasını oluşturmayan iş parçacıkları engeller belirli senaryolarda önemlidir.  
  
 Birden çok iş parçacığı veya görev öğeleri koleksiyona eşzamanlı olarak ekleyebilir ve koleksiyonu belirtilen en yüksek kapasiteye ulaşırsa, öğeyi kaldırılana kadar üretim iş parçacıkları engeller. Birden fazla tüketici öğelerini eşzamanlı olarak kaldırabilir ve koleksiyonu boş hale gelirse bir üretici bir öğe ekler kadar alıcı iş parçacığı engeller. Üretim iş parçacığı çağırabilirsiniz <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> daha fazla öğe eklenmesi belirtmek için. Tüketiciler İzleyici <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> özelliği zaman koleksiyonu boş olan ve daha fazla öğe eklenir. Aşağıdaki örnek, bir basit Blockingcollection'a 100 sınırlanmış kapasitesine sahip gösterir. Bazı dış koşul true'dur ve sonra çağıran sürece bir üretici görev öğeleri koleksiyona ekler. <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>. Tüketici Görev öğeleri kadar sürer <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> özelliği true ise.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Tam bir örnek için bkz. [nasıl yapılır: ekleme ve öğeleri tek tek bir Blockingcollection'dan](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>İşlemleri engelleme zaman aşımına uğradı  
 Buna engelleyen zaman aşımına <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemi operations sınırlanmış koleksiyonlarda çalışır eklemek veya bir öğe. Bir öğe varsa başvuruyla geçirildi değişken içine yerleştirilir ve yöntem true değerini döndürür. Yöntemi, belirtilen bir zaman aşımı süresi hiçbir öğe alınır değilse false döndürür. İş parçacığı ardından koleksiyon erişmek yeniden denemeden önce diğer bazı yararlı işleri yapmak ücretsizdir. Zamanlanmış erişimi engelleyen bir örneği için ikinci örneğe bakın [nasıl yapılır: ekleme ve öğeleri tek tek bir Blockingcollection'dan](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>İptal etme ekleyin ve işlemleri Al  
 Ekleme ve alma işlemleri, genellikle bir döngüde gerçekleştirilir. Bir döngü geçirerek iptal edebilirsiniz bir <xref:System.Threading.CancellationToken> için <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemi ve ardından belirtecin değerini kontrol <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> her yinelemede özelliği. Ardından değeri true ise, size tüm kaynakları temizleme ve döngüden çıkma iptal isteğine yanıt vermesi olduğu. Aşağıdaki örnek, aşırı yüklenmesini gösterir <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> bir iptal belirteci alır ve kodu, bunu kullanır:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 İkinci örnekte iptal desteği ekleme örneği için bkz. [nasıl yapılır: ekleme ve öğeleri tek tek bir Blockingcollection'dan](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Koleksiyon türü belirtme  
 Oluştururken bir <xref:System.Collections.Concurrent.BlockingCollection%601>, yalnızca sınırlı kapasite aynı zamanda toplama türünü kullanmak için belirtebilirsiniz. Örneğin, belirtebilirsiniz bir <xref:System.Collections.Concurrent.ConcurrentQueue%601> ilk olarak-ilk çıkar (FIFO) davranışı için veya bir <xref:System.Collections.Concurrent.ConcurrentStack%601> son içinde-ilk çıkar (LIFO) davranışı için. Uygulayan herhangi bir koleksiyon sınıfının kullanabileceğiniz <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> arabirimi. İçin varsayılan toplama türü <xref:System.Collections.Concurrent.BlockingCollection%601> olduğu <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Collections.Concurrent.BlockingCollection%601> 1000 bir kapasiteye sahiptir ve kullandığı dizelerden oluşan bir <xref:System.Collections.Concurrent.ConcurrentBag%601>:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Daha fazla bilgi için [nasıl yapılır: ekleme sınırlama ve engelleme işlevi bir koleksiyona](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>IEnumerable desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601> sağlar bir <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yönteminin kullanılacağını tüketiciler tanıyan `foreach` (`For Each` Visual Basic'te) koleksiyonu tamamlanana kadar öğeleri kaldırmak için yani boştur ve daha fazla öğe eklenir. Daha fazla bilgi için [nasıl yapılır: bir BlockingCollection öğeleri kaldırmak için ForEach kullanım](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Birçok BlockingCollections kullanma  
 Aynı anda birden çok koleksiyon öğeleri almak bir tüketici gereken senaryolarda, dizileri oluşturabilirsiniz <xref:System.Collections.Concurrent.BlockingCollection%601> ve statik yöntemleri kullanın <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> , ekleme veya koleksiyonlar birinden yararlanın dizisi. Bir koleksiyon engelleme, işlemi gerçekleştiren bir bulana kadar yöntemi hemen başka bir çalışır. Daha fazla bilgi için [nasıl yapılır: işlem hattında engelleme koleksiyonları kullanım diziler](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Koleksiyonlar ve Veri Yapıları](../../../../docs/standard/collections/index.md)  
- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
