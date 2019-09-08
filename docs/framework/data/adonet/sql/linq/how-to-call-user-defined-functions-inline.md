---
title: 'Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: e9808856543e20b8904be812b15b32154eab56e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782116"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="6b0a2-102">Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="6b0a2-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="6b0a2-103">Kullanıcı tanımlı işlevleri satır içi olarak çağırabilseniz de, yürütme geciktirilen bir sorguda bulunan işlevler sorgu yürütülene kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6b0a2-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="6b0a2-104">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="6b0a2-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="6b0a2-105">Aynı işlevi bir sorgu dışında çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Yöntem çağırma ifadesinden basit bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b0a2-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="6b0a2-106">Aşağıdaki SQL sözdizimidir (parametresi `@p0` geçilen sabite bağlanır):</span><span class="sxs-lookup"><span data-stu-id="6b0a2-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6b0a2-107">aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="6b0a2-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="6b0a2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b0a2-108">Example</span></span>  
 <span data-ttu-id="6b0a2-109">Aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguda, oluşturulan kullanıcı tanımlı işlev yöntemine `ReverseCustName`ait bir satır içi çağrı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b0a2-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="6b0a2-110">Sorgu yürütmesi ertelenmesi nedeniyle işlev hemen yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="6b0a2-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="6b0a2-111">Bu sorgu için oluşturulan SQL, veritabanında kullanıcı tanımlı işleve bir çağrı yapar (sorguyu izleyen SQL koduna bakın).</span><span class="sxs-lookup"><span data-stu-id="6b0a2-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b0a2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b0a2-112">See also</span></span>

- [<span data-ttu-id="6b0a2-113">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="6b0a2-113">User-Defined Functions</span></span>](user-defined-functions.md)
