---
title: Compensable etkinlik örnek
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 8008eaaca062723cab1efabfb1b25018353c73b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514012"
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="c99fd-102">Compensable etkinlik örnek</span><span class="sxs-lookup"><span data-stu-id="c99fd-102">Compensable Activity Sample</span></span>
<span data-ttu-id="c99fd-103">Bu örnek nasıl kullanılacağı ortaya `CompensableActivity` normal yürütme sırasında belirli bir eylem için yapılacak işleri ve o eylemi dengelemek için daha sonra gerekirse yapılması gerekli olan iş tanımlamak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c99fd-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="c99fd-104">Windows Workflow Foundation (WF) compensable iş birimleri nasıl tanımlanabilir örnek ilk bölümü gösterir kullanarak bir `CompensableActivity` etkinliği ve nasıl başarılı çalıştırılmasıyla yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c99fd-104">The first part of the sample shows how units of compensable work can be defined in Windows Workflow Foundation (WF) using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="c99fd-105">Örnek ikinci bölümü nasıl compensable iş aynı birimleri otomatik olarak maaş beklenmeyen bir olay isabet ve iş akışı örneği iptal ilgilenebilmek gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99fd-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c99fd-106">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c99fd-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c99fd-107">Visual Studio 2010 kullanarak CompensableActivity.sln açın.</span><span class="sxs-lookup"><span data-stu-id="c99fd-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="c99fd-108">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c99fd-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c99fd-109">F5 tuşuna basarak uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c99fd-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c99fd-110">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c99fd-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c99fd-111">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c99fd-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c99fd-112">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c99fd-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c99fd-113">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c99fd-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`