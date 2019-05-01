---
title: 'Nasıl yapılır: İlgili Verileri Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 3dbedfb7065ac4b1a570a3f6cdbcdcc2177f20cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037797"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="5703b-102">Nasıl yapılır: İlgili Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="5703b-102">How to: Filter Related Data</span></span>
<span data-ttu-id="5703b-103">Kullanım <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> alınan veri miktarını sınırlamak için alt sorgularda belirtmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5703b-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5703b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5703b-104">Example</span></span>  
 <span data-ttu-id="5703b-105">Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi sınırları `Orders` bugün sevk edilmiş değil o alınır.</span><span class="sxs-lookup"><span data-stu-id="5703b-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="5703b-106">Bu yaklaşım olmadan tüm `Orders` yalnızca bir alt istenen olsa bile alınan.</span><span class="sxs-lookup"><span data-stu-id="5703b-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5703b-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5703b-107">See also</span></span>

- [<span data-ttu-id="5703b-108">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="5703b-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
