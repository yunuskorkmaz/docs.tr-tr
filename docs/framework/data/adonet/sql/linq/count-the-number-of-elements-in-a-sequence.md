---
title: "Bir dizi öğelerin sayısı"
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
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 060dec47169adccee10477e1c01d7afb02ab0973
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Bir dizi öğelerin sayısı
Kullanım <xref:System.Linq.Enumerable.Count%2A> işleci dizisindeki öğelerin sayısı.  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırmak üretir çıktısı `91`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sayısını sayar `Customers` veritabanındaki.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek veritabanındaki değil sonlandırdıktan ürün sayısını sayar.  
  
 Bu örnek Northwind örnek veritabanı karşı çalıştırmak üretir çıktısı `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Toplama sorguları](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
