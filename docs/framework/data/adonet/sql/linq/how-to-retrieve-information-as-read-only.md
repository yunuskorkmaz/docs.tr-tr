---
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 131562e9ee0fbfde8c94f580bcb6d452918f42ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148986"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma
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
