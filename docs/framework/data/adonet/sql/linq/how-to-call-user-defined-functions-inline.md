---
title: 'Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: ed8071352902b8f97445cbfa5ff0ebe8fead9bb9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163715"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma
Kullanıcı tanımlı satır içi işlevleri çağırabilir olsa da, sorgu yürütülene kadar olan yürütme ertelenmiştir bir sorguya dahil işlevleri yürütülmez. Daha fazla bilgi için [(C#) LINQ sorgularına giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Bir sorgu dışında aynı işlev çağırdığınızda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yöntemi çağrısı ifadesinden basit bir sorgu oluşturur. SQL sözdizimi verilmiştir (parametre `@p0` geçirilen sabiti bağlıdır):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdakileri oluşturur:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu için oluşturulan kullanıcı tanımlı işlev yöntem çağrısı bir satır içi görebilirsiniz `ReverseCustName`. Sorgu yürütme ertelenmiş çünkü işlevi hemen yürütülmez. SQL veritabanında kullanıcı tanımlı işlev çağrısı için bu sorgu çevirir için yerleşik (sorgu aşağıdaki SQL kodu bakın).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
