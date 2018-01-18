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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 120cc6d08d02fd33510903242c44feae3f8ec5c0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="return-the-set-difference-between-two-sequences"></a>İki sıraları arasında ayarlanmış farkı döndürür
Kullanım <xref:System.Linq.Queryable.Except%2A> iki sıraları arasında ayarlanmış farkı döndürülecek işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Except%2A> tüm ülkelerde bir dizi içinde dönmek için `Customers` hangi Hayır, Canlı ancak `Employees` Canlı.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemi yalnızca kümeleri üzerinde iyi tanımlanmış. Multisets anlamları tanımlanmamıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
