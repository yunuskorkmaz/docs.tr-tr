---
title: Compensable etkinliği örneği
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583333"
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="66673-102">Compensable etkinliği örneği</span><span class="sxs-lookup"><span data-stu-id="66673-102">Compensable Activity Sample</span></span>
<span data-ttu-id="66673-103">Bu örnek nasıl kullanılacağını gösterir `CompensableActivity` normal yürütme sırasında belirli bir eylemi için yapılacak işleri ve bu eylemi dengelemek için daha sonra gerekirse yapılması gereken çalışmayı tanımlamak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="66673-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="66673-104">Windows Workflow Foundation (WF) compensable iş birimleri nasıl tanımlanabilir örnek ilk bölümü gösterir kullanarak bir `CompensableActivity` etkinliği ve nasıl başarılı bir çalıştırmada yürütülür.</span><span class="sxs-lookup"><span data-stu-id="66673-104">The first part of the sample shows how units of compensable work can be defined in Windows Workflow Foundation (WF) using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="66673-105">İkinci örnek bölümü nasıl aynı compensable iş birimleri otomatik olarak maaş beklenmeyen bir olay ulaşılır ve iş akışı örneği iptal ilgileniriz gösterir.</span><span class="sxs-lookup"><span data-stu-id="66673-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="66673-106">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="66673-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="66673-107">Visual Studio 2010'u kullanarak, CompensableActivity.sln açın.</span><span class="sxs-lookup"><span data-stu-id="66673-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="66673-108">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="66673-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="66673-109">F5 tuşuna basarak uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66673-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="66673-110">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="66673-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66673-111">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="66673-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="66673-112">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="66673-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66673-113">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="66673-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`