---
title: "SendParameters ve ReceiveParameters etkinliklerin temel kullanım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 501aead51a96d483a55602c737613e1d9066b74c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="ed744-102">SendParameters ve ReceiveParameters etkinliklerin temel kullanım</span><span class="sxs-lookup"><span data-stu-id="ed744-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="ed744-103">Bu örnek kullanımı gösterilmiştir <xref:System.ServiceModel.Activities.SendParametersContent> ve <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ed744-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="ed744-104">Hizmet, dize bağımsız değişkeni alır ve istemciye geri giriş görüntülemektedir bir işlemi sunar.</span><span class="sxs-lookup"><span data-stu-id="ed744-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="ed744-105">Örnek ileti bu etkinlikler parametrelerini ayarlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed744-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed744-106">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed744-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed744-107">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ed744-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed744-108">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ed744-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed744-109">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ed744-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="ed744-110">Bu örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="ed744-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="ed744-111">Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed744-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="ed744-112">İlk [çözüm temel dizin] \EchoWorkflowService\bin\debug oluşturulan EchoWorkflowService uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ed744-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="ed744-113">İkinci olarak, [çözüm temel dizin] \EchoWorkflowClient\bin\debug oluşturulan EchoWorkflowClient uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ed744-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="ed744-114">İstemci Yankı işlemi hizmet üzerinde çağıran ve sonuçları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ed744-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="ed744-115">Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ed744-115">When complete, press ENTER to exit the client and then the service.</span></span>