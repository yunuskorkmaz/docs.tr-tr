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
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="b5f29-102">Nasıl yapılır: Salt okunur olarak bilgileri alınamıyor</span><span class="sxs-lookup"><span data-stu-id="b5f29-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="b5f29-103">Verileri değiştirmek istemediğiniz zaman, salt okunur sonuçları arayan tarafından sorguların performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5f29-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="b5f29-104">Salt okunur işleme ayarlayarak uygulamak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="b5f29-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5f29-105">Zaman <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlanır `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> örtük olarak ayarlandığında `false`.</span><span class="sxs-lookup"><span data-stu-id="b5f29-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5f29-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5f29-106">Example</span></span>  
 <span data-ttu-id="b5f29-107">Aşağıdaki kod, çalışan işe alma tarihleri salt okunur bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="b5f29-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b5f29-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5f29-108">See also</span></span>
- [<span data-ttu-id="b5f29-109">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="b5f29-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="b5f29-110">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="b5f29-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [<span data-ttu-id="b5f29-111">Ertelenmiş ve Hemen Yükleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="b5f29-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
