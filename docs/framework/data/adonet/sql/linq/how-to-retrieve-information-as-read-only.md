---
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: b98c5e6ea49695015eb566ca2176b23c5260017a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928706"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma
Verileri değiştirmeyi düşünmüyorsanız, salt okuma sonuçları girerek sorguların performansını artırabilirsiniz.  
  
 Öğesini olarak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> `false`ayarlayarak salt okuma işlemini uygulayabilirsiniz.  
  
> [!NOTE]
> , Olarak `false`ayarlandığında, örtük<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> olarak olarak ayarlanır. `false` <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, çalışan işe alma tarihlerinin salt okunurdur bir koleksiyonunu alır.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [Ertelenmiş ve Hemen Yükleme Karşılaştırması](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
