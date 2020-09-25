---
title: 'Nasıl yapılır: İlgili Verileri Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e12bab55b03fac3383b98b8ee1c56ab1954ff978
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173464"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="ef5a1-102">Nasıl yapılır: İlgili Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="ef5a1-102">How to: Filter Related Data</span></span>

<span data-ttu-id="ef5a1-103"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A>Alınan veri miktarını sınırlamak için alt sorgular belirtmek üzere yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef5a1-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef5a1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef5a1-104">Example</span></span>  

 <span data-ttu-id="ef5a1-105">Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi `Orders` bugün gönderilmemişse, alınan ' ı kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="ef5a1-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="ef5a1-106">Bu yaklaşım olmadan, `Orders` yalnızca bir alt küme istendiği halde tüm bunlar alınır.</span><span class="sxs-lookup"><span data-stu-id="ef5a1-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ef5a1-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef5a1-107">See also</span></span>

- [<span data-ttu-id="ef5a1-108">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="ef5a1-108">Querying the Database</span></span>](querying-the-database.md)
