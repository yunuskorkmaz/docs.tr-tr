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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e5c17d0cfa4fed33c2648173002e5ee1bdcc2c15
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="b0231-102">Nasıl yapılır: yükleme ertelenmiş Kapat</span><span class="sxs-lookup"><span data-stu-id="b0231-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="b0231-103">Ayarlayarak yüklenirken ertelenmiş kapatabilirsiniz <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="b0231-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="b0231-104">Daha fazla bilgi için bkz: [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="b0231-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0231-105">İzleme nesnesi devre dışı bırakıldığında dolaylı Ertelenen yükleme devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b0231-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="b0231-106">Daha fazla bilgi için bkz: [nasıl yapılır: olarak bilgi almak Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="b0231-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0231-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0231-107">Example</span></span>  
 <span data-ttu-id="b0231-108">Aşağıdaki örnek ayarlayarak yüklenirken ertelenmiş devre dışı bırakmak gösterilmiştir <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="b0231-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b0231-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0231-109">See Also</span></span>  
 [<span data-ttu-id="b0231-110">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="b0231-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="b0231-111">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="b0231-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
