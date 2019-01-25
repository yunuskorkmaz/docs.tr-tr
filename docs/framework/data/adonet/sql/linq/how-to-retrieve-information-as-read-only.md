---
title: 'Nasıl yapılır: Salt okunur olarak bilgileri alınamıyor'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 8b83a77adb02cc2bcc01b274867143887114bb1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669555"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Nasıl yapılır: Salt okunur olarak bilgileri alınamıyor
Verileri değiştirmek istemediğiniz zaman, salt okunur sonuçları arayan tarafından sorguların performansını artırabilirsiniz.  
  
 Salt okunur işleme ayarlayarak uygulamak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> için `false`.  
  
> [!NOTE]
>  Zaman <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlanır `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> örtük olarak ayarlandığında `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, çalışan işe alma tarihleri salt okunur bir koleksiyonunu alır.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [Ertelenmiş ve Hemen Yükleme Karşılaştırması](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
