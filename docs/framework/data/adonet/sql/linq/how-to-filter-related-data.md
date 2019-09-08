---
title: 'Nasıl yapılır: İlgili Verileri Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e8e63c139f38d6de46390925428e18682a65818d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793597"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="e1730-102">Nasıl yapılır: İlgili Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="e1730-102">How to: Filter Related Data</span></span>
<span data-ttu-id="e1730-103">Alınan veri miktarını sınırlamak için alt sorgular belirtmek üzere yönteminikullanın.<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A></span><span class="sxs-lookup"><span data-stu-id="e1730-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1730-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1730-104">Example</span></span>  
 <span data-ttu-id="e1730-105">Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi bugün gönderilmemişse, `Orders` alınan ' ı kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="e1730-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="e1730-106">Bu yaklaşım olmadan, yalnızca `Orders` bir alt küme istendiği halde tüm bunlar alınır.</span><span class="sxs-lookup"><span data-stu-id="e1730-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e1730-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1730-107">See also</span></span>

- [<span data-ttu-id="e1730-108">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="e1730-108">Querying the Database</span></span>](querying-the-database.md)
