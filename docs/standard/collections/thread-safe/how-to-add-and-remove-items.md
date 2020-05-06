---
title: "Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma"
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 6e5204c5a71232ef9d1a050891e7fe6d92c375f2
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796125"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma

Bu örnek, bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>öğesinden öğe ekleme, alma, güncelleştirme ve kaldırma işlemlerinin nasıl yapılacağını gösterir. Bu koleksiyon sınıfı, iş parçacığı güvenli bir uygulama. Birden çok iş parçacığının aynı anda öğelere erişmeye çalıştığı her seferinde kullanmanızı öneririz.

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>, kodun, verileri ekleme veya kaldırma girişiminde bulunulmadan önce bir anahtarın mevcut olup olmadığını kontrol etmek için gerekli hale getirmek üzere çeşitli kolay yöntemler sağlar. Aşağıdaki tabloda bu kullanışlı yöntemler listelenmekte ve ne zaman kullanılacağı açıklanmaktadır.

| Yöntem | Şu durumlarda kullan... |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | Belirtilen anahtar için yeni bir değer eklemek istiyorsunuz ve anahtar zaten varsa, değerini değiştirmek istersiniz. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | Belirtilen bir anahtar için varolan değeri almak istiyorsunuz ve anahtar yoksa anahtar/değer çifti belirtmek istersiniz. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A> | Anahtar/değer çifti eklemek, almak, güncelleştirmek veya kaldırmak, anahtar zaten varsa veya deneme başka bir nedenle başarısız olursa, alternatif bir işlem yapmak istersiniz. |

## <a name="example"></a>Örnek

Aşağıdaki örnek, bazı öğeleri <xref:System.Threading.Tasks.Task> <xref:System.Collections.Concurrent.ConcurrentDictionary%602> eşzamanlı olarak eklemek için iki örnek kullanır ve sonra öğelerin başarıyla eklendiğini göstermek için tüm içeriği çıkarır. Örnek ayrıca <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, koleksiyondan öğe eklemek, güncelleştirmek ve <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>almak için <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> ,, ve yöntemlerinin nasıl kullanılacağını gösterir.

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>çok iş parçacıklı senaryolar için tasarlanmıştır. Koleksiyonda öğe eklemek veya kaldırmak için kodunuzda kilit kullanmanız gerekmez. Ancak, bir iş parçacığının bir değeri alabilmesi ve aynı anahtara yeni bir değer vererek koleksiyonu hemen güncellemek için başka bir iş parçacığında her zaman mümkündür.

Ayrıca, tüm yöntemleri iş parçacığı <xref:System.Collections.Concurrent.ConcurrentDictionary%602> açısından güvenli olmasına rağmen, tüm yöntemler atomik, özellikle <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> ve. <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> Bu yöntemlere geçirilen kullanıcı temsilcisi sözlüğün iç kilidi dışında çağrılır (Bu işlem, bilinmeyen kodun tüm iş parçacıklarını engellemesini engellemek için yapılır). Bu nedenle, bu olay sırası oluşması mümkündür:

1. _threada_ çağrısı <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, hiçbir öğe buluyor ve `valueFactory` temsilciyi çağırarak eklenecek yeni bir öğe oluşturuyor.

1. _Threadb_ <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> eşzamanlı olarak çağrılır, `valueFactory` temsilcisi çağrılır ve _tehdit_ve sonra iç kilidine ulaşır ve bu nedenle yeni anahtar-değer çifti sözlüğe eklenir.

1. _threada 'un_ Kullanıcı temsilcisi tamamlanır ve iş parçacığı kilidine ulaşır, ancak artık öğenin zaten var olduğunu görür.

1. _Threada_ "Get" gerçekleştirir ve _threadb_tarafından daha önce eklenen verileri döndürür.

Bu nedenle, tarafından <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> döndürülen verilerin iş parçacığı tarafından oluşturulan verilerle aynı olduğu garanti edilmez. `valueFactory` Çağrıldığında benzer bir olay sırası oluşabilir <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı güvenli Koleksiyonlar](../../../../docs/standard/collections/thread-safe/index.md)
