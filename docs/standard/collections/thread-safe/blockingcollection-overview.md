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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711330"
---
# <a name="blockingcollection-overview"></a>BlockingCollection Genel Bakışı
<xref:System.Collections.Concurrent.BlockingCollection%601>, aşağıdaki özellikleri sağlayan iş parçacığı güvenli bir koleksiyon sınıfıdır:  
  
- Üretici-tüketici deseninin bir uygulamasıdır.  
  
- Birden çok iş parçacığından öğe ekleme ve alma.  
  
- İsteğe bağlı maksimum kapasite.  
  
- Koleksiyonun ne zaman boş veya tam olduğunu engelleyen ekleme ve kaldırma işlemleri.  
  
- Ekleme ve kaldırma "TRY" işlemleri, belirli bir süre içinde engellenmez veya engellenmiyor.  
  
- <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> uygulayan tüm koleksiyon türlerini Kapsüller  
  
- İptal belirteçleriyle iptal.  
  
- `foreach` ile iki tür numaralandırma (Visual Basic`For Each`):  
  
    1. Salt okuma numaralandırması.  
  
    2. Öğeleri numaralandırıldıkları gibi kaldıran sabit listesi.  
  
## <a name="bounding-and-blocking-support"></a>Sınırlama ve engelleme desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601> sınırlayıcı ve engellemeyi destekler. Sınırlayıcı, koleksiyonun maksimum kapasitesini ayarlayabilmeniz anlamına gelir. Belirli senaryolarda sınırlayıcı önemlidir çünkü koleksiyonun en büyük boyutunu bellekte denetlemenizi sağlar ve üreten iş parçacıklarının, tüketen iş parçacıklarından çok daha önce ilerlemenize engel olur.  
  
 Birden çok iş parçacığı veya görev koleksiyona aynı anda öğe ekleyebilir ve koleksiyon belirtilen en büyük kapasiteye ulaşırsa, bir öğe kaldırılana kadar, üreten iş parçacıkları engeller. Birden çok tüketici aynı anda öğeleri kaldırabilir ve koleksiyon boşsa, bir üretici bir öğe eklemeene kadar tüketim iş parçacıkları engeller. Bir üreten iş parçacığı, daha fazla öğe eklenmeyeceğini göstermek için <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> çağırabilir. Tüketiciler, koleksiyonun ne zaman boş olduğunu ve daha fazla öğenin eklenmediğini bildirmek için <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> özelliğini izler. Aşağıdaki örnekte, 100 sınırlı kapasitesi olan basit bir BlockingCollection gösterilmektedir. Bir üretici görevi, bazı dış koşullar doğru olduğu sürece koleksiyona öğe ekler ve sonra <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>çağırır. Tüketici görevi, <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> özelliği true olana kadar öğeleri alır.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Tüm bir örnek için bkz. [nasıl yapılır: öğeleri bir BlockingCollection 'Dan ayrı olarak ekleme ve alma](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Zamanlanmış engelleyici Işlemler  
 Sınırlanmış koleksiyonlar üzerinde <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlemler zaman aşımına uğradıktan sonra yöntemi bir öğe eklemeye veya almaya çalışır. Bir öğe varsa, başvuruya göre geçirilen değişkene yerleştirilir ve yöntemi true değerini döndürür. Belirtilen bir zaman aşımı süresinden sonra hiçbir öğe alınmamışsa, yöntem false döndürür. Daha sonra iş parçacığı, koleksiyona erişmeyi yeniden denemeden önce başka bir faydalı iş yapmak için ücretsizdir. Erişimin zaman aşımına uğraması hakkında bir örnek için bkz. [nasıl yapılır: öğeleri bir BlockingCollection 'Dan tek tek ekleme ve alma](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Ekleme ve alma Işlemleri iptal ediliyor  
 Ekleme ve alma işlemleri genellikle bir döngüde gerçekleştirilir. Bir <xref:System.Threading.CancellationToken> <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemine geçirerek ve sonra her yinelemede belirtecin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliğinin değerini denetleyerek bir döngüyü iptal edebilirsiniz. Değer true ise, herhangi bir kaynağı temizleyip döngüden çıkarken iptal isteğine yanıt vermek sizin için olur. Aşağıdaki örnek, bir iptal belirteci alan <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> aşırı yüklemesini ve onu kullanan kodu gösterir:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 İptal desteğinin nasıl ekleneceği hakkında bir örnek için bkz. [nasıl yapılır: öğeleri bir BlockingCollection 'Dan tek tek ekleme ve alma](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Koleksiyon türünü belirtme  
 Bir <xref:System.Collections.Concurrent.BlockingCollection%601>oluşturduğunuzda, yalnızca sınırlanmış kapasiteyi değil, ayrıca kullanılacak koleksiyon türünü de belirtebilirsiniz. Örneğin, ilk çıkar (FıFO) davranışı için bir <xref:System.Collections.Concurrent.ConcurrentQueue%601> veya son ilk çıkar (LıFO) davranışı için bir <xref:System.Collections.Concurrent.ConcurrentStack%601> belirtebilirsiniz. <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> arabirimini uygulayan herhangi bir koleksiyon sınıfını kullanabilirsiniz. <xref:System.Collections.Concurrent.BlockingCollection%601> için varsayılan koleksiyon türü <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Aşağıdaki kod örneği, 1000 kapasiteye sahip dizelerin <xref:System.Collections.Concurrent.BlockingCollection%601> nasıl oluşturulacağını gösterir ve <xref:System.Collections.Concurrent.ConcurrentBag%601>kullanır:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: koleksiyona sınırlama ve engelleme Işlevi ekleme](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>IEnumerable desteği  
 <xref:System.Collections.Concurrent.BlockingCollection%601>, tüketicilerinin Visual Basic`For Each` `foreach` kullanmasını sağlayan bir <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi sağlar, bu, boş olduğu ve daha fazla öğe eklenemeyeceği anlamına gelir. Daha fazla bilgi için bkz. [nasıl yapılır: bir BlockingCollection Içindeki öğeleri kaldırmak Için foreach kullanma](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Birçok BlockingCollections 'ı tek tek kullanma  
 Bir tüketicinin birden fazla koleksiyondan öğe eşzamanlı olarak üstlenilmesi gereken senaryolarda, <xref:System.Collections.Concurrent.BlockingCollection%601> dizileri oluşturabilir ve <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> gibi statik yöntemleri kullanarak dizideki koleksiyonlara eklenecek veya bu koleksiyonları alabilir. Bir koleksiyon engelliyorsa, yöntemi, işlemi gerçekleştirebilecek bir tane bulana kadar hemen başka bir yöntem dener. Daha fazla bilgi için bkz. [nasıl yapılır: bir işlem hattında engelleme koleksiyonlarının dizilerini kullanma](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Koleksiyonlar ve Veri Yapıları](../../../../docs/standard/collections/index.md)
- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
