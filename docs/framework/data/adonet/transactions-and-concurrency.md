---
title: İşlemler ve eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 9ea136a34c478f3619c81ad3cbbae0765fb99374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365273"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="60742-102">İşlemler ve eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="60742-102">Transactions and Concurrency</span></span>
<span data-ttu-id="60742-103">Bir işlem tek bir komutu veya bir paket olarak yürütme komut grubunu oluşur.</span><span class="sxs-lookup"><span data-stu-id="60742-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="60742-104">İşlemler, iş birden çok işlem tek bir birime birleştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="60742-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="60742-105">İşlem bir noktada bir hata oluşursa, tüm güncelleştirmeler geri ön işlem durumlarına geri alınabilir.</span><span class="sxs-lookup"><span data-stu-id="60742-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="60742-106">Bir işlem ACID özellikleri uymalıdır — kararlılık, tutarlılık, yalıtım ve dayanıklılık — veri tutarlılığı garanti etmek için.</span><span class="sxs-lookup"><span data-stu-id="60742-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="60742-107">Microsoft SQL Server, bir istemci uygulaması bir güncelleştirme gerçekleştirdiğinde, günlüğe kaydetme ve işlem yönetim olanakları kilitleme sağlayarak destek işlemleri gibi çoğu ilişkisel veritabanı sistemleri ekleme veya silme işlemi.</span><span class="sxs-lookup"><span data-stu-id="60742-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60742-108">Kilitleri uzun tutulur, birden fazla kaynak gerektiren işlemler eşzamanlılık düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60742-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="60742-109">Bu nedenle, işlemleri olabildiğince kısa tutun.</span><span class="sxs-lookup"><span data-stu-id="60742-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="60742-110">Bir işlem aynı veritabanı veya sunucu birden çok tablo içeriyorsa, ardından saklı yordamlarda açık işlemleri genellikle daha iyi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="60742-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="60742-111">Transact-SQL kullanarak SQL Server saklı yordamlarda işlemleri oluşturabilirsiniz `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, ve `ROLLBACK TRANSACTION` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="60742-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="60742-112">Daha fazla bilgi için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="60742-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="60742-113">SQL Server ve Oracle, arasında bir işlem gibi farklı kaynak yöneticileri içeren işlemlerin bir dağıtılmış işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="60742-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60742-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="60742-114">In This Section</span></span>  
 [<span data-ttu-id="60742-115">Yerel İşlemler</span><span class="sxs-lookup"><span data-stu-id="60742-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="60742-116">Bir veritabanında işlemleri gerçekleştirmek üzere gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="60742-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="60742-117">Dağıtılmış İşlemler</span><span class="sxs-lookup"><span data-stu-id="60742-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="60742-118">ADO.NET dağıtılmış işlemleri gerçekleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="60742-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="60742-119">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="60742-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="60742-120">Açıklar <xref:System.Transactions> ile çalışmak için SQL Server ile tümleştirme dağıtılmış işlemler.</span><span class="sxs-lookup"><span data-stu-id="60742-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="60742-121">İyimser Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="60742-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="60742-122">İyimser ve kötümser eşzamanlılık ve eşzamanlılık ihlali test nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="60742-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60742-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60742-123">See Also</span></span>  
 [<span data-ttu-id="60742-124">İşlem Temelleri</span><span class="sxs-lookup"><span data-stu-id="60742-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [<span data-ttu-id="60742-125">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="60742-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="60742-126">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="60742-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="60742-127">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="60742-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="60742-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="60742-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="60742-129">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="60742-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
