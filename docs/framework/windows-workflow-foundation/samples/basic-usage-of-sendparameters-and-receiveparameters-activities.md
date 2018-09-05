---
title: SendParameters ve ReceiveParameters etkinliklerinin temel kullanımı
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504014"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="24798-102">SendParameters ve ReceiveParameters etkinliklerinin temel kullanımı</span><span class="sxs-lookup"><span data-stu-id="24798-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="24798-103">Bu örnek, kullanımını gösterir. <xref:System.ServiceModel.Activities.SendParametersContent> ve <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="24798-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="24798-104">Hizmet, bir dize bağımsız değişkeni alır ve giriş istemcisine yankılayan tek bir işlem sunar.</span><span class="sxs-lookup"><span data-stu-id="24798-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="24798-105">Örnek, bu ileti etkinlikleri parametrelerini ayarlama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24798-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24798-106">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="24798-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24798-107">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="24798-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="24798-108">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="24798-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24798-109">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="24798-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="24798-110">Bu örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="24798-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="24798-111">Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="24798-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="24798-112">İlk [çözüm temel dizini] \EchoWorkflowService\bin\debug içinde oluşturulan EchoWorkflowService uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="24798-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="24798-113">İkinci olarak, [çözüm temel dizini] \EchoWorkflowClient\bin\debug içinde oluşturulan EchoWorkflowClient uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="24798-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="24798-114">İstemci, Echo hizmet işlemi çağırır ve sonuçları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="24798-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="24798-115">Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="24798-115">When complete, press ENTER to exit the client and then the service.</span></span>