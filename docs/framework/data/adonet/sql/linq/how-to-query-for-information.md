---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bilgi sorgula'
title: 'Nasıl yapılır: Bilgi Sorgulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 41774834fe919b28d71691203941cb8e0a8a0397
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802027"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="c955a-103">Nasıl yapılır: Bilgi Sorgulama</span><span class="sxs-lookup"><span data-stu-id="c955a-103">How to: Query for Information</span></span>

<span data-ttu-id="c955a-104">İçindeki sorgular [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] LINQ içindeki sorgularla aynı sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c955a-104">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="c955a-105">Tek fark, sorgularda başvurulan nesnelerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veritabanındaki öğelerle eşlendiğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c955a-105">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="c955a-106">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="c955a-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c955a-107">yazdığınız sorguları eşdeğer SQL sorgularına çevirir ve işlenmek üzere sunucuya gönderir.</span><span class="sxs-lookup"><span data-stu-id="c955a-107">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="c955a-108">LINQ sorgularının bazı özelliklerinin uygulamalarda özel ilgilenilmesi gerekebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c955a-108">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="c955a-109">Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="c955a-109">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c955a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c955a-110">Example</span></span>  

 <span data-ttu-id="c955a-111">Aşağıdaki sorgu, Londra 'dan müşterilerin bir listesini ister.</span><span class="sxs-lookup"><span data-stu-id="c955a-111">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="c955a-112">Bu örnekte, `Customers` Northwind örnek veritabanındaki bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="c955a-112">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c955a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c955a-113">See also</span></span>

- [<span data-ttu-id="c955a-114">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c955a-114">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="c955a-115">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="c955a-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="c955a-116">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="c955a-116">Querying the Database</span></span>](querying-the-database.md)
