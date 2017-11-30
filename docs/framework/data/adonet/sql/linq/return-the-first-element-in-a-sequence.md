---
title: "Bir dizisinde ilk öğesini döndürür"
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
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb43e75ae5cf55df87d00f44aa856d353dd25c0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-first-element-in-a-sequence"></a>Bir dizisinde ilk öğesini döndürür
Kullanım <xref:System.Linq.Enumerable.First%2A> işleci bir dizisinde ilk öğesini döndürür. Sorgular kullanan <xref:System.Linq.Enumerable.First%2A> hemen çalıştırılır.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]desteklemediği <xref:System.Linq.Enumerable.Last%2A> işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ilk bulur `Shipper` bir tabloda:  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, sonuçları demektir.  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tek bulur `Customer` olan `CustomerID` BONAP.  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırırsanız, sonuçları olan `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
