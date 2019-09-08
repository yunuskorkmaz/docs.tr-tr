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
# <a name="how-to-filter-related-data"></a>Nasıl yapılır: İlgili Verileri Filtreleme
Alınan veri miktarını sınırlamak için alt sorgular belirtmek üzere yönteminikullanın.<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi bugün gönderilmemişse, `Orders` alınan ' ı kısıtlar. Bu yaklaşım olmadan, yalnızca `Orders` bir alt küme istendiği halde tüm bunlar alınır.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanını Sorgulama](querying-the-database.md)
