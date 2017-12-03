---
title: "Kanal göndererek önbelleğe alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f8a11397fe161edad6f726c1d6df9ed09dad54a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="320dc-102">Kanal göndererek önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="320dc-102">Channel Caching with Send</span></span>
<span data-ttu-id="320dc-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Kullanıcıların kanal önbelleğe almayı, farklı düzeylerde olanak sağlayan <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendParametersContent> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="320dc-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="320dc-104">Örnek düzeyinde önbelleğe almayı varsayılan olarak etkindir ve aşağıdaki özellikleri bu örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="320dc-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="320dc-105">Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> uygulama etki alanı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="320dc-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="320dc-106">Kanal önbelleğe almayı devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="320dc-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="320dc-107">Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> iş akışı örnekleri arasında bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="320dc-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="320dc-108">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="320dc-108">Demonstrates</span></span>  
 <span data-ttu-id="320dc-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache>uzantı, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="320dc-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="320dc-110">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="320dc-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="320dc-111">Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="320dc-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="320dc-112">\EchoWorkflowService\bin\debug içinde oluşturulan EchoWorkflowService uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="320dc-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="320dc-113">.\EchoWorkflowClient\bin\debug içinde oluşturulan EchoWorkflowClient uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="320dc-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="320dc-114">İstemci Yankı işlemi hizmet üzerinde çağıran ve sonuçları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="320dc-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="320dc-115">Yazdırma sonuçları, istemci ve hizmet çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="320dc-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="320dc-116">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="320dc-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="320dc-117">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="320dc-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="320dc-118">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="320dc-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="320dc-119">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="320dc-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
