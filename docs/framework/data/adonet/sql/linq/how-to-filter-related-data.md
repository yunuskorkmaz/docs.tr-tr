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
# <a name="how-to-filter-related-data"></a>Nasıl yapılır: İlgili verileri filtreleme
Kullanım <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> alınan veri miktarını sınırlamak için alt sorgularda belirtmek için yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi sınırları `Orders` bugün sevk edilmiş değil o alınır. Bu yaklaşım olmadan tüm `Orders` yalnızca bir alt istenen olsa bile alınan.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
