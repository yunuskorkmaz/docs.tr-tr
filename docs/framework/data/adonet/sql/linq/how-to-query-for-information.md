---
title: "Nasıl yapılır: sorgu için bilgi"
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
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 55ef74cecf5a3669662e5fe189aea88b7d912344
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="97db2-102">Nasıl yapılır: sorgu için bilgi</span><span class="sxs-lookup"><span data-stu-id="97db2-102">How to: Query for Information</span></span>
<span data-ttu-id="97db2-103">İçindeki sorgular [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularda olarak aynı sözdizimini kullanır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97db2-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="97db2-104">Yalnızca farktır nesneleri içinde başvurulan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları bir veritabanında öğelerine eşlendi.</span><span class="sxs-lookup"><span data-stu-id="97db2-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="97db2-105">Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="97db2-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97db2-106">eşdeğer SQL sorguları yazma sorguları çevirir ve işlem sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="97db2-106"> translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="97db2-107">Bazı özellikleri [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorguları özel dikkat gerekebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="97db2-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="97db2-108">Daha fazla bilgi için bkz: [sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="97db2-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97db2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="97db2-109">Example</span></span>  
 <span data-ttu-id="97db2-110">Londra müşterilerden listesi için aşağıdaki sorguyu sorar.</span><span class="sxs-lookup"><span data-stu-id="97db2-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="97db2-111">Bu örnekte, `Customers` Northwind örnek veritabanı tablosunda vardır.</span><span class="sxs-lookup"><span data-stu-id="97db2-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97db2-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97db2-112">See Also</span></span>  
 [<span data-ttu-id="97db2-113">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="97db2-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="97db2-114">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="97db2-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="97db2-115">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="97db2-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
