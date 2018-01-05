---
title: "Kesinlik temelli bir hareket bir iş akışı yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 530a590931a1cb3994406e5605f8da2853ceddaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a><span data-ttu-id="794c9-102">Kesinlik temelli bir hareket bir iş akışı yürütme</span><span class="sxs-lookup"><span data-stu-id="794c9-102">Execute a Workflow in an Imperative TransactionScope</span></span>
<span data-ttu-id="794c9-103">Bu örnek, bir iş akışını kullanarak yürütmek gösterilmiştir <xref:System.Activities.WorkflowInvoker> altında bir <xref:System.Transactions.Transaction> kesinlik temelli C# kodundan.</span><span class="sxs-lookup"><span data-stu-id="794c9-103">This sample shows how to execute a workflow using <xref:System.Activities.WorkflowInvoker> under a <xref:System.Transactions.Transaction> from imperative C# code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="794c9-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="794c9-104">Sample Details</span></span>  
 <span data-ttu-id="794c9-105">Kesinlik temelli C# kod, <xref:System.Transactions.TransactionScope> aynı işlemde yürüten iş kümesi kapsüllemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="794c9-105">In imperative C# code, the <xref:System.Transactions.TransactionScope> is used to encapsulate a set of work that executes under the same transaction.</span></span> <span data-ttu-id="794c9-106"><xref:System.Transactions.TransactionScope> Bir ortam işlem oluşturma ve başlatma çalışır <xref:System.Transactions.Transaction.Current%2A> sonra o iş parçacığı üzerinde yürütülmekte olan herhangi bir iş tarafından erişilebilecek özelliği.</span><span class="sxs-lookup"><span data-stu-id="794c9-106">The <xref:System.Transactions.TransactionScope> works by creating an ambient transaction and initializing the <xref:System.Transactions.Transaction.Current%2A> property, which can then be accessed by any work being executed on that thread.</span></span>  
  
 <span data-ttu-id="794c9-107">İş akışında eşdeğer davranışı elde etmek üzere başlatma ek işlemlerini yapmak çalışma zamanı sahip <xref:System.Transactions.Transaction.Current%2A> bir iş akışı etkinlikleri arasındaki iş parçacığı benzeşimini korumaz çünkü her etkinlik yürütmeden önce.</span><span class="sxs-lookup"><span data-stu-id="794c9-107">To get equivalent behavior in workflow, the runtime has to do the extra work of initializing <xref:System.Transactions.Transaction.Current%2A> before executing each activity because a workflow does not maintain thread affinity between activities.</span></span> <span data-ttu-id="794c9-108">Bu çalışma zamanı desteği ile sonuç davranışına sahip bir iş akışı yürütülürken olan <xref:System.Activities.WorkflowInvoker> içinde bir <xref:System.Transactions.TransactionScope>, tüm etkinlikleri tarafından oluşturulan ortam işlem bağlamı altında çalışmasını garanti <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="794c9-108">With this runtime support, the resulting behavior is that when executing a workflow with <xref:System.Activities.WorkflowInvoker> inside a <xref:System.Transactions.TransactionScope>, all activities are guaranteed to run under the context of the ambient transaction created by the <xref:System.Transactions.TransactionScope>.</span></span>  
  
 <span data-ttu-id="794c9-109">Bir iş akışı yalnızca tek bir ortam işlem her iş akışı örneği olabilir; iç içe geçmiş işlemler kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="794c9-109">A workflow can have only a single ambient transaction for each workflow instance; nested transactions are not available.</span></span> <span data-ttu-id="794c9-110">İş akışı içeriyor olsa bile bir <xref:System.Activities.Statements.TransactionScope> etkinlik, bu oluşturmaz yeni bir iç işlemi.</span><span class="sxs-lookup"><span data-stu-id="794c9-110">Even if the workflow contains a <xref:System.Activities.Statements.TransactionScope> activity, this does not create a new inner transaction.</span></span> <span data-ttu-id="794c9-111">Bunun yerine, bu iş akışının dışında oluşturulduğu ortam işlem yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="794c9-111">Instead, this reuses the ambient transaction that was created outside the workflow.</span></span>  
  
 <span data-ttu-id="794c9-112">Örnek bir yeni başlayan <xref:System.Transactions.TransactionScope>, işlem kimliği yazdırır ve iş akışını kullanarak başlar <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="794c9-112">The sample begins a new <xref:System.Transactions.TransactionScope>, prints the transaction ID and begins a workflow using <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="794c9-113">İş akışı kimliği yeniden şekilde gösteren aynı işlem, sonra çalışan işlem yazdırır bir <xref:System.Activities.Statements.TransactionScope>, ardından tamamlar.</span><span class="sxs-lookup"><span data-stu-id="794c9-113">The workflow prints the transaction ID again, showing that it is the same transaction, then runs a <xref:System.Activities.Statements.TransactionScope>, then completes.</span></span> <span data-ttu-id="794c9-114"><xref:System.Activities.WorkflowInvoker.Invoke%2A> Çağırmak <xref:System.Activities.WorkflowInvoker> iş akışı tamamlanana kadar özgün iş parçacığı engeller şekilde uyumludur.</span><span class="sxs-lookup"><span data-stu-id="794c9-114">The <xref:System.Activities.WorkflowInvoker.Invoke%2A> call on <xref:System.Activities.WorkflowInvoker> is synchronous so the original thread blocks until the workflow completes.</span></span> <span data-ttu-id="794c9-115">İş akışı tamamlandıktan sonra işlem tamamlanmadan ve kaynakları atıldı.</span><span class="sxs-lookup"><span data-stu-id="794c9-115">Once the workflow is complete, the transaction is completed and resources disposed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="794c9-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="794c9-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="794c9-117">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ImperativeTransactionSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="794c9-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ImperativeTransactionSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="794c9-118">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="794c9-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="794c9-119">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="794c9-119">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="794c9-120">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="794c9-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="794c9-121">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="794c9-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="794c9-122">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="794c9-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="794c9-123">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="794c9-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`