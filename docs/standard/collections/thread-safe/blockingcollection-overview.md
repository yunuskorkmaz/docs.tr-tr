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
ms.openlocfilehash: 708ab9dc8df2ee3128036ffc71e9abc51a56e33b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287919"
---
# <a name="blockingcollection-overview"></a>BlockingCollection Genel Bakışı
<xref:System.Collections.Concurrent.BlockingCollection%601>, aşağıdaki özellikleri sağlayan iş parçacığı güvenli bir koleksiyon sınıfıdır:  
  
- Üretici-tüketici deseninin bir uygulamasıdır.  
  
- Birden çok iş parçacığından öğe ekleme ve alma.  
  
- İsteğe bağlı maksimum kapasite.  
  
- Koleksiyonun ne zaman boş veya tam olduğunu engelleyen ekleme ve kaldırma işlemleri.  
  
- Ekleme ve kaldırma "TRY" işlemleri, belirli bir süre içinde engellenmez veya engellenmiyor.  
  
- Uygulayan tüm koleksiyon türlerini Kapsüller<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
- İptal belirteçleriyle iptal.  
  
- İle iki tür numaralandırma `foreach` ( `For Each` Visual Basic):  
  
    1. Salt okuma numaralandırması.  
  
    2. Öğeleri numaralandırıldıkları gibi kaldıran sabit listesi.  
  
## <a name="bounding-and-blocking-support"></a>Sınırlama ve engelleme desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601>sınırlayıcı ve engellemeyi destekler. Sınırlayıcı, koleksiyonun maksimum kapasitesini ayarlayabilmeniz anlamına gelir. Belirli senaryolarda sınırlayıcı önemlidir çünkü koleksiyonun en büyük boyutunu bellekte denetlemenizi sağlar ve üreten iş parçacıklarının, tüketen iş parçacıklarından çok daha önce ilerlemenize engel olur.  
  
 Birden çok iş parçacığı veya görev koleksiyona aynı anda öğe ekleyebilir ve koleksiyon belirtilen en büyük kapasiteye ulaşırsa, bir öğe kaldırılana kadar, üreten iş parçacıkları engeller. Birden çok tüketici aynı anda öğeleri kaldırabilir ve koleksiyon boşsa, bir üretici bir öğe eklemeene kadar tüketim iş parçacıkları engeller. Bir üreten iş parçacığı, <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> daha fazla öğe eklenmeyeceğini belirtmek için çağırabilir. Tüketiciler, <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> koleksiyonun ne zaman boş olduğunu ve daha fazla öğenin eklenmediğini bilen özelliği izler. Aşağıdaki örnekte, 100 sınırlı kapasitesi olan basit bir BlockingCollection gösterilmektedir. Bir üretici görevi, bazı dış koşullar doğru olduğu sürece koleksiyona öğe ekler ve ardından çağırır <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> . Tüketici görevi, özelliği true olana kadar öğeleri alır <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> .  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Tüm bir örnek için bkz. [nasıl yapılır: öğeleri bir BlockingCollection 'Dan ayrı olarak ekleme ve alma](how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Zamanlanmış engelleyici Işlemler  
 Sınırlanmış koleksiyonlar üzerinde zaman aşımına uğramaya <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlemlere, yöntemi ekleme veya bir öğe almaya çalışır. Bir öğe varsa, başvuruya göre geçirilen değişkene yerleştirilir ve yöntemi true değerini döndürür. Belirtilen bir zaman aşımı süresinden sonra hiçbir öğe alınmamışsa, yöntem false döndürür. Daha sonra iş parçacığı, koleksiyona erişmeyi yeniden denemeden önce başka bir faydalı iş yapmak için ücretsizdir. Erişimin zaman aşımına uğraması hakkında bir örnek için bkz. [nasıl yapılır: öğeleri bir BlockingCollection 'Dan tek tek ekleme ve alma](how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Ekleme ve alma Işlemleri iptal ediliyor  
 Ekleme ve alma işlemleri genellikle bir döngüde gerçekleştirilir. Bir döngüyü <xref:System.Threading.CancellationToken> <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemine geçirerek ve sonra her yinelemede belirtecin özelliğinin değerini denetleyerek iptal edebilirsiniz <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> . Değer true ise, herhangi bir kaynağı temizleyip döngüden çıkarken iptal isteğine yanıt vermek sizin için olur. Aşağıdaki örnek, <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> bir iptal belirteci ve onu kullanan kodu alan aşırı yüklemesini gösterir:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 İptal desteğinin nasıl ekleneceği hakkında bir örnek için bkz. [nasıl yapılır: öğeleri bir BlockingCollection 'Dan tek tek ekleme ve alma](how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Koleksiyon türünü belirtme  
 Bir oluşturduğunuzda <xref:System.Collections.Concurrent.BlockingCollection%601> , yalnızca sınırlanmış kapasiteyi değil, kullanılacak koleksiyon türünü de belirtebilirsiniz. Örneğin, ilk <xref:System.Collections.Concurrent.ConcurrentQueue%601> çıkar (FIFO) davranışını veya <xref:System.Collections.Concurrent.ConcurrentStack%601> en son bir for-Out (LIFO) davranışını belirtebilirsiniz. Arabirimini uygulayan herhangi bir koleksiyon sınıfını kullanabilirsiniz <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> . İçin varsayılan koleksiyon türü <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> . Aşağıdaki kod örneği, <xref:System.Collections.Concurrent.BlockingCollection%601> 1000 kapasiteye sahip dizelerin nasıl oluşturulacağını gösterir ve şunu kullanır <xref:System.Collections.Concurrent.ConcurrentBag%601> :  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: koleksiyona sınırlama ve engelleme Işlevi ekleme](how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>IEnumerable desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601>, bir <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> `foreach` `For Each` koleksiyon tamamlanana kadar öğeleri kaldırmak için (Visual Basic olarak), boş olduğu ve daha fazla öğe eklenecek bir yöntem sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: bir BlockingCollection Içindeki öğeleri kaldırmak Için foreach kullanma](how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Birçok BlockingCollections 'ı tek tek kullanma  
 Bir tüketicinin birden çok koleksiyondan öğe eşzamanlı olarak üstlenilmesi gereken senaryolarda, diziler oluşturabilir <xref:System.Collections.Concurrent.BlockingCollection%601> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> dizideki koleksiyonlara eklenecek ya da bu koleksiyondan alma yapılacak statik yöntemleri kullanabilirsiniz. Bir koleksiyon engelliyorsa, yöntemi, işlemi gerçekleştirebilecek bir tane bulana kadar hemen başka bir yöntem dener. Daha fazla bilgi için bkz. [nasıl yapılır: bir işlem hattında engelleme koleksiyonlarının dizilerini kullanma](how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Koleksiyonlar ve veri yapıları](../index.md)
- [İş parçacığı güvenli Koleksiyonlar](index.md)
