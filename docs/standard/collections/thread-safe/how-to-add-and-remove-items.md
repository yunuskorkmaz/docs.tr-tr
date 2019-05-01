---
title: "Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'den Alma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d8b1c63f10d1d79c3fec6cad87c9a82f03716c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052657"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'den Alma
Bu örnek, ekleyin, alma, güncelleştirme ve öğelerden Kaldır gösterir. bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Bir iş parçacığı açısından güvenli uygulaması bu koleksiyon sınıfıdır. Birden çok iş parçacığı öğeleri aynı anda erişmeye çalışıyor olabilir her bunu kullanmanızı öneririz.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ilk veri ekleme veya kaldırma çalışmadan önce bir anahtar var olup olmadığını denetlemek kod için gereksiz hale getiren çeşitli kullanışlı yöntemler sunar. Aşağıdaki tabloda bu yöntemler listeler ve bunların ne zaman kullanılacağı açıklanır.  
  
|Yöntem|Şu durumlarda kullanın...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Belirtilen anahtar için yeni bir değer eklemek istediğiniz ve anahtarı zaten varsa, değeri değiştirmek istiyorsunuz.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Belirtilen anahtar mevcut değerini almak istediğiniz ve anahtar mevcut değilse, bir anahtar/değer çifti belirtmek istediğinizde.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Ekle, Al, güncelleştirmek veya bir anahtar/değer çiftini kaldırmak istediğiniz ve anahtar zaten var veya başka bir nedenle denemesi başarısız olursa, alternatif bir eylem gerçekleştirmek istediğiniz.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki örnekte <xref:System.Threading.Tasks.Task> örnekleri için bazı öğeler eklemek için bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> eşzamanlı ve tüm öğeler başarıyla eklendiğini gösterilecek içeriğini çıkarır. Örnek ayrıca nasıl kullanılacağını gösterir <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> yöntemleri eklemek, güncelleştirme ve tüm öğeleri koleksiyondan Al.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> çok iş parçacıklı senaryoları için tasarlanmıştır. Kilit ekleme veya öğeleri koleksiyondan kaldırmak için kodunuzda kullanmak zorunda değil. Ancak, her zaman bir değer almak için bir iş parçacığı ve yeni bir değer aynı anahtara vererek koleksiyonu hemen güncelleştirmek için başka bir iş parçacığı mümkündür.  
  
 Ayrıca, ancak tüm yöntemleri <xref:System.Collections.Concurrent.ConcurrentDictionary%602> olan iş parçacığı açısından güvenli, kararlı, özellikle olan tüm yöntemleri <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Bu yönteme geçirilen kullanıcı temsilcisine sözlüğün iç kilit (Bu bilinmeyen kod tüm iş parçacıklarının engellemesini önlemek için yapılır) dışında çağrılır. Bu nedenle, oluşacak olayları bu dizi için mümkündür:  
  
 1\) threadA çağrıları <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, hiçbir öğeyi bulur ve valueFactory temsilci çağırarak eklenecek yeni bir öğe oluşturur.  
  
 2\) threadB çağrıları <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> eş zamanlı olarak, kendi valueFactory temsilci çağrılır ve iç kilit threadA önce ulaştığında ve yeni anahtar-değer çiftini sözlüğe eklenen şekilde.  
  
 3\) threadA'ın kullanıcı temsilcisinde tamamlanır ve iş parçacığı kilit ulaşan, ancak öğe zaten var. Şimdi görür.  
  
 4\) threadA "Get" gerçekleştirir ve threadB tarafından daha önceden eklenmiş verileri döndürür.  
  
 Bu nedenle, böyle değildir, tarafından döndürülen veri garanti <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> iş parçacığının valueFactory tarafından oluşturulan aynı verilerdir. Benzer bir olay dizisi oluşabilir olduğunda <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
