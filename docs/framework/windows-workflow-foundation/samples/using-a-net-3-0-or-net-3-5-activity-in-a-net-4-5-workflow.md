---
title: Bir .NET Framework 4.5 iş akışında .NET Framework 3.0 veya .NET Framework 3.5 etkinliği kullanma
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ec44e56a99660ba422c73bbbf00bf5ef6b7b61ff
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486137"
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="e7ac2-102">Bir .NET Framework 4.5 iş akışında .NET Framework 3.0 veya .NET Framework 3.5 etkinliği kullanma</span><span class="sxs-lookup"><span data-stu-id="e7ac2-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="e7ac2-103"><xref:System.Activities.Statements.Interop> Etkinliği sağlar, bir .NET Framework 3.0 Windows Workflow Foundation (WF) etkinliği içinde çalıştırmak bir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] iş akışı.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 Windows Workflow Foundation (WF) activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="e7ac2-104">Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.Interop> bir dize, özel bir bağımsız değişken olarak geçirmek için etkinlik [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="e7ac2-105">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e7ac2-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="e7ac2-106">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], SimpleInterop.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e7ac2-107">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e7ac2-108">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7ac2-109">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e7ac2-110">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e7ac2-111">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7ac2-112">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="e7ac2-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7ac2-113">See Also</span></span>
