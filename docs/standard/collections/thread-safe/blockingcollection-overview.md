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
ms.openlocfilehash: fb01d29c723962e28d8ec4afc984cb4d6c48f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711330"
---
# <a name="blockingcollection-overview"></a>BlockingCollection Genel Bakışı
<xref:System.Collections.Concurrent.BlockingCollection%601>aşağıdaki özellikleri sağlayan iş parçacığı güvenli bir koleksiyon sınıfıdır:  
  
- Üretici-Tüketici modelinin uygulanması.  
  
- Eş zamanlı ekleme ve birden çok iş parçacığı öğeleri alma.  
  
- İsteğe bağlı maksimum kapasite.  
  
- Toplama boş veya dolu olduğunda engelleyen ekleme ve kaldırma işlemleri.  
  
- Belirli bir süreyi engellemeyen veya engellemeyen "try" işlemleri ekleme ve kaldırma.  
  
- Uygulayan herhangi bir toplama türünü kapsüller<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
- İptal jetonları ile iptal.  
  
- İki tür numaralandırma ile `foreach` `For Each` (Visual Basic'te):  
  
    1. Salt okunur numaralandırma.  
  
    2. Numaralandırılınırken öğeleri kaldıran numaralandırma.  
  
## <a name="bounding-and-blocking-support"></a>Sınırlama ve Engelleme Desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601>sınırlandırma ve engellemeyi destekler. Sınırlama, koleksiyonun maksimum kapasitesini ayarlayabileceğiniz anlamına gelir. Sınırlama, bellekteki koleksiyonun en büyük boyutunu denetlemenize olanak sağladığından ve üreten iş parçacıklarının tüketen iş parçacıklarının çok ilerisine taşınmasını önlediği için belirli senaryolarda önemlidir.  
  
 Birden çok iş parçacığı veya görev koleksiyona aynı anda öğe ekleyebilir ve koleksiyon belirtilen maksimum kapasiteye ulaşırsa, bir öğe kaldırılana kadar üretim iş parçacıkları engellenir. Birden çok tüketici öğeleri aynı anda kaldırabilir ve koleksiyon boşalırsa, tüketen iş parçacıkları üretici bir öğe ekleyene kadar engellenir. Üreten bir iş <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> parçacığı, başka öğe eklenmeyeceğini belirtmek için arayabilir. Tüketiciler, <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> koleksiyonun ne zaman boş olduğunu ve başka öğe eklenmeyeceğini bilmek için özelliği izler. Aşağıdaki örnekte, sınırlı kapasitesi 100 olan basit bir Engelleme Koleksiyonu gösterilmektedir. Üretici görevi, bazı dış koşullar doğru olduğu sürece koleksiyona <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>öğeler ekler ve sonra çağırır. Tüketici görevi, özellik <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> doğru olana kadar öğeleri alır.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Tam bir örnek için [bkz: Engelleme Koleksiyonundan Tek tek Öğe Ekleme ve Alma.](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)  
  
## <a name="timed-blocking-operations"></a>Zamanlı Engelleme İşlemleri  
 Zamanlanmış engelleme <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> sınırlanmış koleksiyonlar üzerindeki işlemlerde, yöntem bir öğe eklemeye veya almaya çalışır. Bir öğe varsa, başvuru tarafından geçirilen değişkene yerleştirilir ve yöntem doğru döndürür. Belirtilen bir zaman uzatma döneminden sonra hiçbir öğe alınmazsa yöntem yanlış döndürür. İş parçacığı daha sonra koleksiyona erişmek için yeniden denemeden önce başka yararlı işler yapmak için ücretsizdir. Zamanlanmış engelleme erişimi örneği için, [Nasıl Olur: BlokingKoleksiyonundan Tek tek Öğe Ekleme ve Alma'daki](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)ikinci örneğe bakın.  
  
## <a name="cancelling-add-and-take-operations"></a>Ekle ve Alma İşlemlerini İptal Etme  
 Ekle ve Al işlemleri genellikle bir döngü içinde gerçekleştirilir. Bir döngüyü <xref:System.Threading.CancellationToken> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yönteme geçirerek ve sonra her yinelemede belirteç <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliğinin değerini denetleyerek iptal edebilirsiniz. Değer doğruysa, iptal isteğini herhangi bir kaynağı temizleyerek ve döngüden çıkararak yanıtlamak size kılır. Aşağıdaki örnek, iptal jetonu alan aşırı <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> yüklemeyi ve onu kullanan kodu gösterir:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 İptal desteği ekleme nin bir örneği için, [engelleme koleksiyonundan öğeleri tek tek ekleme ve alma](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)işlemi nin ikinci örneğine bakın.  
  
## <a name="specifying-the-collection-type"></a>Tahsilat Türünü Belirtme  
 Bir <xref:System.Collections.Concurrent.BlockingCollection%601>, oluşturduğunuzda yalnızca sınırlanmış kapasiteyi değil, aynı zamanda kullanılacak koleksiyon türünü de belirtebilirsiniz. Örneğin, ilk ilk <xref:System.Collections.Concurrent.ConcurrentQueue%601> in-first out (FIFO) davranışı veya <xref:System.Collections.Concurrent.ConcurrentStack%601> son ilk çıkış (LIFO) davranışı için bir belirtebilirsiniz. <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> Arabirimi uygulayan herhangi bir koleksiyon sınıfı kullanabilirsiniz. Varsayılan toplama <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601>türü. Aşağıdaki kod örneği, 1000 kapasiteye sahip bir <xref:System.Collections.Concurrent.BlockingCollection%601> dize oluşturmanın <xref:System.Collections.Concurrent.ConcurrentBag%601>nasıl yapılacağını gösterir ve aşağıdakileri kullanır:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Daha fazla bilgi için [bkz: Koleksiyona Bağlama ve Engelleme İşlevselliği Ekleme.](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)  
  
## <a name="ienumerable-support"></a>Tümevarım Desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601>tüketicilerin <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> koleksiyon tamamlanana kadar `foreach` öğeleri`For Each` kaldırmak için (Visual Basic'te) kullanmalarını sağlayan bir yöntem sağlar, bu da boş olduğu ve başka öğe eklenmeyeceğini anlamına gelir. Daha fazla bilgi için [bkz: Engelleme Koleksiyonundaki Öğeleri Kaldırmak için ForEach'i kullanın.](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)  
  
## <a name="using-many-blockingcollections-as-one"></a>Birçok Engelleme Koleksiyonlarını Tek Olarak Kullanma  
 Bir tüketicinin aynı anda birden çok koleksiyondan öğe alması gereken senaryolar için, dizideki koleksiyonlardan herhangi birini <xref:System.Collections.Concurrent.BlockingCollection%601> ekleyecek veya alacak statik yöntemlerdizileri <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> oluşturabilir ve kullanabilirsiniz. Bir koleksiyon engelleyiciyse, yöntem işlemi gerçekleştirebilecek bir koleksiyon bulana kadar hemen başka bir yöntem dener. Daha fazla bilgi için [bkz: Engelleyici Koleksiyon Dizilerini Bir Ardışık Düzen'de kullanın.](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Koleksiyonlar ve Veri Yapıları](../../../../docs/standard/collections/index.md)
- [İş Parçacığı Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
