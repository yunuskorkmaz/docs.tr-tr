---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Ilgili verileri filtreleme'
title: 'Nasıl yapılır: İlgili Verileri Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: d44e0805b82c0c58f9ee19808e078f9f9b337050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738956"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="fb82e-103">Nasıl yapılır: İlgili Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="fb82e-103">How to: Filter Related Data</span></span>

<span data-ttu-id="fb82e-104"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A>Alınan veri miktarını sınırlamak için alt sorgular belirtmek üzere yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fb82e-104">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb82e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb82e-105">Example</span></span>  

 <span data-ttu-id="fb82e-106">Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi `Orders` bugün gönderilmemişse, alınan ' ı kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="fb82e-106">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="fb82e-107">Bu yaklaşım olmadan, `Orders` yalnızca bir alt küme istendiği halde tüm bunlar alınır.</span><span class="sxs-lookup"><span data-stu-id="fb82e-107">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fb82e-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb82e-108">See also</span></span>

- [<span data-ttu-id="fb82e-109">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="fb82e-109">Querying the Database</span></span>](querying-the-database.md)
