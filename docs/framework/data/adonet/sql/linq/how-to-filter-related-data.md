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
# <a name="how-to-filter-related-data"></a>Nasıl yapılır: İlgili Verileri Filtreleme

<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A>Alınan veri miktarını sınırlamak için alt sorgular belirtmek üzere yöntemini kullanın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi `Orders` bugün gönderilmemişse, alınan ' ı kısıtlar. Bu yaklaşım olmadan, `Orders` yalnızca bir alt küme istendiği halde tüm bunlar alınır.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanını Sorgulama](querying-the-database.md)
