---
title: Bağıntılı hesaplayıcı
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 71cfdd0906ef20ec36b76ef5e508a4551b9fe3fe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517319"
---
# <a name="correlated-calculator"></a><span data-ttu-id="c7a32-102">Bağıntılı hesaplayıcı</span><span class="sxs-lookup"><span data-stu-id="c7a32-102">Correlated Calculator</span></span>
<span data-ttu-id="c7a32-103">Bu örnek ileti etkinlikleri kullanma işlemini gösterir (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>) iletiyi bir parametre temel içerik temelli bağıntı ile Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="c7a32-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="c7a32-104">Bu senaryoda paralel bir konvoy hesaplayıcı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="c7a32-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="c7a32-105">Hem bir örneği hem de bir bağıntı (temel `CalculatorId`) iş akışı ve daha sonraki iletileri aynı ilk ileti gönderildiğinde oluşturulan `CalculatorId` sıfırlama işlemi çağrılana kadar bu örneğe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c7a32-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="c7a32-106">İstemci hizmetiyle iletişim kurmak için bir kod tabanlı istemci proxy kullanan bir WPF uygulaması olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c7a32-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c7a32-107">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c7a32-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="c7a32-108">Başlangıç [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükseltilmiş izinler For.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c7a32-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="c7a32-109">İçeren klasöre gidin [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7a32-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="c7a32-110">Devenv.exe sağ tıklayıp **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="c7a32-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="c7a32-111">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CorrelatedCalculator.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c7a32-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="c7a32-112">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="c7a32-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="c7a32-113">Hizmet projeyi çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="c7a32-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="c7a32-114">Hazır ve dinleme iletileri, Çözüm Gezgini'nde Hizmet başladıktan sonra istemci projesini sağ tıklayın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7a32-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7a32-115">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c7a32-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7a32-116">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c7a32-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7a32-117">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c7a32-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7a32-118">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c7a32-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`