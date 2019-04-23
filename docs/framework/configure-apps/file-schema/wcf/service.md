---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 68bddc01b02d9885b3f0fc4c2cbc5c3249de03f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197964"
---
# <a name="service"></a>\<Hizmet >
`service` Öğesi Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir. Ayrıca, açığa çıkaran hizmet uç noktaları içerir.  
  
 \<system.ServiceModel>  
\<Hizmetleri >  
\<Hizmet >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|behaviorConfiguration|Hizmeti örneklemek için kullanılacak davranış adını içeren bir dize. Davranış adı, hizmet tanımlı bir noktada kapsam içinde olması gerekir. Varsayılan değer boş bir dizedir.|  
|name|Oluşturulacak hizmet türünü belirten bir dize özniteliği gerekli. Bu ayar, geçerli bir tür için değer gerekir. Biçiminde olmalıdır `Namespace.Class.`|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|Bir koleksiyonu `endpoint` kullanıma sunan bu hizmet öğeleri.|  
|[\<konak >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Bu hizmet örneğinin konak belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Tüm WCF yapılandırma öğelerinin kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmetleri tanımlanmış `services` yapılandırma dosyasının. Derleme Hizmetleri herhangi bir sayıda içerebilir. Her hizmet kendi sahip `service` yapılandırma bölümü. Bu bölümde ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktaları tanımlayın.  
  
 `behaviorConfiguration` Öğesi, aynı zamanda isteğe bağlıdır. Bu hizmetin davranışı tanımlar kullanır. Bu öznitelikte belirtilen davranışı kapsamında aynı yapılandırma dosyasında bir davranış bağlanmanız gerekir.  
  
 Her hizmet kendi adres ve bağlama sahip olduğu bir veya daha fazla uç nokta kullanıma sunar. Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir. Bağlama özniteliklerinin birleşimiyle uç noktalarına bağlı olan `name` ve `bindingConfiguration`. `name` Özniteliği bağlama tanımlanmış bölümünde açıklanmaktadır. `bindingConfiguration` Özniteliği, bağlama bölüm içindeki hangi yapılandırma kullanıldığını tanımlar. Bir bağlama bölümü birkaç yapılandırmaları tanımlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu, bir hizmet yapılandırması örneğidir.  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [Hizmetleri Yapılandırma](../../../../../docs/framework/wcf/configuring-services.md)
