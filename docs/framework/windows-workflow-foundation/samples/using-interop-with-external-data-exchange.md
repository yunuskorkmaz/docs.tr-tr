---
title: "Dış veri Exchange ile birlikte çalışabilirliği kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a17e4a51648facbc17e6af31f65360a3414a5c15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="b352e-102">Dış veri Exchange ile birlikte çalışabilirliği kullanma</span><span class="sxs-lookup"><span data-stu-id="b352e-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="b352e-103"><xref:System.Activities.Statements.Interop> Etkinlik, etkinlikten yürütmek için kullanılabilir [!INCLUDE[wf](../../../../includes/wf-md.md)] içinde [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) ve iş akışlarından [!INCLUDE[wf2](../../../../includes/wf2-md.md)] içinde [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span><span class="sxs-lookup"><span data-stu-id="b352e-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from [!INCLUDE[wf](../../../../includes/wf-md.md)] in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within [!INCLUDE[wf2](../../../../includes/wf2-md.md)] in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="b352e-104">Bu örnek, yapılandırmak ve kullandığı WF3 iş akışını çalıştırmak gösterilmiştir <xref:System.Workflow.Activities.ExternalDataExchangeService> (ve yöntemleri çağırma ve olayları işlemek için karşılık gelen özel etkinlikleri) kullanarak <xref:System.Activities.Statements.Interop> WF4 iş akışı hizmeti etkinliğinde.</span><span class="sxs-lookup"><span data-stu-id="b352e-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b352e-105">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b352e-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b352e-106">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b352e-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b352e-107">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b352e-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b352e-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b352e-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b352e-109">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b352e-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="b352e-110">ExternalDataExchange.sln dosyasında açma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b352e-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b352e-111">Örneği oluşturmak için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b352e-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b352e-112">Örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b352e-112">To run the sample, press F5.</span></span>
