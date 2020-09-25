---
title: İşlem Uygulaması Yazma
description: .NET ' te bir işlemsel uygulama yazın. Sırasıyla Transaction Class veya TransactionScope sınıfıyla açık veya örtük bir programlama modeli kullanın.
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: b4cc33939128e61a69db319491a7d2d60ab9a819
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186684"
---
# <a name="writing-a-transactional-application"></a><span data-ttu-id="c6a71-104">İşlem Uygulaması Yazma</span><span class="sxs-lookup"><span data-stu-id="c6a71-104">Writing a Transactional Application</span></span>

<span data-ttu-id="c6a71-105">Bir işlem uygulaması programlayıcı olarak, <xref:System.Transactions> bir işlem oluşturmak için ad alanı tarafından sunulan iki programlama modelinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6a71-105">As a transactional application programmer, you can take advantage of the two programming models provided by the <xref:System.Transactions> namespace to create a transaction.</span></span> <span data-ttu-id="c6a71-106">Sınıfını kullanarak açık programlama modelini <xref:System.Transactions.Transaction> ya da işlem altyapısı tarafından otomatik olarak yönetilecek örtük programlama modelini kullanabilirsiniz <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="c6a71-106">You can utilize the explicit programming model by using the <xref:System.Transactions.Transaction> class, or the implicit programming model in which transactions are automatically managed by the infrastructure, by using the <xref:System.Transactions.TransactionScope> class.</span></span> <span data-ttu-id="c6a71-107">Geliştirme için örtük işlem modelini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="c6a71-107">We recommend that you use the implicit transaction model for development.</span></span> <span data-ttu-id="c6a71-108">İşlem kapsamı [kullanarak örtük bir Işlem uygulama](implementing-an-implicit-transaction-using-transaction-scope.md) konusunda bir işlem kapsamının nasıl kullanılacağına ilişkin daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6a71-108">You can find more information on how to use a transaction scope in the [Implementing an Implicit Transaction using Transaction Scope](implementing-an-implicit-transaction-using-transaction-scope.md) topic.</span></span>  
  
 <span data-ttu-id="c6a71-109">Her iki model de program tutarlı bir duruma ulaştığında işlem yürütmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="c6a71-109">Both models support committing a transaction when the program reaches a consistent state.</span></span> <span data-ttu-id="c6a71-110">Yürütme başarılı olursa, işlem durda işlenir.</span><span class="sxs-lookup"><span data-stu-id="c6a71-110">If the commit succeeds, the transaction is durably committed.</span></span> <span data-ttu-id="c6a71-111">İşleme başarısız olursa, işlem iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="c6a71-111">If the commit fails, the transaction aborts.</span></span> <span data-ttu-id="c6a71-112">Uygulama programı işlemi başarıyla tamamlayamadıysanız, işlemin etkilerini durdurmayı ve geri almayı dener.</span><span class="sxs-lookup"><span data-stu-id="c6a71-112">If the application program cannot successfully complete the transaction, it attempts to abort and undo the transaction's effects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6a71-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c6a71-113">In This Section</span></span>  
  
