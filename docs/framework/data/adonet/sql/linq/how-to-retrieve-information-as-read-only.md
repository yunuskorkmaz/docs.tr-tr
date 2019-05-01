---
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 131562e9ee0fbfde8c94f580bcb6d452918f42ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037589"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="dc48a-102">Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="dc48a-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="dc48a-103">Verileri değiştirmek istemediğiniz zaman, salt okunur sonuçları arayan tarafından sorguların performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc48a-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="dc48a-104">Salt okunur işleme ayarlayarak uygulamak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="dc48a-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc48a-105">Zaman <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlanır `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> örtük olarak ayarlandığında `false`.</span><span class="sxs-lookup"><span data-stu-id="dc48a-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc48a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc48a-106">Example</span></span>  
 <span data-ttu-id="dc48a-107">Aşağıdaki kod, çalışan işe alma tarihleri salt okunur bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="dc48a-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dc48a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc48a-108">See also</span></span>

- [<span data-ttu-id="dc48a-109">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="dc48a-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="dc48a-110">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="dc48a-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [<span data-ttu-id="dc48a-111">Ertelenmiş ve Hemen Yükleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="dc48a-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
