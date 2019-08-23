---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936518"
---
# <a name="service"></a>\<hizmet >
`service` Öğesi bir Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir. Ayrıca hizmeti kullanıma sunan uç noktaları da içerir.  
  
 \<system.ServiceModel>  
\<Hizmetler >  
\<hizmet >  
  
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
|behaviorConfiguration|Hizmeti başlatmak için kullanılacak davranışın davranış adını içeren bir dize. Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır. Varsayılan değer boş bir dizedir.|  
|name|Oluşturulacak hizmetin türünü belirten gerekli dize özniteliği. Bu ayar geçerli bir türe eşit olmalıdır. Biçim şu şekilde olmalıdır`Namespace.Class.`|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<uç nokta >](endpoint-element.md)|Bu hizmeti kullanıma `endpoint` sunan öğelerin koleksiyonu.|  
|[\<Ana bilgisayar >](host.md)|Bu hizmet örneğinin konağını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Hizmetler >](services.md)|Tüm WCF yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmetler, yapılandırma dosyasının `services` bölümünde tanımlanmıştır. Bir derleme, herhangi bir sayıda hizmeti içerebilir. Her hizmetin kendi `service` yapılandırma bölümü vardır. Bu bölüm ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.  
  
 `behaviorConfiguration` Öğesi de isteğe bağlıdır. Hizmetin kullandığı davranışı tanımlar. Bu öznitelikte belirtilen davranışın, aynı yapılandırma dosyasındaki kapsamdaki bir davranışa bağlanması gerekir.  
  
 Her hizmet kendi adresine ve bağlamaya sahip bir veya daha fazla bitiş noktası sunar. Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır. Bağlama, özniteliklerin `name` ve `bindingConfiguration`öğelerinin birleşimi aracılığıyla uç noktalara bağlanır. `name` Özniteliği, bağlamanın tanımlandığı bölümü tanımlar. `bindingConfiguration` Özniteliği, bağlama bölümünde hangi yapılandırmanın kullanıldığını tanımlar. Bağlama bölümü, birkaç yapılandırma tanımlayabilir.  
  
## <a name="example"></a>Örnek  
 Bu, hizmet yapılandırmasına bir örnektir.  
  
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
- [Hizmetleri Yapılandırma](../../../wcf/configuring-services.md)
