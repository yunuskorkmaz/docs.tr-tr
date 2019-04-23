---
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f82e347ecdb3c69cee3749855d1e4cb457a460f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112963"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="8d4db-102">Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="8d4db-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="8d4db-103">Geciktirilmiş yüklemeyi ayarlayarak kapatabilirsiniz <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="8d4db-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="8d4db-104">Daha fazla bilgi için [Ertelenen hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="8d4db-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d4db-105">Ertelenen yükleme izleme nesnesi kapalı olduğunda dolaylı kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d4db-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="8d4db-106">Daha fazla bilgi için [nasıl yapılır: Salt okunur olarak bilgileri almak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="8d4db-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d4db-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d4db-107">Example</span></span>  
 <span data-ttu-id="8d4db-108">Aşağıdaki örnek, geciktirilmiş yüklemeyi ayarlayarak kapatma işlemi gösterilmektedir <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="8d4db-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8d4db-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d4db-109">See also</span></span>

- [<span data-ttu-id="8d4db-110">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="8d4db-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="8d4db-111">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="8d4db-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
