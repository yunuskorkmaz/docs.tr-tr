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
ms.openlocfilehash: 67e752b9997301fcb3140539255fc32572bfd6e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573626"
---
# <a name="blockingcollection-overview"></a>BlockingCollection Genel Bakışı
<xref:System.Collections.Concurrent.BlockingCollection%601> Aşağıdaki özellikleri sağlayan bir iş parçacığı koleksiyonunun sınıfı şöyledir:  
  
-   Üretici-tüketici düzeni uygulaması.  
  
-   Eşzamanlı eklemek ve birden çok iş parçacığından öğelerinin sürüyor.  
  
-   İsteğe bağlı kapasite üst sınırı.  
  
-   Koleksiyon boş ya da tam olduğunda engelleme ekleme ve kaldırma işlemleri.  
  
-   Ekleme ve kaldırma ", değil engelleyebilir veya belirli bir süre kadar engelleyebilir işlemleri deneyin".  
  
-   Uygulayan herhangi bir koleksiyon türü yalıtır <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
-   İptal belirteçleri iptalini.  
  
-   İki tür olan numaralandırma `foreach` (`For Each` Visual Basic'te):  
  
    1.  Salt okunur numaralandırması.  
  
    2.  Bunlar numaralandırılır gibi öğeleri kaldırır numaralandırması.  
  
## <a name="bounding-and-blocking-support"></a>Sınırlama ve engelleme desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601> sınırlama ve engelleme destekler. Anlamına gelir sınırlayıcı koleksiyon maksimum kapasitesini ayarlayabilirsiniz. Sınırlayıcı bellek koleksiyonunda en büyük boyutunu denetlemek sağlar ve öncesinde Süren iş parçacığı çok taşıma üretmeye iş parçacığı engeller belirli senaryolarda önemlidir.  
  
 Birden çok iş parçacığı veya görevleri öğeler koleksiyonuna eşzamanlı olarak ekleyebilirsiniz ve koleksiyon belirtilen kapasitesinin üst sınırına ulaşırsa, öğeyi kaldırılana kadar üretmeye iş parçacığı engeller. Birden çok tüketiciye öğeleri aynı anda kaldırabilirsiniz ve koleksiyonu boş olursa, bir üretici bir öğe ekler kadar süren iş parçacığı engeller. Oluşturmayan bir iş parçacığı çağırabilir <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> başka öğe yok eklenmesi belirtmek için. Tüketiciler İzleyici <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> zaman koleksiyonu boş olan ve daha fazla öğe eklenecek bilmeniz özelliği. Aşağıdaki örnek, 100 sınırlanmış kapasitesine sahip basit bir BlockingCollection gösterir. Bazı dış koşul true olduğunda ve daha sonra çağırır sürece üretici görev öğeler koleksiyonuna ekler. <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>. Tüketici Görev öğeleri kadar geçen <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> özelliği true ise.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Tam bir örnek için bkz: [nasıl yapılır: ekleme ve ele öğeleri tek tek bir BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>İşlemleri engelleyen zaman aşımına uğradı  
 Buna engelleme zaman aşımına <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlemleri sınırlanmış koleksiyonlarda yöntemi çalıştığında eklemek veya öğeyi almak. Bir öğe varsa dosya başvuruya göre geçirilen değişkeni yerleştirilir ve yöntem true değerini döndürür. Hiçbir öğe belirtilen bir zaman aşımı süresi alınır varsa yöntemi false değerini döndürür. İş parçacığı sonra koleksiyonuna erişmek yeniden denemeden önce biraz diğer yararlı çalışmanız ücretsizdir. İkinci örnekte bir zaman aşımına erişimi engelleme örnek için bkz [nasıl yapılır: ekleme ve ele öğeleri tek tek bir BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Ekleme ve ele işlemleri iptal ediliyor  
 Ekleyin ve alma işlemleri genellikle bir döngüde gerçekleştirilir. Geçirerek bir döngü iptal bir <xref:System.Threading.CancellationToken> için <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemi ve belirtecin değeri denetleme <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> her bir yineleme özelliği. Ardından değeri true ise, tüm kaynakları temizleme ve döngüden çıkma iptal isteğini yanıt size kadar olan. Aşağıdaki örnek, bir aşırı yüklemesini gösterir <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> iptal belirteci alır ve kod kullanan bu:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 İkinci örnekte iptal desteği eklemek nasıl bir örnek için bkz: [nasıl yapılır: ekleme ve ele öğeleri tek tek bir BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Koleksiyon türünü belirtme  
 Oluştururken bir <xref:System.Collections.Concurrent.BlockingCollection%601>, yalnızca sınırlı kapasite aynı zamanda koleksiyon türünü kullanmak için belirtebilirsiniz. Örneğin, belirtebilirsiniz bir <xref:System.Collections.Concurrent.ConcurrentQueue%601> ilk olarak-ilk çıkar (FIFO) davranışı için veya bir <xref:System.Collections.Concurrent.ConcurrentStack%601> son içinde-ilk çıkar (LIFO) davranışı için. Uygulayan herhangi bir koleksiyon sınıf kullanabilirsiniz <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> arabirimi. Varsayılan koleksiyon türü <xref:System.Collections.Concurrent.BlockingCollection%601> olan <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir bir <xref:System.Collections.Concurrent.BlockingCollection%601> 1000 kapasitesine sahiptir ve kullandığı dizelerin bir <xref:System.Collections.Concurrent.ConcurrentBag%601>:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: ekleme sınırlama ve engelleme işlevi bir koleksiyona](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>IEnumerable desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601> sağlayan bir <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> kullanmasına olanak sağlayan yöntemi `foreach` (`For Each` Visual Basic'te) koleksiyon tamamlanana kadar öğeleri kaldırmak için yani boştur ve daha fazla öğe eklenir. Daha fazla bilgi için bkz: [nasıl yapılır: bir BlockingCollection öğeleri kaldırmak için kullanım ForEach](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Birçok BlockingCollections olarak kullanma  
 İçinde bir tüketici gereken aynı anda birden fazla koleksiyonun öğelerinden yapılacak senaryoları için dizileri oluşturabilirsiniz <xref:System.Collections.Concurrent.BlockingCollection%601> ve statik yöntemler gibi kullandığınız <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> , ekleme veya herhangi birinden koleksiyonlardaki alın dizi. Bir koleksiyon engelleme varsa, işlemi gerçekleştiren bir tane bulana kadar yöntemi hemen başka çalışır. Daha fazla bilgi için bkz: [nasıl yapılır: ardışık düzende engelleme koleksiyonları kullanım diziler](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Koleksiyonlar ve Veri Yapıları](../../../../docs/standard/collections/index.md)  
 [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
