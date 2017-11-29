---
title: "Nasıl yapılır: salt okunur olarak bilgisi alma"
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
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a9765d8d8330c7ad2a6e8cb25166427cdd9414a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="7a9e7-102">Nasıl yapılır: salt okunur olarak bilgisi alma</span><span class="sxs-lookup"><span data-stu-id="7a9e7-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="7a9e7-103">Verileri değiştirmek düşünmüyorsanız, salt okunur sonuçları aramayı tarafından sorguların performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="7a9e7-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="7a9e7-104">Salt okunur işleme ayarlayarak uygulamak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="7a9e7-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a9e7-105">Zaman <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlanır `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> örtük olarak ayarlandığında `false`.</span><span class="sxs-lookup"><span data-stu-id="7a9e7-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a9e7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a9e7-106">Example</span></span>  
 <span data-ttu-id="7a9e7-107">Aşağıdaki kod çalışan işe alma tarihleri salt okunur bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="7a9e7-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7a9e7-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a9e7-108">See Also</span></span>  
 [<span data-ttu-id="7a9e7-109">Sorgu kavramları</span><span class="sxs-lookup"><span data-stu-id="7a9e7-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="7a9e7-110">Veritabanı sorgulama</span><span class="sxs-lookup"><span data-stu-id="7a9e7-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [<span data-ttu-id="7a9e7-111">Ertelenmiş karşı hemen yükleniyor</span><span class="sxs-lookup"><span data-stu-id="7a9e7-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
