---
title: İşlemler ve eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: bd47c5e0e2b2086e5fd0482bf4319ebab5674a54
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386691"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="15b54-102">İşlemler ve eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="15b54-102">Transactions and Concurrency</span></span>
<span data-ttu-id="15b54-103">Tek bir komutu veya bir paket olarak çalıştırılacak komut grubuyla ilgili bir işlem oluşur.</span><span class="sxs-lookup"><span data-stu-id="15b54-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="15b54-104">İşlemler, iş birden çok işlem tek bir birim halinde birleştirmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="15b54-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="15b54-105">İşlem bir noktadaki bir hata oluşması durumunda tüm güncelleştirmeleri geri ön işlem durumlarına geri alınabilir.</span><span class="sxs-lookup"><span data-stu-id="15b54-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="15b54-106">Bir işlem için ACID özellikleri uymalıdır — kararlılık, tutarlılık, yalıtım ve dayanıklılık — veri tutarlılık garantisi için.</span><span class="sxs-lookup"><span data-stu-id="15b54-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="15b54-107">Microsoft SQL Server, bir istemci uygulama bir güncelleştirme gerçekleştirdiğinde, günlüğe kaydetme ve işlem yönetimi olanakları kilitleme sağlayarak destek işlemleri gibi çoğu ilişkisel veritabanı sistemleri ekleme veya silme işlemi.</span><span class="sxs-lookup"><span data-stu-id="15b54-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15b54-108">Kilitleri uzun tutulur, birden fazla kaynak gerektiren işlemler eşzamanlılık düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15b54-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="15b54-109">Bu nedenle, işlemleri olabildiğince kısa tutun.</span><span class="sxs-lookup"><span data-stu-id="15b54-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="15b54-110">Bir işlem birden çok tablodan aynı veritabanı veya sunucu içeriyorsa, ardından saklı yordamlarda açık işlemleri genellikle daha iyi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="15b54-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="15b54-111">Transact-SQL kullanarak SQL Server saklı yordamları işlemleri oluşturabilirsiniz `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, ve `ROLLBACK TRANSACTION` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="15b54-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="15b54-112">Daha fazla bilgi için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="15b54-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="15b54-113">SQL Server ve Oracle, arasında bir işlem gibi farklı kaynak yöneticileri içeren işlemler, dağıtılmış bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="15b54-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15b54-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="15b54-114">In This Section</span></span>  
 [<span data-ttu-id="15b54-115">Yerel İşlemler</span><span class="sxs-lookup"><span data-stu-id="15b54-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="15b54-116">Bir veritabanında işlemleri gerçekleştirmek üzere nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="15b54-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="15b54-117">Dağıtılmış İşlemler</span><span class="sxs-lookup"><span data-stu-id="15b54-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="15b54-118">Dağıtılmış işlemler ADO.NET yerine getirilmesi anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15b54-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="15b54-119">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="15b54-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="15b54-120">Açıklar <xref:System.Transactions> dağıtılmış işlemler ile çalışmak için SQL Server ile tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="15b54-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="15b54-121">İyimser Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="15b54-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="15b54-122">İyimser ve kötümser eşzamanlılık ve eşzamanlılık ihlaller için nasıl sınayıp doğrulayabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="15b54-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b54-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15b54-123">See Also</span></span>  
 [<span data-ttu-id="15b54-124">İşlem Temelleri</span><span class="sxs-lookup"><span data-stu-id="15b54-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [<span data-ttu-id="15b54-125">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="15b54-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="15b54-126">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="15b54-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="15b54-127">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="15b54-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="15b54-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="15b54-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="15b54-129">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="15b54-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
