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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6aa309f2c6c44934f491229ac43003a05301bacb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569752"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma
Bu örnek eklemek, alma, güncelleştirme ve öğeleri kaldırmak nasıl gösterir bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Bu koleksiyon sınıfı bir iş parçacığı uygulamasıdır. Birden çok iş parçacığı öğeleri aynı anda erişmeye çalışıyor olabilir her bunu kullanmanızı öneririz.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ilk veri ekleme veya kaldırma çalışmadan önce bir anahtarı var olup olmadığını denetlemek kod için gereksiz olun birkaç kullanışlı yöntemler sağlar. Aşağıdaki tabloda bu kullanışlı yöntemler listelenmekte ve bunların ne zaman kullanılacağı açıklanmaktadır.  
  
|Yöntem|Şu durumlarda kullanın...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Belirtilen anahtar için yeni bir değer eklemek istediğiniz ve değerini değiştirmek isterseniz anahtar zaten varsa.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Belirtilen anahtar için mevcut değeri almak istediğiniz ve anahtar mevcut değilse, bir anahtar/değer çifti belirtmek istiyorsanız.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Ekle, Al, güncelleştirmek veya bir anahtar/değer çiftini kaldırmak istediğiniz ve anahtar zaten var veya herhangi bir nedenden dolayı denemesi başarısız olursa, alternatif bir eylemi yapmak istiyorsunuz.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki kullanan <xref:System.Threading.Tasks.Task> bazı öğeler eklemek için örnek bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> aynı anda ve tüm öğeleri başarıyla eklendiğini göstermek için içeriği çıkarır. Bu örnek ayrıca nasıl kullanılacağını gösterir <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> yöntemleri eklemek, güncelleştirmek ve tüm öğeleri koleksiyondan Al.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> birden çok iş parçacıklı senaryoları için tasarlanmıştır. Öğe eklemek veya koleksiyondan kaldırmak için kodunuzda kilitleri kullanmak zorunda değil. Bununla birlikte, her zaman bir değer almak için bir iş parçacığı ve yeni bir değer aynı anahtarı vererek koleksiyonu hemen güncelleştirmek için başka bir iş parçacığı mümkündür.  
  
 Ayrıca, ancak tüm yöntemleri <xref:System.Collections.Concurrent.ConcurrentDictionary%602> olan tüm yöntemleri atomik, özellikle iş parçacığı, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Bu yönteme geçirilen kullanıcı temsilci sözlüğün iç kilit dışında çağrılır. (Bu bilinmeyen kod tüm iş parçacığı engellemelerini önlemek için yapılır.) Bu nedenle bu gerçekleşecek olaylar dizisi için mümkündür:  
  
 1\) threadA çağrıları <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, öğe bulur ve valueFactory temsilci çağırarak eklenecek yeni bir öğesi oluşturur.  
  
 2\) threadB çağrıları <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> eşzamanlı olarak, kendi valueFactory temsilci çağrılır ve iç kilidi threadA önce ulaştığında ve bu nedenle, yeni bir anahtar-değer çifti eklenir sözlüğe.  
  
 3\) threadA'ın kullanıcı temsilci tamamlar ve iş parçacığı kilidi sırasında ulaştığında, ancak şimdi öğe zaten görür  
  
 4\) threadA "Get" gerçekleştirir ve threadB tarafından önceden eklendi verileri döndürür.  
  
 Bu nedenle, bu değil tarafından döndürülen veri garanti <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> iş parçacığının valueFactory tarafından oluşturulan aynı veridir. Benzer bir olay dizisi oluşabilir zaman <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> olarak adlandırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
