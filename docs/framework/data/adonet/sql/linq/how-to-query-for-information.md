---
title: 'Nasıl yapılır: Bilgi Sorgulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166410"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="02de2-102">Nasıl yapılır: Bilgi Sorgulama</span><span class="sxs-lookup"><span data-stu-id="02de2-102">How to: Query for Information</span></span>

<span data-ttu-id="02de2-103">İçindeki sorgular [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] LINQ içindeki sorgularla aynı sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="02de2-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="02de2-104">Tek fark, sorgularda başvurulan nesnelerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veritabanındaki öğelerle eşlendiğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="02de2-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="02de2-105">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="02de2-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="02de2-106">yazdığınız sorguları eşdeğer SQL sorgularına çevirir ve işlenmek üzere sunucuya gönderir.</span><span class="sxs-lookup"><span data-stu-id="02de2-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="02de2-107">LINQ sorgularının bazı özelliklerinin uygulamalarda özel ilgilenilmesi gerekebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="02de2-107">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="02de2-108">Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="02de2-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02de2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="02de2-109">Example</span></span>  

 <span data-ttu-id="02de2-110">Aşağıdaki sorgu, Londra 'dan müşterilerin bir listesini ister.</span><span class="sxs-lookup"><span data-stu-id="02de2-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="02de2-111">Bu örnekte, `Customers` Northwind örnek veritabanındaki bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="02de2-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="02de2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02de2-112">See also</span></span>

- [<span data-ttu-id="02de2-113">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02de2-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="02de2-114">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="02de2-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="02de2-115">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="02de2-115">Querying the Database</span></span>](querying-the-database.md)
