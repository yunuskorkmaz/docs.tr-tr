---
title: "Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma"
description: .NET 'teki ConcurrentDictionary<TKey, TValue> Collection sınıfında öğe ekleme, alma, güncelleştirme ve kaldırma hakkında bir örnek okuyun.
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 827eb9db984289929c591046a4713419c9587312
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662868"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma

Bu örnek, bir öğesinden öğe ekleme, alma, güncelleştirme ve kaldırma işlemlerinin nasıl yapılacağını gösterir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> . Bu koleksiyon sınıfı, iş parçacığı güvenli bir uygulama. Birden çok iş parçacığının aynı anda öğelere erişmeye çalıştığı her seferinde kullanmanızı öneririz.

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>, kodun, verileri ekleme veya kaldırma girişiminde bulunulmadan önce bir anahtarın mevcut olup olmadığını kontrol etmek için gerekli hale getirmek üzere çeşitli kolay yöntemler sağlar. Aşağıdaki tabloda bu kullanışlı yöntemler listelenmekte ve ne zaman kullanılacağı açıklanmaktadır.

| Yöntem | Şu durumlarda kullan... |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | Belirtilen anahtar için yeni bir değer eklemek istiyorsunuz ve anahtar zaten varsa, değerini değiştirmek istersiniz. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | Belirtilen bir anahtar için varolan değeri almak istiyorsunuz ve anahtar yoksa anahtar/değer çifti belirtmek istersiniz. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A> | Anahtar/değer çifti eklemek, almak, güncelleştirmek veya kaldırmak, anahtar zaten varsa veya deneme başka bir nedenle başarısız olursa, alternatif bir işlem yapmak istersiniz. |

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Threading.Tasks.Task> bazı öğeleri eşzamanlı olarak eklemek için iki örnek kullanır <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ve sonra öğelerin başarıyla eklendiğini göstermek için tüm içeriği çıkarır. Örnek ayrıca <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> , <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> koleksiyondan öğe eklemek, güncelleştirmek ve almak için,, ve yöntemlerinin nasıl kullanılacağını gösterir.

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>çok iş parçacıklı senaryolar için tasarlanmıştır. Koleksiyonda öğe eklemek veya kaldırmak için kodunuzda kilit kullanmanız gerekmez. Ancak, bir iş parçacığının bir değeri alabilmesi ve aynı anahtara yeni bir değer vererek koleksiyonu hemen güncellemek için başka bir iş parçacığında her zaman mümkündür.

Ayrıca, tüm yöntemleri iş parçacığı açısından güvenli olmasına rağmen, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> tüm yöntemler atomik, özellikle <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> . Bu yöntemlere geçirilen kullanıcı temsilcisi sözlüğün iç kilidi dışında çağrılır (Bu işlem, bilinmeyen kodun tüm iş parçacıklarını engellemesini engellemek için yapılır). Bu nedenle, bu olay sırası oluşması mümkündür:

1. _threada_ çağrısı <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> , hiçbir öğe buluyor ve temsilciyi çağırarak eklenecek yeni bir öğe oluşturuyor `valueFactory` .

1. _Threadb_ <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> eşzamanlı olarak çağrılır, `valueFactory` temsilcisi çağrılır ve _tehdit_ve sonra iç kilidine ulaşır ve bu nedenle yeni anahtar-değer çifti sözlüğe eklenir.

1. _threada 'un_ Kullanıcı temsilcisi tamamlanır ve iş parçacığı kilidine ulaşır, ancak artık öğenin zaten var olduğunu görür.

1. _Threada_ "Get" gerçekleştirir ve _threadb_tarafından daha önce eklenen verileri döndürür.

Bu nedenle, tarafından döndürülen verilerin <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> iş parçacığı tarafından oluşturulan verilerle aynı olduğu garanti edilmez `valueFactory` . Çağrıldığında benzer bir olay sırası oluşabilir <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı güvenli Koleksiyonlar](index.md)
