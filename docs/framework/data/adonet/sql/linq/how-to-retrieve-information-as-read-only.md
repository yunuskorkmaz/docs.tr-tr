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
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="c8e8a-102">Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="c8e8a-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="c8e8a-103">Verileri değiştirmeyi düşünmüyorsanız, salt okuma sonuçları girerek sorguların performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e8a-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="c8e8a-104">Öğesini olarak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> `false`ayarlayarak salt okuma işlemini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e8a-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8e8a-105">, Olarak `false`ayarlandığında, örtük<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> olarak olarak ayarlanır. `false` <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A></span><span class="sxs-lookup"><span data-stu-id="c8e8a-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8e8a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8e8a-106">Example</span></span>  
 <span data-ttu-id="c8e8a-107">Aşağıdaki kod, çalışan işe alma tarihlerinin salt okunurdur bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="c8e8a-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c8e8a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e8a-108">See also</span></span>

- [<span data-ttu-id="c8e8a-109">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="c8e8a-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="c8e8a-110">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="c8e8a-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [<span data-ttu-id="c8e8a-111">Ertelenmiş ve Hemen Yükleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="c8e8a-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
