---
title: "İş akışı hizmetleri güvenli hale getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cd7620186ed51110a32e251d5239c85bb90e0f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="securing-workflow-services"></a><span data-ttu-id="ffad6-102">İş akışı hizmetleri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="ffad6-102">Securing Workflow Services</span></span>
<span data-ttu-id="ffad6-103">İş akışı hizmeti güvenli hale getirilmiş örnek aşağıdaki yordamları gösterir:</span><span class="sxs-lookup"><span data-stu-id="ffad6-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="ffad6-104">Kullanarak bir temel iş akışı hizmeti oluşturma <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ffad6-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="ffad6-105">Kullanarak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iş akışı hizmeti tarafından kullanım için güvenli uç noktalarını tanımlamak için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="ffad6-105">Using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="ffad6-106">Özel bir ilke içinde talep oluşturma ve kullanma <xref:System.ServiceModel.ServiceAuthorizationManager> doğrulamak için.</span><span class="sxs-lookup"><span data-stu-id="ffad6-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ffad6-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="ffad6-107">Demonstrates</span></span>  
 <span data-ttu-id="ffad6-108">İş akışı hizmeti ile istemci arasındaki iletişimin güvenliğini sağlamak için WCF güvenlik kullanarak, talep tabanlı yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="ffad6-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ffad6-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="ffad6-109">Discussion</span></span>  
 <span data-ttu-id="ffad6-110">Bu örnek kullanımını gösteren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ile normal bir şekilde bir iş akışı hizmeti güvenli hale getirmek için güvenlik altyapısı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="ffad6-110">This sample demonstrates the use of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure to secure a workflow service just like you would with a normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="ffad6-111">Özellikle, bir özel talep yetkilendirme için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ffad6-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="ffad6-112">Bu durumda, kullanan <xref:System.ServiceModel.WSHttpBinding> ve ileti mod güvenliği Windows kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="ffad6-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="ffad6-113">Özel <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) istemcinin Windows kullanıcı adı denetler ve özel karakter.</span><span class="sxs-lookup"><span data-stu-id="ffad6-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="ffad6-114">Bu karakteri varsa, oluşturur ve talep ekler <xref:System.IdentityModel.Policy.EvaluationContext>.</span><span class="sxs-lookup"><span data-stu-id="ffad6-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="ffad6-115">Bunu yaparak, özel ilke deyimi, yapıyor istemci, kullanıcı bu karakter içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ffad6-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="ffad6-116">Bu talep çağrı ömrü sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ffad6-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="ffad6-117">Bu karakteri bulabilirsiniz `Constants.cs`.</span><span class="sxs-lookup"><span data-stu-id="ffad6-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="ffad6-118">İçinde talep yetkilendirme ilkesi arar `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="ffad6-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="ffad6-119">Bulduğu varsa, döndürür `true` ve devam etmek iş akışı izin verin.</span><span class="sxs-lookup"><span data-stu-id="ffad6-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="ffad6-120">Aksi takdirde, döndürür `false`, istemciye döndürülecek bir 'Erişim engellendi' iletisi neden olur.</span><span class="sxs-lookup"><span data-stu-id="ffad6-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="ffad6-121">Diğer talepleri bağlamda mevcut olduğundan ve de içinde incelenebilir `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="ffad6-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="ffad6-122">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ffad6-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="ffad6-123">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="ffad6-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="ffad6-124">İçinde SecuringWorkflowServices.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ffad6-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="ffad6-125">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ffad6-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="ffad6-126">Hizmet projesinin çözüm başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ffad6-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="ffad6-127">Hata ayıklama olmadan hizmetini başlatmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ffad6-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="ffad6-128">İstemci projesi çözüm başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ffad6-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="ffad6-129">İstemci hata ayıklama olmadan başlatmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ffad6-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffad6-130">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ffad6-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ffad6-131">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ffad6-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ffad6-132">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ffad6-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ffad6-133">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ffad6-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
