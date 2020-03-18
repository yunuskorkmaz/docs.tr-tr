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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711317"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma
Bu örnek, bir öğenin nasıl ekleyeceğini, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>alın, güncelleştirilip kaldırılacaklarını gösterir. Bu koleksiyon sınıfı iş parçacığı güvenli bir uygulamadır. Birden çok iş parçacığı öğelere aynı anda erişmeye çalışırken olduğunda kullanmanızı öneririz.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>veri eklemeye veya kaldırmaya çalışmadan önce bir anahtarın var olup olmadığını önce kodun kontrol etmesini gereksiz hale getiren çeşitli kolaylık yöntemleri sağlar. Aşağıdaki tabloda bu kolaylık yöntemleri listelanır ve ne zaman kullanılacağı açıklanır.  
  
|Yöntem|Ne zaman kullanın...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Belirtilen bir anahtar için yeni bir değer eklemek istiyorsunuz ve anahtar zaten varsa, değerini değiştirmek istiyorsunuz.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Belirtilen bir anahtar için varolan değeri almak istiyorsunuz ve anahtar yoksa bir anahtar/değer çifti belirtmek istiyorsunuz.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Bir anahtar/değer çifti eklemek, almak, güncelleştirmek veya kaldırmak istiyorsunuz ve anahtar zaten varsa veya girişim başka bir nedenle başarısız olursa, bazı alternatif eylemlerde bulunmak istiyorsunuz.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Task> aynı <xref:System.Collections.Concurrent.ConcurrentDictionary%602> anda bazı öğeleri eklemek için iki örnek kullanır ve sonra öğelerin başarıyla eklandığını göstermek için tüm içeriğini çıktırır. Örnek, koleksiyondan öğeleri <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>eklemek, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> güncelleştirmek ve almak için ,, ve <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>yöntemlerinasıl kullanılacağını da gösterir.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>çok iş parçacığı senaryoları için tasarlanmıştır. Öğeleri koleksiyondan eklemek veya kaldırmak için kodunuzda kilit kullanmanız gerekmez. Ancak, bir iş parçacığının bir değer alması ve başka bir iş parçacığının aynı anahtara yeni bir değer vererek koleksiyonu hemen güncelleştirmesi her zaman mümkündür.  
  
 Ayrıca, tüm yöntemler <xref:System.Collections.Concurrent.ConcurrentDictionary%602> iplik güvenli olmasına rağmen, tüm <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> yöntemler <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>atomik, özellikle ve . Bu yöntemlere geçirilen kullanıcı temsilcisi sözlüğün iç kilidi dışında çağrılır (bu, bilinmeyen kodun tüm iş parçacıklarını engellemesini önlemek için yapılır). Bu nedenle, bu olaylar dizisinin oluşması mümkündür:  
  
 1\) threadA <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>çağırır, öğe yi bulur ve valueFactory temsilcisini çağırarak Ekle'ye yeni bir öğe oluşturur.  
  
 2\) threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> aynı anda çağırır, onun valueFactory temsilcisi çağrılır ve threadA önce iç kilit geldi ve böylece yeni anahtar değeri çifti sözlüğe eklenir.  
  
 3\) threadA kullanıcı temsilcisi tamamlar ve iş parçacığı kilit geldiğinde, ancak şimdi öğenin zaten var olduğunu görür.  
  
 4\) threadA bir "Get" gerçekleştirir ve daha önce threadB tarafından eklenen verileri döndürür.  
  
 Bu nedenle, döndürülen <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> verilerin iş parçacığının değeri Factory tarafından oluşturulan aynı veriler olduğu garanti edilmez. Çağrıldığında <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> benzer bir olaylar dizisi oluşabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş Parçacığı Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
