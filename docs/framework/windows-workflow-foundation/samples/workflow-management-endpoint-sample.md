---
title: İş akışı Yönetimi uç nokta örnek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 558591cb645de9591fd0ac770061a5fb8825d21d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="workflow-management-endpoint-sample"></a>İş akışı Yönetimi uç nokta örnek
Bu örnek, bir iş akışı denetim uç noktası oluşturmak ve iş akışları hem yerel hem de uzaktan çalıştırmak için nasıl kullanılabileceğini gösterir. Örnek bir denetim uç noktası ana bilgisayar ve istemcileri yazma nasıl oluşturulduğunu gösteren oluşturmak ve bir iş akışı örneği çalıştırmak için denetim uç noktası çağırın. İş akışı bir hizmeti değil.  
  
 Örnek hizmet tarafında WorkflowServiceHost ile iş akışı barındırılır ve istemcilerin denetimi işlemleri (askıya alma, Başlat, vb.) gerçekleştirebilmeleri için bir WorkflowControlEndpoint eklenir. Kullanıcı tanımlı bir CreationEndpoint, iş akışının oluşturulmasına izin de eklenir. Hizmet askıya alınmış durumda iş akışını başlatmak için bu uç noktalar kullanır ve iş akışını devam ettirin. İstemci aynı işlemleri gerçekleştirir ancak istemci kodu. Bunlar hakkında daha fazla bilgi için bkz arabirimleri için [iş akışı denetim uç noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) ve [nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  ManagementEndpoint.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.  
  
4.  ManagementEndpoint.exe uygulamayı başlatın.  
  
5.  Client.exe uygulamayı başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`