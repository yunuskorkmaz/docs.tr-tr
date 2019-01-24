---
title: 'Nasıl yapılır: Bilgi sorgulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 9476144d84454aedc331214a55c77547697c378f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608420"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="071bf-102">Nasıl yapılır: Bilgi sorgulama</span><span class="sxs-lookup"><span data-stu-id="071bf-102">How to: Query for Information</span></span>
<span data-ttu-id="071bf-103">Sorgulara [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularda olarak aynı sözdizimini kullanır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="071bf-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="071bf-104">Nesneler, başvurulan tek fark, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları bir veritabanında öğelerine eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="071bf-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="071bf-105">Daha fazla bilgi için [(C#) LINQ sorgularına giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="071bf-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="071bf-106">eşdeğer SQL sorguları yazma sorguları çevirir ve işlem sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="071bf-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="071bf-107">Bazı özellikleri [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorguları özel dikkat ihtiyaç duyabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="071bf-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="071bf-108">Daha fazla bilgi için [sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="071bf-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="071bf-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="071bf-109">Example</span></span>  
 <span data-ttu-id="071bf-110">Londralı müşteriler listesi için aşağıdaki sorguyu ister.</span><span class="sxs-lookup"><span data-stu-id="071bf-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="071bf-111">Bu örnekte, `Customers` Northwind örnek veritabanındaki bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="071bf-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="071bf-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="071bf-112">See also</span></span>
- [<span data-ttu-id="071bf-113">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="071bf-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="071bf-114">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="071bf-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="071bf-115">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="071bf-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
