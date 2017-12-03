---
title: "Bağıntılı hesaplayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6296ecb5c708d344624cac6e24247d2163fd66b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="correlated-calculator"></a><span data-ttu-id="33a66-102">Bağıntılı hesaplayıcısı</span><span class="sxs-lookup"><span data-stu-id="33a66-102">Correlated Calculator</span></span>
<span data-ttu-id="33a66-103">Bu örnek ileti etkinlikleri kullanmak nasıl gösterir (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>) iletisindeki bir parametre göre içerik tabanlı bağıntıyla Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="33a66-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="33a66-104">Bu senaryoda paralel convoy hesaplayıcı işlemleridir.</span><span class="sxs-lookup"><span data-stu-id="33a66-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="33a66-105">Bir örneği ve bir bağıntı (temel `CalculatorId`) ilk iletiyi iş akışı ve aynı sonraki ileti gönderildiğinde oluşturulan `CalculatorId` sıfırlama işlemi çağrılıncaya kadar bu örneğe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="33a66-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="33a66-106">İstemci hizmetiyle iletişim kurmak için kod tabanlı istemci proxy kullanan bir WPF uygulaması olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="33a66-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="33a66-107">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="33a66-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="33a66-108">Başlat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükseltilmiş izinler'de For.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="33a66-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="33a66-109">İçeren klasöre gidin [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33a66-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="33a66-110">Devenv.exe sağ tıklatıp **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="33a66-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="33a66-111">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CorrelatedCalculator.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="33a66-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="33a66-112">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="33a66-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="33a66-113">Hizmet projesinin çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="33a66-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="33a66-114">Hizmet, Çözüm Gezgini'nde, iletileri için hazır ve dinleme sonra istemci projesine sağ tıklayın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33a66-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33a66-115">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="33a66-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33a66-116">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="33a66-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="33a66-117">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="33a66-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33a66-118">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="33a66-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`