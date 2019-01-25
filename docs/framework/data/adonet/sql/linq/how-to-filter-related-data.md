---
title: 'Nasıl yapılır: İlgili verileri filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 9a046c94363a1a161e19dcb68e015f8c6791e511
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703477"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="08fe4-102">Nasıl yapılır: İlgili verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="08fe4-102">How to: Filter Related Data</span></span>
<span data-ttu-id="08fe4-103">Kullanım <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> alınan veri miktarını sınırlamak için alt sorgularda belirtmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08fe4-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08fe4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="08fe4-104">Example</span></span>  
 <span data-ttu-id="08fe4-105">Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi sınırları `Orders` bugün sevk edilmiş değil o alınır.</span><span class="sxs-lookup"><span data-stu-id="08fe4-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="08fe4-106">Bu yaklaşım olmadan tüm `Orders` yalnızca bir alt istenen olsa bile alınan.</span><span class="sxs-lookup"><span data-stu-id="08fe4-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="08fe4-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08fe4-107">See also</span></span>
- [<span data-ttu-id="08fe4-108">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="08fe4-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
