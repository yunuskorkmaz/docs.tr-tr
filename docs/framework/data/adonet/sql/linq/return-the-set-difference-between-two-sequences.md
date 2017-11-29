---
title: "İki sıraları arasında ayarlanmış farkı döndürür"
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
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a3dae34f2b5904312fa3fcd994a01b2e024f1970
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-set-difference-between-two-sequences"></a>İki sıraları arasında ayarlanmış farkı döndürür
Kullanım <xref:System.Linq.Queryable.Except%2A> iki sıraları arasında ayarlanmış farkı döndürülecek işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Except%2A> tüm ülkelerde bir dizi içinde dönmek için `Customers` hangi Hayır, Canlı ancak `Employees` Canlı.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemi yalnızca kümeleri üzerinde iyi tanımlanmış. Multisets anlamları tanımlanmamıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Standart sorgu işleci çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
