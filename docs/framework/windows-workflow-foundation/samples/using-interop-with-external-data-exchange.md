---
title: Dış veri değişimi ile birlikte çalışması kullanarak
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 534321e5b5568e0dd0988333dc98ccc18ff33df8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616318"
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="74fb8-102">Dış veri değişimi ile birlikte çalışması kullanarak</span><span class="sxs-lookup"><span data-stu-id="74fb8-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="74fb8-103"><xref:System.Activities.Statements.Interop> Etkinliği içinde Windows Workflow Foundation'a (WF) gelen etkinlikleri yürütmek için kullanılabilir [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) ve iş akışı içinde Windows Workflow Foundation'da [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span><span class="sxs-lookup"><span data-stu-id="74fb8-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from Windows Workflow Foundation (WF) in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="74fb8-104">Bu örnek, yapılandırmak ve kullandığı WF3 iş akışı çalıştırma işlemi gösterilmektedir <xref:System.Workflow.Activities.ExternalDataExchangeService> (ve yöntemlerini çağırmaya ve olayları işleme için karşılık gelen özel etkinlikler) kullanarak <xref:System.Activities.Statements.Interop> WF4 iş akışı hizmeti içinde etkinlik.</span><span class="sxs-lookup"><span data-stu-id="74fb8-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74fb8-105">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="74fb8-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74fb8-106">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="74fb8-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74fb8-107">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="74fb8-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74fb8-108">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="74fb8-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="74fb8-109">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="74fb8-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="74fb8-110">ExternalDataExchange.sln açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74fb8-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="74fb8-111">Örneği oluşturmak için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="74fb8-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="74fb8-112">Örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74fb8-112">To run the sample, press F5.</span></span>
