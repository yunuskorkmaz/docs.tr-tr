---
title: 'Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 6bd112be311eb9397ad89801be5358d67c7499fd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332280"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme
Keşif proxy'si farklı bulma sürümlerini kullanan birden fazla bulma uç noktası getirebilir. Bir UDP, çok noktaya yayın araştırma isteğinin proxy bir çok noktaya yayın gizleme ileti ile yanıt vermelidir proxy ulaşır. Bunu yapmak için isteğinin keşif sürümünü bilmesi gerekir.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Bir araştırma isteğinin keşif sürümünü belirleme  
  
1. Bir araştırma isteğine yanıt vermeden yöntem (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) statik <xref:System.ServiceModel.OperationContext.Current%2A> aramak için özellik bir <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> aşağıdaki kodda gösterildiği gibi.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Keşif Proxy'si Ekleme](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
