---
title: 'Nasıl yapılır: Kullanıcı tanımlı satır içi işlevleri çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 76a41ded52ac29b4a8b597188171333a888be5cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692775"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="81bd4-102">Nasıl yapılır: Kullanıcı tanımlı satır içi işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="81bd4-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="81bd4-103">Kullanıcı tanımlı satır içi işlevleri çağırabilir olsa da, sorgu yürütülene kadar olan yürütme ertelenmiştir bir sorguya dahil işlevleri yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="81bd4-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="81bd4-104">Daha fazla bilgi için [(C#) LINQ sorgularına giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="81bd4-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="81bd4-105">Bir sorgu dışında aynı işlev çağırdığınızda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yöntemi çağrısı ifadesinden basit bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81bd4-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="81bd4-106">SQL sözdizimi verilmiştir (parametre `@p0` geçirilen sabiti bağlıdır):</span><span class="sxs-lookup"><span data-stu-id="81bd4-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="81bd4-107">aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="81bd4-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="81bd4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="81bd4-108">Example</span></span>  
 <span data-ttu-id="81bd4-109">Aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu için oluşturulan kullanıcı tanımlı işlev yöntem çağrısı bir satır içi görebilirsiniz `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="81bd4-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="81bd4-110">Sorgu yürütme ertelenmiş çünkü işlevi hemen yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="81bd4-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="81bd4-111">SQL veritabanında kullanıcı tanımlı işlev çağrısı için bu sorgu çevirir için yerleşik (sorgu aşağıdaki SQL kodu bakın).</span><span class="sxs-lookup"><span data-stu-id="81bd4-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="81bd4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81bd4-112">See also</span></span>
- [<span data-ttu-id="81bd4-113">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="81bd4-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
