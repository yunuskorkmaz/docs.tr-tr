---
title: İşlemler ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 837fe6c42d64f7416dbd895e56a38d1a409e567a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791310"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="bc316-102">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="bc316-102">Transactions and Concurrency</span></span>
<span data-ttu-id="bc316-103">Bir işlem, paket olarak yürütülen tek bir komuttan veya bir komut grubundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="bc316-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="bc316-104">İşlemler, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc316-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="bc316-105">İşlemdeki bir noktada bir hata oluşursa, tüm güncelleştirmeler ön işlem durumuna geri alınabilir.</span><span class="sxs-lookup"><span data-stu-id="bc316-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="bc316-106">Veri tutarlılığını güvence altına almak için bir işlemin ACID özelliklerine (kararlılık, tutarlılık, yalıtım ve dayanıklılık) uyması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc316-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="bc316-107">Microsoft SQL Server gibi çoğu ilişkisel veritabanı sistemi, bir istemci uygulaması bir güncelleştirme, ekleme veya silme işlemi gerçekleştirdiğinde kilitleme, günlüğe kaydetme ve işlem yönetimi olanakları sağlayarak işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="bc316-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc316-108">Kilitler çok uzun tutuluyorsa birden çok kaynağı içeren işlemler eşzamanlılık daha düşük olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc316-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="bc316-109">Bu nedenle, işlemleri mümkün olduğunca kısa tutun.</span><span class="sxs-lookup"><span data-stu-id="bc316-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="bc316-110">Bir işlem aynı veritabanı veya sunucuda birden çok tablo içeriyorsa, saklı yordamlardaki açık işlemler genellikle daha iyi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc316-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="bc316-111">Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, ve `ROLLBACK TRANSACTION` deyimlerini kullanarak SQL Server saklı yordamda işlem oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc316-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="bc316-112">Daha fazla bilgi için bkz. Books Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc316-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="bc316-113">SQL Server ve Oracle arasındaki bir işlem gibi farklı kaynak yöneticileriyle ilgili işlemler, dağıtılmış bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bc316-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc316-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bc316-114">In This Section</span></span>  
 [<span data-ttu-id="bc316-115">Yerel İşlemler</span><span class="sxs-lookup"><span data-stu-id="bc316-115">Local Transactions</span></span>](local-transactions.md)  
 <span data-ttu-id="bc316-116">Bir veritabanına yönelik işlemlerin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc316-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="bc316-117">Dağıtılmış İşlemler</span><span class="sxs-lookup"><span data-stu-id="bc316-117">Distributed Transactions</span></span>](distributed-transactions.md)  
 <span data-ttu-id="bc316-118">ADO.NET içinde dağıtılmış işlemlerin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc316-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="bc316-119">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="bc316-119">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="bc316-120">Dağıtılmış <xref:System.Transactions> işlemlerle çalışmak için SQL Server ile tümleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc316-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="bc316-121">İyimser Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="bc316-121">Optimistic Concurrency</span></span>](optimistic-concurrency.md)  
 <span data-ttu-id="bc316-122">İyimser ve Kötümser eşzamanlılık ve eşzamanlılık ihlalleri için nasıl test kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc316-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc316-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc316-123">See also</span></span>

- [<span data-ttu-id="bc316-124">İşlem Temelleri</span><span class="sxs-lookup"><span data-stu-id="bc316-124">Transaction Fundamentals</span></span>](../transactions/transaction-fundamentals.md)
- [<span data-ttu-id="bc316-125">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="bc316-125">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="bc316-126">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc316-126">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="bc316-127">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="bc316-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="bc316-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="bc316-128">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="bc316-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc316-129">ADO.NET Overview</span></span>](ado-net-overview.md)
