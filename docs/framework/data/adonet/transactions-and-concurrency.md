---
title: İşlemler ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 049e402345e1abbb46739e48c89101207a43bb27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191677"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="1855b-102">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="1855b-102">Transactions and Concurrency</span></span>

<span data-ttu-id="1855b-103">Bir işlem, paket olarak yürütülen tek bir komuttan veya bir komut grubundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="1855b-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="1855b-104">İşlemler, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1855b-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="1855b-105">İşlemdeki bir noktada bir hata oluşursa, tüm güncelleştirmeler ön işlem durumuna geri alınabilir.</span><span class="sxs-lookup"><span data-stu-id="1855b-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="1855b-106">Veri tutarlılığını güvence altına almak için bir işlemin ACID özelliklerine (kararlılık, tutarlılık, yalıtım ve dayanıklılık) uyması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1855b-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="1855b-107">Microsoft SQL Server gibi çoğu ilişkisel veritabanı sistemi, bir istemci uygulaması bir güncelleştirme, ekleme veya silme işlemi gerçekleştirdiğinde kilitleme, günlüğe kaydetme ve işlem yönetimi olanakları sağlayarak işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1855b-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1855b-108">Kilitler çok uzun tutuluyorsa birden çok kaynağı içeren işlemler eşzamanlılık daha düşük olabilir.</span><span class="sxs-lookup"><span data-stu-id="1855b-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="1855b-109">Bu nedenle, işlemleri mümkün olduğunca kısa tutun.</span><span class="sxs-lookup"><span data-stu-id="1855b-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="1855b-110">Bir işlem aynı veritabanı veya sunucuda birden çok tablo içeriyorsa, saklı yordamlardaki açık işlemler genellikle daha iyi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1855b-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="1855b-111">Transact-SQL `BEGIN TRANSACTION` , `COMMIT TRANSACTION` , ve deyimlerini kullanarak SQL Server saklı yordamda işlem oluşturabilirsiniz `ROLLBACK TRANSACTION` .</span><span class="sxs-lookup"><span data-stu-id="1855b-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="1855b-112">Daha fazla bilgi için bkz. Books Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1855b-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="1855b-113">SQL Server ve Oracle arasındaki bir işlem gibi farklı kaynak yöneticileriyle ilgili işlemler, dağıtılmış bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1855b-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1855b-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1855b-114">In This Section</span></span>  

 [<span data-ttu-id="1855b-115">Yerel İşlemler</span><span class="sxs-lookup"><span data-stu-id="1855b-115">Local Transactions</span></span>](local-transactions.md)  
 <span data-ttu-id="1855b-116">Bir veritabanına yönelik işlemlerin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1855b-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="1855b-117">Dağıtılmış İşlemler</span><span class="sxs-lookup"><span data-stu-id="1855b-117">Distributed Transactions</span></span>](distributed-transactions.md)  
 <span data-ttu-id="1855b-118">ADO.NET içinde dağıtılmış işlemlerin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1855b-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="1855b-119">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="1855b-119">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="1855b-120"><xref:System.Transactions>Dağıtılmış işlemlerle çalışmak için SQL Server ile tümleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1855b-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="1855b-121">İyimser Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="1855b-121">Optimistic Concurrency</span></span>](optimistic-concurrency.md)  
 <span data-ttu-id="1855b-122">İyimser ve Kötümser eşzamanlılık ve eşzamanlılık ihlalleri için nasıl test kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1855b-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1855b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1855b-123">See also</span></span>

- [<span data-ttu-id="1855b-124">İşlem Temelleri</span><span class="sxs-lookup"><span data-stu-id="1855b-124">Transaction Fundamentals</span></span>](../transactions/transaction-fundamentals.md)
- [<span data-ttu-id="1855b-125">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="1855b-125">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="1855b-126">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="1855b-126">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="1855b-127">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="1855b-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="1855b-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="1855b-128">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="1855b-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1855b-129">ADO.NET Overview</span></span>](ado-net-overview.md)
