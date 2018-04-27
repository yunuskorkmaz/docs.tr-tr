---
title: Dış veri Exchange ile birlikte çalışabilirliği kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4acec4209ddadd181774ae754cb1d6b94a21685e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="using-interop-with-external-data-exchange"></a>Dış veri Exchange ile birlikte çalışabilirliği kullanma
<xref:System.Activities.Statements.Interop> Etkinlik içinde Windows Workflow Foundation (WF) gelen etkinlikleri yürütmek için kullanılabilir [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) ve Windows Workflow Foundation iş akışlarını [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). Bu örnek, yapılandırmak ve kullandığı WF3 iş akışını çalıştırmak gösterilmiştir <xref:System.Workflow.Activities.ExternalDataExchangeService> (ve yöntemleri çağırma ve olayları işlemek için karşılık gelen özel etkinlikleri) kullanarak <xref:System.Activities.Statements.Interop> WF4 iş akışı hizmeti etkinliğinde.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ExternalDataExchange.sln dosyasında açma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Örneği oluşturmak için CTRL + SHIFT + B tuşuna basın.  
  
3.  Örneği çalıştırmak için F5 tuşuna basın.
