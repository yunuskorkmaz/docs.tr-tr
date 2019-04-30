---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704303"
---
# <a name="client"></a>\<İstemci >
`client` Öğesi, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.  
  
 \<system.ServiceModel>  
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
|[\<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Bu istemcinin bağlanabileceği uç noktaları belirttiğiniz bitiş noktası öğelerinin bir koleksiyonunu içerir.|  
|[\<meta veri >](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|İşleme meta veri ayarlarını içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 `client` Bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar. Kendi bağlama davranışı ve sözleşme istemci bölümünde listelenen her bir uç nokta tanımlar. Birleşimiyle benzersiz şekilde tanımlanır `name` ve `contract` öznitelikleri. İstemci kodu belirtir `name` uygulayan istemci hizmeti için bir uç noktaya bağlanmak için. Varsa `name` özniteliği atlanırsa, uç nokta sözleşmesinin varsayılan uç nokta, uygular işlevi görür.  
  
 Ayrıca, bu bölümde Ayrıca işlem meta veri ayarlarını belirtir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [WCF İstemci Yapılandırması](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [İstemciler](../../../../../docs/framework/wcf/feature-details/clients.md)
