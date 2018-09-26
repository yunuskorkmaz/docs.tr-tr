---
title: İş akışı Yönetimi uç nokta örneği
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 3d99cbef20895381f5e40ee939e1d94a409f1391
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078402"
---
# <a name="workflow-management-endpoint-sample"></a>İş akışı Yönetimi uç nokta örneği
Bu örnek, bir iş akışı denetim uç noktası oluşturma ve yerel olarak ve Uzaktan iş akışlarını çalıştırmak için nasıl kullanılabileceğini gösterir. Örnek, bir denetim uç noktası ana bilgisayar ve istemcileri yazma gösterir oluşturmak ve bir iş akışı örneğini çalıştırmak için denetim uç noktası çağrısı. İş akışı, bir hizmeti değil.  
  
 Örnek sunucusu tarafında WorkflowServiceHost ile iş akışı barındırılır ve istemcilerin denetimi işlemleri (askıya alma, Başlat, vb.) gerçekleştirebilmeleri için bir WorkflowControlEndpoint eklenir. Kullanıcı tanımlı bir CreationEndpoint oluşturulacak iş akışının izin vermek için de eklenir. Hizmet, ardından iş akışını askıya alınmış durumda başlatmak için bu uç noktaları kullanır ve ardından iş akışını sürdürmek. İstemci aynı işlemleri gerçekleştirir. ancak bu, istemci kodu. Bunlar hakkında daha fazla bilgi için bkz arabirimleri için [iş akışı denetim uç noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) ve [nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  ManagementEndpoint.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın veya seçin **Çözümü Derle** gelen **derleme** menüsü.  
  
4.  ManagementEndpoint.exe uygulamayı başlatın.  
  
5.  Client.exe uygulamayı başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`