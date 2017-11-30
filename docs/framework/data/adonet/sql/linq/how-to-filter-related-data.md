---
title: "Nasıl yapılır: ilgili veri filtreleme"
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
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f02b09cc5389a90ea42a0dd851579327972c20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="a52a2-102">Nasıl yapılır: ilgili veri filtreleme</span><span class="sxs-lookup"><span data-stu-id="a52a2-102">How to: Filter Related Data</span></span>
<span data-ttu-id="a52a2-103">Kullanım <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi miktarını sınırlamak için alt sorgularda belirtmek için veri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="a52a2-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a52a2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a52a2-104">Example</span></span>  
 <span data-ttu-id="a52a2-105">Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi sınırları `Orders` bugün sevk edilmiş değil o alınır.</span><span class="sxs-lookup"><span data-stu-id="a52a2-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="a52a2-106">Bu yaklaşım olmadan tüm `Orders` yalnızca bir alt istenen olsa bile alınan.</span><span class="sxs-lookup"><span data-stu-id="a52a2-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a52a2-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a52a2-107">See Also</span></span>  
 [<span data-ttu-id="a52a2-108">Veritabanı sorgulama</span><span class="sxs-lookup"><span data-stu-id="a52a2-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
