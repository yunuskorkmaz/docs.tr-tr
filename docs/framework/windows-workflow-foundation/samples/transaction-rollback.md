---
title: "İşlemi geri alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85ae459a8e79beba9ecffb16476b37468aeb632e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-rollback"></a><span data-ttu-id="92924-102">İşlemi geri alma</span><span class="sxs-lookup"><span data-stu-id="92924-102">Transaction Rollback</span></span>
<span data-ttu-id="92924-103">Bu örnek özel bir oluşturulacağını gösterir <xref:System.Activities.NativeActivity> ortam erişen <xref:System.Activities.RuntimeTransactionHandle> ortam işlem almak ve açıkça geri alma.</span><span class="sxs-lookup"><span data-stu-id="92924-103">This sample shows how to create a custom <xref:System.Activities.NativeActivity> that accesses the ambient <xref:System.Activities.RuntimeTransactionHandle> to get the ambient transaction and explicitly roll it back.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="92924-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="92924-104">Sample Details</span></span>  
 <span data-ttu-id="92924-105">İş akışı içinde otomatik olarak bir işlem olduğu zaman tamamlandı dıştaki <xref:System.Activities.Statements.TransactionScope> veya <xref:System.ServiceModel.Activities.TransactedReceiveScope> tamamlar.</span><span class="sxs-lookup"><span data-stu-id="92924-105">In workflow, a transaction is automatically completed when the outermost <xref:System.Activities.Statements.TransactionScope> or <xref:System.ServiceModel.Activities.TransactedReceiveScope> completes.</span></span>  <span data-ttu-id="92924-106">İşlenmeyen bir özel durum kapsam sınırından geri yayar zaman örtük olarak bir işlem yapar.</span><span class="sxs-lookup"><span data-stu-id="92924-106">A transaction implicitly rolls back when an unhandled exception propagates across the scope boundary.</span></span> <span data-ttu-id="92924-107">Ancak, ne zaman açıkça bir işlem bir özel durum gerek kalmadan geri almak için bir anlam zamanlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="92924-107">However, there may be times when it makes sense to explicitly roll back a transaction without having to throw an exception.</span></span> <span data-ttu-id="92924-108">Bu durumda, bu örnekteki gibi özel geri alma etkinlik açıkça ortam işlem iptal etmek ve isteğe bağlı özel durum nedeni sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92924-108">In this case, you can use the custom rollback activity like the one in this sample to explicitly abort the ambient transaction and provide an optional exception reason.</span></span>  
  
 <span data-ttu-id="92924-109">`RollbackActivity` Olan bir <xref:System.Activities.NativeActivity> ortam almak için yürütme özelliklerine erişim gerektirdiği şekilde <xref:System.Activities.RuntimeTransactionHandle>.</span><span class="sxs-lookup"><span data-stu-id="92924-109">The `RollbackActivity` is a <xref:System.Activities.NativeActivity> as it requires access to the execution properties to get the ambient <xref:System.Activities.RuntimeTransactionHandle>.</span></span> <span data-ttu-id="92924-110">İçinde `Execute` yöntemi alır <xref:System.Activities.RuntimeTransactionHandle> ve olup olmadığını denetler `null`, etkinlik bir ortam çalıştırma işlem olmadan kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="92924-110">In the `Execute` method, it obtains the <xref:System.Activities.RuntimeTransactionHandle> and checks whether it is `null`, which indicates that the activity was used without an ambient run-time transaction.</span></span> <span data-ttu-id="92924-111">Daha sonra yeniden denetlemeden işlemin edinir olup olmadığını `null` mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="92924-111">It then obtains the transaction, again checking whether `null` is present.</span></span> <span data-ttu-id="92924-112">Bir ortam olması mümkündür <xref:System.Activities.RuntimeTransactionHandle> olmadan herhangi bir zamanda bir çalışma zamanı işlemi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="92924-112">It is possible to have an ambient <xref:System.Activities.RuntimeTransactionHandle> without ever initializing a run-time transaction.</span></span> <span data-ttu-id="92924-113">Son olarak çağırarak işlemi iptal <xref:System.Transactions.Transaction.Rollback%2A> ve bir kullanıcı tarafından sağlanan özel veya etkinlik işlem geri alındı durumları genel bir özel durum belirtme.</span><span class="sxs-lookup"><span data-stu-id="92924-113">Finally it aborts the transaction by calling <xref:System.Transactions.Transaction.Rollback%2A> and specifying either a user-provided exception or a generic exception that states that the activity rolled back the transaction.</span></span>  
  
 <span data-ttu-id="92924-114">Tanıtım iş akışı oluşan bir <xref:System.Activities.Statements.TransactionScope> , gövde önce ve sonra işlem durumu yazdırır `RollbackActivity` yürütür.</span><span class="sxs-lookup"><span data-stu-id="92924-114">The demonstration workflow consists of a <xref:System.Activities.Statements.TransactionScope> whose body prints the transaction status before and after the `RollbackActivity` executes.</span></span> <span data-ttu-id="92924-115">İşlem geri alınamaz olsa bile unutmayın <xref:System.Activities.Statements.TransactionScope> tamamlanıncaya kadar yürütür ve gövde tamamlanana kadar iş akışı iptal değil.</span><span class="sxs-lookup"><span data-stu-id="92924-115">Note that even though the transaction has been rolled back, the <xref:System.Activities.Statements.TransactionScope> executes to completion and does not abort the workflow until the body completes.</span></span> <span data-ttu-id="92924-116">İş akışı olduğundan iptal <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> özelliği varsayılan olarak `true`.</span><span class="sxs-lookup"><span data-stu-id="92924-116">The workflow is aborted because the <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> property defaults to `true`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="92924-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="92924-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="92924-118">TransactionRollback.sln çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92924-118">Load the TransactionRollback.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="92924-119">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="92924-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="92924-120">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="92924-120">Press CTRL+F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92924-121">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="92924-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="92924-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="92924-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="92924-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="92924-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92924-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="92924-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a><span data-ttu-id="92924-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92924-125">See Also</span></span>  
 [<span data-ttu-id="92924-126">İşlemler</span><span class="sxs-lookup"><span data-stu-id="92924-126">Transactions</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
