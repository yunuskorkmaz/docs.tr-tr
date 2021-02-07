---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bilgileri Read-Only olarak alma'
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 7743e555bcc3f6371ca601d02313e30895e57961
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723458"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma

Verileri değiştirmeyi düşünmüyorsanız, salt okuma sonuçları girerek sorguların performansını artırabilirsiniz.  
  
 Öğesini olarak ayarlayarak salt okuma işlemini uygulayabilirsiniz <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> `false` .  
  
> [!NOTE]
> , Olarak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlandığında `false` , örtük olarak <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> olarak ayarlanır `false` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, çalışan işe alma tarihlerinin salt okunurdur bir koleksiyonunu alır.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
- [Veritabanını Sorgulama](querying-the-database.md)
- [Ertelenmiş ve Hemen Yükleme Karşılaştırması](deferred-versus-immediate-loading.md)
