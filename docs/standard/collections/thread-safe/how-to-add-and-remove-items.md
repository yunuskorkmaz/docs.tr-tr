---
title: "Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: dc4d13e09a91633fac1fcf5bd8ab5b043473bd7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711317"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma
Bu örnek, bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>öğe ekleme, alma, güncelleştirme ve kaldırma işlemlerinin nasıl yapılacağını gösterir. Bu koleksiyon sınıfı, iş parçacığı güvenli bir uygulama. Birden çok iş parçacığının aynı anda öğelere erişmeye çalıştığı her seferinde kullanmanızı öneririz.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, kodun, verileri ekleme veya kaldırma girişiminden önce bir anahtarın mevcut olup olmadığını kontrol etmek için gereksiz hale getirmek üzere çeşitli yöntemler sunar. Aşağıdaki tabloda bu kullanışlı yöntemler listelenmekte ve ne zaman kullanılacağı açıklanmaktadır.  
  
|Yöntem|Şu durumlarda kullan...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Belirtilen anahtar için yeni bir değer eklemek istiyorsunuz ve anahtar zaten varsa, değerini değiştirmek istersiniz.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Belirtilen bir anahtar için varolan değeri almak istiyorsunuz ve anahtar yoksa anahtar/değer çifti belirtmek istersiniz.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Anahtar/değer çifti eklemek, almak, güncelleştirmek veya kaldırmak, anahtar zaten varsa veya deneme başka bir nedenle başarısız olursa, alternatif bir işlem yapmak istersiniz.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bazı öğeleri eşzamanlı olarak bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> eklemek için iki <xref:System.Threading.Tasks.Task> örneği kullanılmıştır ve sonra öğelerin başarıyla eklendiğini göstermek için tüm içerik çıkışları oluşur. Örnek ayrıca, koleksiyondan öğe eklemek, güncelleştirmek ve almak için <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> yöntemlerinin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, çok iş parçacıklı senaryolar için tasarlanmıştır. Koleksiyonda öğe eklemek veya kaldırmak için kodunuzda kilit kullanmanız gerekmez. Ancak, bir iş parçacığının bir değeri alabilmesi ve aynı anahtara yeni bir değer vererek koleksiyonu hemen güncellemek için başka bir iş parçacığında her zaman mümkündür.  
  
 Ayrıca, tüm <xref:System.Collections.Concurrent.ConcurrentDictionary%602> yöntemleri iş parçacığı açısından güvenlidir, ancak tüm yöntemler atomik, özellikle <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>değildir. Bu yöntemlere geçirilen kullanıcı temsilcisi sözlüğün iç kilidi dışında çağrılır (Bu işlem, bilinmeyen kodun tüm iş parçacıklarını engellemesini engellemek için yapılır). Bu nedenle, bu olay sırası oluşması mümkündür:  
  
 1\) threadA <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>çağırır, hiçbir öğe buluyor ve valueFactory temsilcisini çağırarak eklenecek yeni bir öğe oluşturuyor.  
  
 2\) threadB aynı anda <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> çağırır, valueFactory temsilcisi çağrılır ve bu, tehdit ve sonra iç kilidine ulaşır ve bu nedenle yeni anahtar-değer çifti sözlüğe eklenir.  
  
 3\) threadA 'un Kullanıcı temsilcisi tamamlanır ve iş parçacığı kilidine ulaşır, ancak artık öğenin zaten var olduğunu görüyor.  
  
 4\) threadA bir "Get" gerçekleştirir ve threadB tarafından daha önce eklenmiş olan verileri döndürür.  
  
 Bu nedenle, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> tarafından döndürülen verilerin, iş parçacığının valueFactory tarafından oluşturulan verilerle aynı olduğu garanti edilmez. <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> çağrıldığında benzer bir olay dizisi meydana gelebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
