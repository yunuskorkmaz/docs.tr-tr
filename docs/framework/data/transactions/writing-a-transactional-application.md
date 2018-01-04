---
title: "İşlem uygulaması yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fab355da61ea7445e429cfc4e336a14b588e30c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-transactional-application"></a><span data-ttu-id="9a3ba-102">İşlem uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="9a3ba-102">Writing a Transactional Application</span></span>
<span data-ttu-id="9a3ba-103">İşlem Uygulaması Programcı olarak tarafından sağlanan iki programlama modeli özelliklerden yararlanabilirsiniz <xref:System.Transactions> bir işlem oluşturmak için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-103">As a transactional application programmer, you can take advantage of the two programming models provided by the <xref:System.Transactions> namespace to create a transaction.</span></span> <span data-ttu-id="9a3ba-104">Açık programlama modeli kullanarak kullanabilir <xref:System.Transactions.Transaction> sınıfı ya da hangi işlemleri otomatik olarak yönetilir altyapısı tarafından kullanarak örtük programlama modeli <xref:System.Transactions.TransactionScope> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-104">You can utilize the explicit programming model by using the <xref:System.Transactions.Transaction> class, or the implicit programming model in which transactions are automatically managed by the infrastructure, by using the <xref:System.Transactions.TransactionScope> class.</span></span> <span data-ttu-id="9a3ba-105">Geliştirme için örtük işlem modeli kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-105">We recommend that you use the implicit transaction model for development.</span></span> <span data-ttu-id="9a3ba-106">Bir işlem kapsamı içinde kullanma hakkında daha fazla bilgi bulabilirsiniz [örtük bir işlem kapsamı kullanarak işlem uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) konu.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-106">You can find more information on how to use a transaction scope in the [Implementing an Implicit Transaction using Transaction Scope](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) topic.</span></span>  
  
 <span data-ttu-id="9a3ba-107">Her iki modelleri program tutarlı bir duruma ulaştığında bir işlem gerçekleştirmeden destekler.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-107">Both models support committing a transaction when the program reaches a consistent state.</span></span> <span data-ttu-id="9a3ba-108">Yürütme başarılı olursa, işlem getirilir.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-108">If the commit succeeds, the transaction is durably committed.</span></span> <span data-ttu-id="9a3ba-109">Yürütme başarısız olursa, işlem durdurur.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-109">If the commit fails, the transaction aborts.</span></span> <span data-ttu-id="9a3ba-110">Uygulama programı işlem başarılı bir şekilde tamamlanamazsa, iptal etmek ve hareket etkilerinin geri almak çalışır.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-110">If the application program cannot successfully complete the transaction, it attempts to abort and undo the transaction's effects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a3ba-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9a3ba-111">In This Section</span></span>  
  
