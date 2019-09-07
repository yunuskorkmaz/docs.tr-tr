---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 6cc8b80edb3206bb2ef3a8a1ffa34ab40af77612
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398148"
---
# <a name="client"></a>\<İstemci >
Öğesi `client` , bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<İstemci >**  
  
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
|[\<uç nokta >](endpoint-of-client.md)|Bu istemcinin bağlanabileceği uç noktaları belirten bir uç nokta öğeleri koleksiyonu içerir.|  
|[\<meta veri >](metadata.md)|Meta verileri işlemeye yönelik ayarları içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bölümü `client` , bir istemcinin bağlanabileceği uç noktaların listesini tanımlar. İstemci bölümünde listelenen her bir uç nokta kendi bağlamasını, davranışını ve sözleşmesini tanımlar. `name` Ve`contract` özniteliklerinin birleşimiyle benzersiz şekilde tanımlanır. İstemci kodu, `name` istemcinin uyguladığı hizmet için bir uç noktaya bağlanmak üzere öğesini belirtir. `name` Özniteliği atlanırsa, uç noktası uyguladığı sözleşmenin varsayılan uç noktası olarak davranır.  
  
 Ayrıca, bu bölüm meta verileri işlemeye yönelik ayarları da belirtir.  
  
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
- [WCF İstemci Yapılandırması](../../../wcf/feature-details/client-configuration.md)
- [İstemciler](../../../wcf/feature-details/clients.md)
