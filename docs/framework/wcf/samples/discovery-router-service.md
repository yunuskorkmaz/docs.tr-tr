---
title: Keşif Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 09309b23d2a3cc672811c2f617e6fb81a2b4e021
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712282"
---
# <a name="discovery-router-service"></a>Keşif Yönlendirme Hizmeti
Bu örnek, bulma iletilerinin başka bir uç noktaya nasıl iletileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösterir  
 Bulma yönlendirmesi  
  
## <a name="discussion"></a>Tartışma  
 Bulma yönlendirmesi, bir istemcinin proxy kullanarak hizmet arayan ve proxy 'nin böyle bir hizmetin farkında olduğu, ancak başka bir proxy 'nin bildiği bir senaryoda yararlıdır. Bu proxy, bulma paketini bu istemciden ikinci proxy 'ye iletebilir. İkinci proxy hizmeti arayabilir ve özgün istemciye yanıtları döndürebilir.  
  
 Bu örnekte, bir istemci bulma yönlendirme bileşenine bir ileti gönderir. Bu ileti, bulma yönlendiricisinde belirli bir uç noktaya gönderilir. Yönlendirici daha sonra iletiyi bir UDP çok noktaya yayın uç noktasına iletir. Araştırma iletisi çok noktaya yayın uç noktasına gider ve bir UDP çok noktaya yayın adresini dinleyen bir hizmet, bu bulma yönlendiricisine yanıt verir. Bulma yönlendiricisi yanıtları toplar ve istemciye geri gönderir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Örneği oluşturun.  
  
2. DiscoveryRouter yürütülebilir dosyasını çalıştırın.  
  
3. Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.  
  
4. İstemci yürütülebilir dosyasını çalıştırın. İstemcinin hizmeti konumlandırır olduğunu unutmayın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
