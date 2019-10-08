---
title: 'Nasıl yapılır: Kullanıcı tanımlı Işlevleri satır Içinde çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 01ba9ab4359cbd124b2207c87d5dae904641911a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002991"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Nasıl yapılır: Kullanıcı tanımlı Işlevleri satır Içinde çağırma
Kullanıcı tanımlı işlevleri satır içi olarak çağırabilseniz de, yürütme geciktirilen bir sorguda bulunan işlevler sorgu yürütülene kadar yürütülmez. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Aynı işlevi bir sorgu dışında çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Yöntem çağırma ifadesinden basit bir sorgu oluşturur. Aşağıdaki SQL sözdizimidir (`@p0` parametresi geçilen sabite bağlanır):  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdakileri oluşturur:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgusunda, oluşturulan kullanıcı tanımlı işlev metoduna `ReverseCustName` için bir satır içi çağrı görebilirsiniz. Sorgu yürütmesi ertelenmesi nedeniyle işlev hemen yürütülmedi. Bu sorgu için oluşturulan SQL, veritabanında kullanıcı tanımlı işleve bir çağrı yapar (sorguyu izleyen SQL koduna bakın).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı Tanımlı İşlevler](user-defined-functions.md)
