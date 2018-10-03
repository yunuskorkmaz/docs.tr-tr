---
title: 'Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 98dfd5ec5d3c180b619e2f15d95037feae8ebbaf
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48031581"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme
Keşif proxy'si farklı bulma sürümlerini kullanan birden fazla bulma uç noktası getirebilir. Bir UDP, çok noktaya yayın araştırma isteğinin proxy bir çok noktaya yayın gizleme ileti ile yanıt vermelidir proxy ulaşır. Bunu yapmak için isteğinin keşif sürümünü bilmesi gerekir.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Bir araştırma isteğinin keşif sürümünü belirleme  
  
1.  Bir araştırma isteğine yanıt vermeden yöntem (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) statik <xref:System.ServiceModel.OperationContext.Current%2A> aramak için özellik bir <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> aşağıdaki kodda gösterildiği gibi.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
- [Keşif Proxy'si Ekleme](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  