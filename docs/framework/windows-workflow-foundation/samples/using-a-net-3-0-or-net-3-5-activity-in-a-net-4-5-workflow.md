---
title: .NET Framework 3.0 veya .NET Framework 3.5 etkinliği bir .NET Framework 4.5 iş akışında kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64c0e4b6e84f442b6e34f0cbd442ae04e2a9d0b5
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="3091f-102">.NET Framework 3.0 veya .NET Framework 3.5 etkinliği bir .NET Framework 4.5 iş akışında kullanma</span><span class="sxs-lookup"><span data-stu-id="3091f-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="3091f-103"><xref:System.Activities.Statements.Interop> Etkinlik içinde .NET Framework 3.0 Windows Workflow Foundation (WF) etkinlik çalıştırmanıza olanak sağlar bir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] iş akışı.</span><span class="sxs-lookup"><span data-stu-id="3091f-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 Windows Workflow Foundation (WF) activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="3091f-104">Bu örnek nasıl kullanılacağı ortaya <xref:System.Activities.Statements.Interop> özel bir bağımsız değişken olarak bir dizeyi geçirmek için etkinlik [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3091f-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="3091f-105">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="3091f-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="3091f-106">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], SimpleInterop.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="3091f-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="3091f-107">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3091f-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="3091f-108">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3091f-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3091f-109">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3091f-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3091f-110">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3091f-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3091f-111">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3091f-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3091f-112">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3091f-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="3091f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3091f-113">See Also</span></span>
