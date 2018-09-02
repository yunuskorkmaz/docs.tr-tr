---
title: Başlangıç başlatılan özel bir etkinlik yazma
ms.date: 03/30/2017
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
ms.openlocfilehash: 4d9c140ca230750ca1119b33252b1edb8796d458
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405234"
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="7b48d-102">Başlangıç başlatılan özel bir etkinlik yazma</span><span class="sxs-lookup"><span data-stu-id="7b48d-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="7b48d-103">Bu örnek nasıl basit bir özel etkinlik XAML içinde tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b48d-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="7b48d-104">Etkinlik adı verilen `Rhyme`, ve mantığını üç dizi <xref:System.Activities.Statements.WriteLine> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="7b48d-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b48d-105">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7b48d-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7b48d-106">Açık **Simple.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b48d-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7b48d-107">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b48d-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b48d-108">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="7b48d-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b48d-109">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b48d-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b48d-110">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7b48d-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b48d-111">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7b48d-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`