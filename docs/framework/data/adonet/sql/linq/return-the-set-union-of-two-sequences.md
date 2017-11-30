---
title: "İki sıraları kümesi birleşimini döndürür"
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
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 865aa82ebc119a3952124a93f9042c2732e3ab48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-set-union-of-two-sequences"></a>İki sıraları kümesi birleşimini döndürür
Kullanım <xref:System.Linq.Queryable.Union%2A> iki sıraları kümesi birleşimi döndürülecek işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Union%2A> tüm ülkelerde, vardır ya da bir dizi döndürülecek `Customers` veya `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> işleci için multisets multisets sırasız birleştirme tanımlanır (sonucu etkili bir şekilde `UNION ALL` SQL yan tümcesinde).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Standart sorgu işleci çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
