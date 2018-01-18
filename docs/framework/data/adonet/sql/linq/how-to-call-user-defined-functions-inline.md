---
title: "Nasıl yapılır: çağrı kullanıcı tanımlı işlevler satır içi"
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
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f84d6c2c75844ab265259339ed8f72e42419f63a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-user-defined-functions-inline"></a>Nasıl yapılır: çağrı kullanıcı tanımlı işlevler satır içi
Kullanıcı tanımlı işlevler satır içi çağırabilirsiniz olsa da, sorgu yürütülür kadar yürütme ertelenmiş sorguda içerdiği işlevleri yürütülmez. Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Aynı işlevin bir sorgu dışında çağırdığınızda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yöntemi çağrısı ifadesinden basit bir sorgu oluşturur. SQL söz dizimi aşağıdaki gibidir (parametre `@p0` geçirilen sabiti bağlı):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki oluşturur:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu için oluşturulan kullanıcı tanımlı işlev yöntemini çağırın satır içi görebilirsiniz `ReverseCustName`. Sorgu yürütme ertelenmiş çünkü işlev hemen yürütülemiyor. SQL veritabanındaki kullanıcı tanımlı işlev çağrısı için bu sorguyu çevirir için oluşturulmuş (sorgu aşağıdaki SQL kodunu bakın).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
