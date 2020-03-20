---
title: Keşif Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183722"
---
# <a name="discovery-router-service"></a>Keşif Yönlendirme Hizmeti
Bu örnek, keşif iletilerinin başka bir uç noktaya nasıl iletilenin nasıl gösterildiğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Keşif Yönlendirme  
  
## <a name="discussion"></a>Tartışma  
 Bulma yönlendirme, istemcinin proxy kullanarak bir hizmet aradığı ve proxy'nin böyle bir hizmetten habersiz olduğu, ancak başka bir proxy bildiği bir senaryoda yararlıdır. Bu proxy, bulma paketini bu istemciden ikinci proxy'ye iletebilir. İkinci proxy hizmeti arar ve yanıtları özgün istemciye döndürebilir.  
  
 Bu örnekte, istemci bir bulma yönlendirme bileşenine bir ileti gönderir. Bu ileti, bulma yönlendiricisindeki belirli bir bitiş noktasına gönderilir. Yönlendirici daha sonra iletiyi UDP çok noktaya yayın ucuna ileter. Sonda iletisi çok noktaya yayın ucuna gider ve UDP çok noktaya yayın adresini dinleyen bir hizmet bu keşif yönlendiricisine yanıt verir. Bulma yönlendiricisi yanıtları toplar ve istemciye geri gönderir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Örneği derleyin.  
  
2. DiscoveryRouter çalıştırılabilir çalıştırın.  
  
3. Yapı dizininden çalıştırılabilen hizmeti çalıştırın.  
  
4. İstemciyi çalıştırılabilir çalıştırın. İstemcinin hizmeti bulup bulmadığını unutmayın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
