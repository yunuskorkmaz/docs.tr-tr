---
title: Gösterme ve ActivityActions çağırma
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 2d369ec4b028b047ce02016dd511c1c088b46a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513158"
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="cf471-102">Gösterme ve ActivityActions çağırma</span><span class="sxs-lookup"><span data-stu-id="cf471-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="cf471-103">Bu örnek sahip özel bir aktivite geliştirme yapmayı gösteren bir <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="cf471-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="cf471-104">Ayrıca uygulaması sağlayarak bu etkinliği kullanın yapmayı gösteren <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="cf471-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="cf471-105">Bir <xref:System.Activities.ActivityAction> belirli imzaları ile "delik burada etkinliği kullanıcı takın özel bir davranış" kullanıma sunmak bir etkinlik Yazar verir.</span><span class="sxs-lookup"><span data-stu-id="cf471-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="cf471-106">Örneğin, <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` etkinliği (öğeleri koleksiyonu faaliyet), sahip bir <xref:System.Activities.ActivityAction> Etkinlik geçerli yineleme öğede çalışır davranışı takın kullanıcıya izin verir.</span><span class="sxs-lookup"><span data-stu-id="cf471-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cf471-107">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="cf471-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cf471-108">Açık **ActivityAction.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf471-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf471-109">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf471-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf471-110">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf471-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf471-111">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cf471-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cf471-112">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cf471-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf471-113">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cf471-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`