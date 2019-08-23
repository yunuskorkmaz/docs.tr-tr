---
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938684"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="e6b2f-102">Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="e6b2f-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="e6b2f-103">Giderek ertelenmiş yüklemeyi <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6b2f-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="e6b2f-104">Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e6b2f-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6b2f-105">Ertelenmiş yükleme, nesne izleme kapalıyken etkili bir şekilde kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6b2f-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="e6b2f-106">Daha fazla bilgi için [nasıl yapılır: Bilgileri salt okuma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)olarak alın.</span><span class="sxs-lookup"><span data-stu-id="e6b2f-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b2f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6b2f-107">Example</span></span>  
 <span data-ttu-id="e6b2f-108">Aşağıdaki örnek, ' i ' ye <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`ayarlayarak ertelenmiş yüklemenin nasıl kapatılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e6b2f-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b2f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b2f-109">See also</span></span>

- [<span data-ttu-id="e6b2f-110">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="e6b2f-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="e6b2f-111">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="e6b2f-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
