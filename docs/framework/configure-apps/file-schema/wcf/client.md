---
title: "&lt;İstemci&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f91f4462fc8c11b1769d5805a4ad1407385a50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientgt"></a>&lt;İstemci&gt;
`client` Öğe, bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar.  
  
 \<Sistem. ServiceModel >  
\<İstemci >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
    <client>  
        <endpoint>  
        </endpoint>  
                <metadata>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Bu istemcinin bağlanabileceği uç noktaları belirttiğiniz bitiş noktası öğe koleksiyonunu içerir.|  
|[\<meta veri >](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|İşleme meta veri ayarlarını içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `client` Bölümü, bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar. İstemci bölümünde listelenen her endpoint kendi bağlama davranışı ve sözleşme tanımlar. Birleşimiyle benzersiz şekilde tanımlanır `name` ve `contract` öznitelikleri. İstemci kodu belirtir `name` istemci uygulayan hizmeti için bir uç nokta bağlanmak için. Varsa `name` özniteliği atlanırsa, uç nokta sözleşme için varsayılan uç noktası, Implements görür.  
  
 Ayrıca, bu bölümde ayrıca işleme meta veri ayarlarını belirtir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [WCF istemci yapılandırması](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [İstemciler](../../../../../docs/framework/wcf/feature-details/clients.md)
