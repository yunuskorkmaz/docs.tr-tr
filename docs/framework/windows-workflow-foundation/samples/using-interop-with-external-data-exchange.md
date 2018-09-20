---
title: Dış veri değişimi ile birlikte çalışması kullanarak
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 534321e5b5568e0dd0988333dc98ccc18ff33df8
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326260"
---
# <a name="using-interop-with-external-data-exchange"></a>Dış veri değişimi ile birlikte çalışması kullanarak
<xref:System.Activities.Statements.Interop> Etkinliği içinde Windows Workflow Foundation'a (WF) gelen etkinlikleri yürütmek için kullanılabilir [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) ve iş akışı içinde Windows Workflow Foundation'da [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). Bu örnek, yapılandırmak ve kullandığı WF3 iş akışı çalıştırma işlemi gösterilmektedir <xref:System.Workflow.Activities.ExternalDataExchangeService> (ve yöntemlerini çağırmaya ve olayları işleme için karşılık gelen özel etkinlikler) kullanarak <xref:System.Activities.Statements.Interop> WF4 iş akışı hizmeti içinde etkinlik.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ExternalDataExchange.sln açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Örneği oluşturmak için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Örneği çalıştırmak için F5 tuşuna basın.
