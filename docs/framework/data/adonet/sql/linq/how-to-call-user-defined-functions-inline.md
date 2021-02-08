---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: User-Defined Işlevleri satır Içi çağırma'
title: 'Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 2a7cf185af05a1ed58a2dd3b365a5bbcaa2a4fd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786062"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="105f3-103">Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="105f3-103">How to: Call User-Defined Functions Inline</span></span>

<span data-ttu-id="105f3-104">Kullanıcı tanımlı işlevleri satır içi olarak çağırabilseniz de, yürütme geciktirilen bir sorguda bulunan işlevler sorgu yürütülene kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="105f3-104">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="105f3-105">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="105f3-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="105f3-106">Aynı işlevi bir sorgu dışında çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Yöntem çağırma ifadesinden basit bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="105f3-106">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="105f3-107">Aşağıdaki SQL sözdizimidir (parametresi `@p0` geçilen sabite bağlanır):</span><span class="sxs-lookup"><span data-stu-id="105f3-107">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="105f3-108">aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="105f3-108">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="105f3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="105f3-109">Example</span></span>  

 <span data-ttu-id="105f3-110">Aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguda, oluşturulan kullanıcı tanımlı işlev yöntemine ait bir satır içi çağrı görebilirsiniz `ReverseCustName` .</span><span class="sxs-lookup"><span data-stu-id="105f3-110">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="105f3-111">Sorgu yürütmesi ertelenmesi nedeniyle işlev hemen yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="105f3-111">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="105f3-112">Bu sorgu için oluşturulan SQL, veritabanında kullanıcı tanımlı işleve bir çağrı yapar (sorguyu izleyen SQL koduna bakın).</span><span class="sxs-lookup"><span data-stu-id="105f3-112">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="105f3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="105f3-113">See also</span></span>

- [<span data-ttu-id="105f3-114">Kullanıcı tanımlı Işlevler</span><span class="sxs-lookup"><span data-stu-id="105f3-114">User-Defined Functions</span></span>](user-defined-functions.md)
