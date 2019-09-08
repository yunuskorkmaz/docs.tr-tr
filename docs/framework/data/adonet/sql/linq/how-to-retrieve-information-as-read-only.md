---
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 399bf44ef5536a9adebf1cad590439741df998f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793321"
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

- [Sorgu Kavramları](query-concepts.md)
- [Veritabanını Sorgulama](querying-the-database.md)
- [Ertelenmiş ve Hemen Yükleme Karşılaştırması](deferred-versus-immediate-loading.md)
