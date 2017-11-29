---
title: "Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ff5d45997456c12d0292176771ad3c332f6c043
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme
Keşif proxy'si farklı bulma sürümlerini kullanan birden fazla bulma uç noktası getirebilir. Bir UDP, çok noktaya yayın araştırma isteğinin proxy çok noktaya yayın gizleme iletisiyle yanıt vermesi gerektiğini proxy ulaştığında. Bunu yapmak için bir istek bulma sürümü bilmesi gerekir.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Bir araştırma isteğinin keşif sürümünü belirleme  
  
1.  Bir araştırma isteğine yanıt yöntemi (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) statik kullanmak <xref:System.ServiceModel.OperationContext.Current%2A> özelliğini araması için bir <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> aşağıdaki kodda gösterildiği gibi.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [Keşif proxy'si ekleme](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Keşif Proxy örneği](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