### <a name="creating-a-transaction"></a><span data-ttu-id="c6a71-114">Işlem oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6a71-114">Creating a Transaction</span></span>  

 <span data-ttu-id="c6a71-115"><xref:System.Transactions>Ad alanı, işlem oluşturmak için iki model sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6a71-115">The <xref:System.Transactions> namespace provides two models for creating a transaction.</span></span> <span data-ttu-id="c6a71-116">Bu modelleri aşağıdaki konulara değinilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6a71-116">These models are covered in the following topics.</span></span>  
  
 [<span data-ttu-id="c6a71-117">İşlem Kapsamı Kullanarak Örtük İşlem Uygulama</span><span class="sxs-lookup"><span data-stu-id="c6a71-117">Implementing an Implicit Transaction using Transaction Scope</span></span>](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <span data-ttu-id="c6a71-118"><xref:System.Transactions>Ad alanının sınıfını kullanarak örtük işlemler oluşturmayı nasıl desteklediğini açıklar <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="c6a71-118">Describes how the <xref:System.Transactions> namespace supports creating implicit transactions using the <xref:System.Transactions.TransactionScope> class.</span></span>  
  
 [<span data-ttu-id="c6a71-119">CommittableTransaction Kullanarak Belirtik İşlem Uygulama</span><span class="sxs-lookup"><span data-stu-id="c6a71-119">Implementing an Explicit Transaction using CommittableTransaction</span></span>](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <span data-ttu-id="c6a71-120"><xref:System.Transactions>Ad alanının sınıfını kullanarak açık işlemler oluşturmayı nasıl desteklediğini açıklar <xref:System.Transactions.CommittableTransaction> .</span><span class="sxs-lookup"><span data-stu-id="c6a71-120">Describes how the <xref:System.Transactions> namespace supports creating explicit transactions using the <xref:System.Transactions.CommittableTransaction> class.</span></span>  
  
### <a name="escalating-transaction-management"></a><span data-ttu-id="c6a71-121">Işlem yönetimini ilerleme</span><span class="sxs-lookup"><span data-stu-id="c6a71-121">Escalating Transaction Management</span></span>  

 <span data-ttu-id="c6a71-122">Bir işlemin başka bir uygulama etki alanındaki bir kaynağa erişmesi gerektiğinde veya başka bir dayanıklı Resource Manager 'da listeleme yapmak istiyorsanız, işlem otomatik olarak MSDTC tarafından yönetilmek üzere ilerletildi.</span><span class="sxs-lookup"><span data-stu-id="c6a71-122">When a transaction needs to access a resource in another application domain, or if you want to enlist in another durable resource manager, the transaction is automatically escalated to be managed by the MSDTC.</span></span> <span data-ttu-id="c6a71-123">İşlem yükseltme, [Işlem yönetimi yükseltme](transaction-management-escalation.md) konusunda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6a71-123">Transaction escalation is covered in the [Transaction Management Escalation](transaction-management-escalation.md) topic.</span></span>  
  
### <a name="concurrency"></a><span data-ttu-id="c6a71-124">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="c6a71-124">Concurrency</span></span>  

 <span data-ttu-id="c6a71-125">[DependentTransaction Ile eşzamanlılık yönetme](managing-concurrency-with-dependenttransaction.md) konusu, sınıfı kullanılarak zaman uyumsuz görevler arasında eşzamanlılık elde edilebileceğinizi gösterir <xref:System.Transactions.DependentTransaction> .</span><span class="sxs-lookup"><span data-stu-id="c6a71-125">The topic [Managing Concurrency with DependentTransaction](managing-concurrency-with-dependenttransaction.md) demonstrates how concurrency can be achieved between asynchronous tasks by using the <xref:System.Transactions.DependentTransaction> class.</span></span>  
  
### <a name="com-interop"></a><span data-ttu-id="c6a71-126">COM + birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="c6a71-126">COM+ Interop</span></span>  

 <span data-ttu-id="c6a71-127">[Kurumsal Hizmetler ve com+ işlemleri Ile birlikte çalışabilirlik](interoperability-with-enterprise-services-and-com-transactions.md) konusu, dağıtılmış işlemlerinizi com+ işlemleriyle nasıl etkileşime girecağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6a71-127">The topic [Interoperability with Enterprise Services and COM+ Transactions](interoperability-with-enterprise-services-and-com-transactions.md) illustrates how you can make your distributed transactions interact with COM+ transactions.</span></span>  
  
### <a name="diagnostics"></a><span data-ttu-id="c6a71-128">Tanılama</span><span class="sxs-lookup"><span data-stu-id="c6a71-128">Diagnostics</span></span>  

 <span data-ttu-id="c6a71-129">[Tanılama izlemeleri](diagnostic-traces.md) , <xref:System.Transactions> uygulamalarınızda hata gidermek için altyapı tarafından oluşturulan izleme kodlarını nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6a71-129">[Diagnostic Traces](diagnostic-traces.md) describes how you can use the trace codes that are generated by the <xref:System.Transactions> infrastructure to troubleshoot errors in your applications.</span></span>  
  
### <a name="working-within-aspnet"></a><span data-ttu-id="c6a71-130">ASP.NET içinde çalışma</span><span class="sxs-lookup"><span data-stu-id="c6a71-130">Working within ASP.NET</span></span>  

 <span data-ttu-id="c6a71-131">[ASP.net ' de using System. Transactions](using-system-transactions-in-aspnet.md) , <xref:System.Transactions> bir ASP.NET uygulamasının içinde nasıl başarıyla kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6a71-131">The [Using System.Transactions in ASP.NET](using-system-transactions-in-aspnet.md) topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>