### <a name="creating-a-transaction"></a><span data-ttu-id="9a3ba-112">Bir işlem oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a3ba-112">Creating a Transaction</span></span>  
 <span data-ttu-id="9a3ba-113"><xref:System.Transactions> Ad alanı, bir işlem oluşturmak için iki modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-113">The <xref:System.Transactions> namespace provides two models for creating a transaction.</span></span> <span data-ttu-id="9a3ba-114">Bu modelleri aşağıdaki konulara değinilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-114">These models are covered in the following topics.</span></span>  
  
 [<span data-ttu-id="9a3ba-115">İşlem Kapsamı Kullanarak Örtük İşlem Uygulama</span><span class="sxs-lookup"><span data-stu-id="9a3ba-115">Implementing an Implicit Transaction using Transaction Scope</span></span>](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <span data-ttu-id="9a3ba-116">Açıklar nasıl <xref:System.Transactions> ad alanı destekleyen kullanarak örtük hareketleri oluşturma <xref:System.Transactions.TransactionScope> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-116">Describes how the <xref:System.Transactions> namespace supports creating implicit transactions using the <xref:System.Transactions.TransactionScope> class.</span></span>  
  
 [<span data-ttu-id="9a3ba-117">CommittableTransaction Kullanarak Belirtik İşlem Uygulama</span><span class="sxs-lookup"><span data-stu-id="9a3ba-117">Implementing an Explicit Transaction using CommittableTransaction</span></span>](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <span data-ttu-id="9a3ba-118">Açıklar nasıl <xref:System.Transactions> ad alanı destekleyen açık işlemleri kullanarak oluşturma <xref:System.Transactions.CommittableTransaction> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-118">Describes how the <xref:System.Transactions> namespace supports creating explicit transactions using the <xref:System.Transactions.CommittableTransaction> class.</span></span>  
  
### <a name="escalating-transaction-management"></a><span data-ttu-id="9a3ba-119">İşlem yönetimi yükselen</span><span class="sxs-lookup"><span data-stu-id="9a3ba-119">Escalating Transaction Management</span></span>  
 <span data-ttu-id="9a3ba-120">Bir işlem başka bir uygulama etki alanındaki bir kaynağa erişmek gerektiğinde veya başka bir sağlam Kaynak Yöneticisi'nde listeleme istiyorsanız işlem otomatik olarak MSDTC tarafından yönetilecek ilerletilen.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-120">When a transaction needs to access a resource in another application domain, or if you want to enlist in another durable resource manager, the transaction is automatically escalated to be managed by the MSDTC.</span></span> <span data-ttu-id="9a3ba-121">İşlem yükseltme kapsanan [işlem yönetimi yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md) konu.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-121">Transaction escalation is covered in the [Transaction Management Escalation](../../../../docs/framework/data/transactions/transaction-management-escalation.md) topic.</span></span>  
  
### <a name="concurrency"></a><span data-ttu-id="9a3ba-122">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="9a3ba-122">Concurrency</span></span>  
 <span data-ttu-id="9a3ba-123">Konu [yönetme eşzamanlılık DependentTransaction ile](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) eşzamanlılık kullanarak zaman uyumsuz görevler arasında nasıl sağlanabilir gösteren <xref:System.Transactions.DependentTransaction> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-123">The topic [Managing Concurrency with DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) demonstrates how concurrency can be achieved between asynchronous tasks by using the <xref:System.Transactions.DependentTransaction> class.</span></span>  
  
### <a name="com-interop"></a><span data-ttu-id="9a3ba-124">COM + birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="9a3ba-124">COM+ Interop</span></span>  
 <span data-ttu-id="9a3ba-125">Konu [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) COM + hareketlerle etkileşimde, dağıtılmış işlemlerin nasıl yapabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-125">The topic [Interoperability with Enterprise Services and COM+ Transactions](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) illustrates how you can make your distributed transactions interact with COM+ transactions.</span></span>  
  
### <a name="diagnostics"></a><span data-ttu-id="9a3ba-126">Tanılamalar</span><span class="sxs-lookup"><span data-stu-id="9a3ba-126">Diagnostics</span></span>  
 <span data-ttu-id="9a3ba-127">[Tanılama izlemeleri](../../../../docs/framework/data/transactions/diagnostic-traces.md) tarafından oluşturulan izleme kodları nasıl kullanabileceğinizi açıklar <xref:System.Transactions> uygulamalarınızda hatalarında sorun giderme için altyapı.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-127">[Diagnostic Traces](../../../../docs/framework/data/transactions/diagnostic-traces.md) describes how you can use the trace codes that are generated by the <xref:System.Transactions> infrastructure to troubleshoot errors in your applications.</span></span>  
  
### <a name="working-within-aspnet"></a><span data-ttu-id="9a3ba-128">ASP.NET içinde çalışma</span><span class="sxs-lookup"><span data-stu-id="9a3ba-128">Working within ASP.NET</span></span>  
 <span data-ttu-id="9a3ba-129">[Kullanarak System.Transactions ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) konu açıklar, başarılı bir şekilde nasıl kullanabileceğinizi <xref:System.Transactions> bir ASP.NET uygulaması içinde.</span><span class="sxs-lookup"><span data-stu-id="9a3ba-129">The [Using System.Transactions in ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>
