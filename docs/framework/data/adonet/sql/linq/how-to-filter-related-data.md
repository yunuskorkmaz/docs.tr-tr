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
ms.workload: dotnet
ms.openlocfilehash: 9d51ac97611379cc6c47ef698bc635bbf46d1e5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-related-data"></a>Nasıl yapılır: ilgili veri filtreleme
Kullanım <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi miktarını sınırlamak için alt sorgularda belirtmek için veri alınamadı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> yöntemi sınırları `Orders` bugün sevk edilmiş değil o alınır. Bu yaklaşım olmadan tüm `Orders` yalnızca bir alt istenen olsa bile alınan.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
