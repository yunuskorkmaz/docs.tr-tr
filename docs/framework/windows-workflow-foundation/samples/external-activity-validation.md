---
title: "Dış etkinlik doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ebc79fa582a32ccc252e6c22b9b223870da7e44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="external-activity-validation"></a><span data-ttu-id="9cea9-102">Dış etkinlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="9cea9-102">External Activity Validation</span></span>
<span data-ttu-id="9cea9-103">Bu örnek nasıl doğrulama mantığını yazarı olmayan yerleşik bir etkinlik ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9cea9-103">This sample shows how to add validation logic to a built-in activity that you are not the author of.</span></span> <span data-ttu-id="9cea9-104">Doğrulama mantığını zorlama oluşur tüm <xref:System.Activities.Statements.If> etkinlikleri sunmak ya da iş akışında kendi <xref:System.Activities.Statements.If.Then%2A> özellik kümesi veya kendi <xref:System.Activities.Statements.If.Else%2A> özellik kümesi.</span><span class="sxs-lookup"><span data-stu-id="9cea9-104">The validation logic consists of enforcing that all <xref:System.Activities.Statements.If> activities present in the workflow either have their <xref:System.Activities.Statements.If.Then%2A> property set or their <xref:System.Activities.Statements.If.Else%2A> property set.</span></span> <span data-ttu-id="9cea9-105">Ayrıca, doğrulama mantığını olduğunu denetimini içermektedir ve tüm <xref:System.Activities.Statements.Pick> etkinlikler iş akışında mevcut sahip birden çok dal ve bu durumda değilse, bir uyarı üretilir.</span><span class="sxs-lookup"><span data-stu-id="9cea9-105">Also, the validation logic includes checking that all <xref:System.Activities.Statements.Pick> activities present in the workflow have more than one branch, and if that is not the case, a warning is generated.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="9cea9-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9cea9-106">Sample details</span></span>  
 <span data-ttu-id="9cea9-107">Bu örnek bir iş akışı doğrulamak için her etkinlik bir örneğini oluşturur: <xref:System.Activities.Statements.If> etkinlik ve <xref:System.Activities.Statements.Pick> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9cea9-107">This sample creates a workflow with an instance of each activity to validate: the <xref:System.Activities.Statements.If> activity and the <xref:System.Activities.Statements.Pick> activity.</span></span> <span data-ttu-id="9cea9-108">A <xref:System.Activities.Validation.Constraint> her doğrulama davranışını oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9cea9-108">A <xref:System.Activities.Validation.Constraint> is created for each validation behavior.</span></span> <span data-ttu-id="9cea9-109">Bu örnekte oluşturulan sınırlamalardır `ConstraintError_IfShouldHaveThenOrElse` ve `ConstraintWarning_PickHasOneBranch`.</span><span class="sxs-lookup"><span data-stu-id="9cea9-109">The constraints created in this sample are `ConstraintError_IfShouldHaveThenOrElse` and `ConstraintWarning_PickHasOneBranch`.</span></span> <span data-ttu-id="9cea9-110">Ardından, bu kısıtlamaların eklenir `AdditionalConstraints` koleksiyonu bir <xref:System.Activities.Validation.ValidationSettings> örneği.</span><span class="sxs-lookup"><span data-stu-id="9cea9-110">Next, these constraints are added to the `AdditionalConstraints` collection of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="9cea9-111">Son olarak, `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> yöntemi <xref:System.Activities.Validation.ActivityValidationServices> iş akışı ve sonuçları yazdırılmıştır konsola doğrulama etkinlikler doğrulamak üzere çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9cea9-111">Finally, the `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method of <xref:System.Activities.Validation.ActivityValidationServices> is called to validate the activities in the workflow and the validation results are printed out to the console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cea9-112">İlke kısıtlamaları için herhangi bir etkinlik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cea9-112">You can add policy constraints to any activity.</span></span> <span data-ttu-id="9cea9-113">Örneğin, bir ilke kısıtlaması ekleyebileceğiniz bir <xref:System.Activities.Statements.Sequence> veya <xref:System.Activities.Statements.Parallel> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9cea9-113">For example, you can add a policy constraint to a <xref:System.Activities.Statements.Sequence> or <xref:System.Activities.Statements.Parallel> activity.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9cea9-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9cea9-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="9cea9-115">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ExternalActivityValidation.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9cea9-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExternalActivityValidation.sln file.</span></span>  
  
2.  <span data-ttu-id="9cea9-116">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9cea9-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9cea9-117">Çözümü çalıştırmak için Ctrl + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9cea9-117">To run the solution, press Ctrl+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9cea9-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cea9-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9cea9-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9cea9-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9cea9-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9cea9-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9cea9-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9cea9-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`