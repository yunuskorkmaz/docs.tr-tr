---
title: "Nasıl yapılır: yükleme ertelenmiş Kapat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d98b190ef4454ff29318eb6ef0f20624c85b62a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="dde29-102">Nasıl yapılır: yükleme ertelenmiş Kapat</span><span class="sxs-lookup"><span data-stu-id="dde29-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="dde29-103">Ayarlayarak yüklenirken ertelenmiş kapatabilirsiniz <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="dde29-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="dde29-104">Daha fazla bilgi için bkz: [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="dde29-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dde29-105">İzleme nesnesi devre dışı bırakıldığında dolaylı Ertelenen yükleme devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="dde29-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="dde29-106">Daha fazla bilgi için bkz: [nasıl yapılır: olarak bilgi almak Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="dde29-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde29-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="dde29-107">Example</span></span>  
 <span data-ttu-id="dde29-108">Aşağıdaki örnek ayarlayarak yüklenirken ertelenmiş devre dışı bırakmak gösterilmiştir <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="dde29-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="dde29-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dde29-109">See Also</span></span>  
 [<span data-ttu-id="dde29-110">Sorgu kavramları</span><span class="sxs-lookup"><span data-stu-id="dde29-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="dde29-111">Veritabanı sorgulama</span><span class="sxs-lookup"><span data-stu-id="dde29-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
