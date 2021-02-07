---
description: 'Daha fazla bilgi edinin: Işlemler ve eşzamanlılık'
title: İşlemler ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c77b9abc72ae662eec76fc40a9856ad73f000c27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766770"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="822d3-103">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="822d3-103">Transactions and Concurrency</span></span>

<span data-ttu-id="822d3-104">Bir işlem, paket olarak yürütülen tek bir komuttan veya bir komut grubundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="822d3-104">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="822d3-105">İşlemler, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="822d3-105">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="822d3-106">İşlemdeki bir noktada bir hata oluşursa, tüm güncelleştirmeler ön işlem durumuna geri alınabilir.</span><span class="sxs-lookup"><span data-stu-id="822d3-106">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="822d3-107">Veri tutarlılığını güvence altına almak için bir işlemin ACID özelliklerine (kararlılık, tutarlılık, yalıtım ve dayanıklılık) uyması gerekir.</span><span class="sxs-lookup"><span data-stu-id="822d3-107">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="822d3-108">Microsoft SQL Server gibi çoğu ilişkisel veritabanı sistemi, bir istemci uygulaması bir güncelleştirme, ekleme veya silme işlemi gerçekleştirdiğinde kilitleme, günlüğe kaydetme ve işlem yönetimi olanakları sağlayarak işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="822d3-108">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="822d3-109">Kilitler çok uzun tutuluyorsa birden çok kaynağı içeren işlemler eşzamanlılık daha düşük olabilir.</span><span class="sxs-lookup"><span data-stu-id="822d3-109">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="822d3-110">Bu nedenle, işlemleri mümkün olduğunca kısa tutun.</span><span class="sxs-lookup"><span data-stu-id="822d3-110">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="822d3-111">Bir işlem aynı veritabanı veya sunucuda birden çok tablo içeriyorsa, saklı yordamlardaki açık işlemler genellikle daha iyi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="822d3-111">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="822d3-112">Transact-SQL `BEGIN TRANSACTION` , `COMMIT TRANSACTION` , ve deyimlerini kullanarak SQL Server saklı yordamda işlem oluşturabilirsiniz `ROLLBACK TRANSACTION` .</span><span class="sxs-lookup"><span data-stu-id="822d3-112">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="822d3-113">Daha fazla bilgi için bkz. Books Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="822d3-113">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="822d3-114">SQL Server ve Oracle arasındaki bir işlem gibi farklı kaynak yöneticileriyle ilgili işlemler, dağıtılmış bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="822d3-114">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="822d3-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="822d3-115">In This Section</span></span>  

 [<span data-ttu-id="822d3-116">Yerel İşlemler</span><span class="sxs-lookup"><span data-stu-id="822d3-116">Local Transactions</span></span>](local-transactions.md)  
 <span data-ttu-id="822d3-117">Bir veritabanına yönelik işlemlerin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="822d3-117">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="822d3-118">Dağıtılmış Işlemler</span><span class="sxs-lookup"><span data-stu-id="822d3-118">Distributed Transactions</span></span>](distributed-transactions.md)  
 <span data-ttu-id="822d3-119">ADO.NET içinde dağıtılmış işlemlerin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="822d3-119">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="822d3-120">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="822d3-120">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="822d3-121"><xref:System.Transactions>Dağıtılmış işlemlerle çalışmak için SQL Server ile tümleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="822d3-121">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="822d3-122">İyimser Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="822d3-122">Optimistic Concurrency</span></span>](optimistic-concurrency.md)  
 <span data-ttu-id="822d3-123">İyimser ve Kötümser eşzamanlılık ve eşzamanlılık ihlalleri için nasıl test kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="822d3-123">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="822d3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="822d3-124">See also</span></span>

- [<span data-ttu-id="822d3-125">İşlem Temelleri</span><span class="sxs-lookup"><span data-stu-id="822d3-125">Transaction Fundamentals</span></span>](../transactions/transaction-fundamentals.md)
- [<span data-ttu-id="822d3-126">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="822d3-126">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="822d3-127">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="822d3-127">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="822d3-128">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="822d3-128">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="822d3-129">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="822d3-129">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="822d3-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="822d3-130">ADO.NET Overview</span></span>](ado-net-overview.md)
