---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: c176f7f470cc65bb135e5f92935102e09c7e8485
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209833"
---
# <a name="systemservicemodel"></a>\<system.serviceModel>
Bu yapılandırma bölümü, tüm Windows Communication Foundation (WCF) ServiceModel yapılandırma öğelerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışlar >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Bu bölümde adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından kullanılan davranışı öğeleri tanımlar. Her davranışı öğesi kendi benzersiz tarafından tanımlanır `name` özniteliği.|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu bölümde, standart ve özel bağlamalar koleksiyonunu tutar. Her giriş kendi benzersiz tarafından tanımlanır `name`. Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`.|  
|[\<İstemci >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Bu bölüm, bir istemcinin bir hizmete bağlanmak için kullandığı uç noktaları listesini içerir.|  
|[\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Bu bölümde, WCF ve COM birlikte çalışması için etkin COM sözleşmeleri tanımlar.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|Bu bölümü sadece machine.config dosyasında tanımlanabilir. Adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon, sırasıyla tüm WCF uç noktaları ve makinede hizmetler tarafından kullanılan davranışı öğeleri tanımlar.  Hem de bir davranış tanımlanmışsa `<commonBehaviors>` ve `<behaviors>` bölümler, davranış \<davranışları > bölüm tercih verilir.|  
|[\<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Bu bölümde, WCF tanılama özelliklerini ayarlarını içerir. Kullanıcı etkinleştirebilir/izleme, performans sayaçları ve WMI sağlayıcısı devre dışı bırakabilir ve özel ileti filtreleri ekleyebilirsiniz.|  
|[\<Uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Bu bölüm, kullanıcı tanımlı bağlamalar, davranışları ve diğer yönleri uzantıları oluşturmak kullanıcı olanak tanıyan uzantılar koleksiyonunu içerir.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Bu bölümde, taşıma protokol şemaları (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokol eşleşmelerinin bir kümesini tanımlar.|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Bu bölümde, Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlayan<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek ne zaman ileti göndermek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Bu bölümde, hizmet barındırma ortamı için belirli bir örneğini oluşturur. ne tür tanımlar. Bu bölümde boşsa, varsayılan türü kullanılır.|  
|[\<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Bölüm Hizmetleri koleksiyonunu içerir. Derlemede tanımlanan her hizmet için bu öğeyi içeren bir `service` hizmeti ayarlarını belirten öğe.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Bu bölümde, yeniden kullanılabilen önceden yapılandırılmış uç noktalar olan standart uç noktaları koleksiyonu tanımlar. Bir standart uç nokta gerekir veya daha fazla adresi, bağlama ve sözleşme öznitelikleri için sabit bir değer. Örneğin, bulma uç noktası sözleşme sabittir. Standart uç noktaları, yeni özellikleri benzer özel bağlamaları tanımlamak için olan hizmet uç noktası genişletmek için de kullanabilirsiniz.|
|[\<İzleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|Bu bölümde, bir iş akışı hizmeti için izleme ayarlarını tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<Yapılandırma >|Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 WCF öğeleri diğer ürünleri yapılandırma bölümlerini eklemez.  
  
 WCF hizmetleri tanımlanmış `services` yapılandırma dosyasının. Derleme Hizmetleri herhangi bir sayıda içerebilir. Her hizmet kendi sahip `service` yapılandırma bölümü. Bölümü ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktaları tanımlayın.  
  
 Yalnızca bir hizmetin `name` özniteliği gereklidir.  Varsayılan olarak, bir hizmetin adı bir hizmeti uygulamak için kullanılan temel alınan CLR türü açıklar; Ancak, üzerinde ConfigurationName özelliği değişebilir bir <xref:System.ServiceModel.ServiceContractAttribute> CLR türü gereksinimi geçersiz kılmak için.  
  
 `behaviorConfiguration` İsteğe bağlı öznitelik. Bu, bir hizmet tarafından kullanılan hizmet davranışını tanımlar. Bu özniteliği tarafından belirtilen davranışı aynı yapılandırma dosyasının (yani, aynı dosya veya üst dosyası) kapsamında tanımlanan bir hizmet davranışını bağlanmanız gerekir.  
  
 Hizmet her bir sunar veya daha fazla uç noktaları tanımlanan bir `endpoint` öğesi. Her uç nokta, kendi adres ve bağlama vardır. Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.  
  
 Bağlamaları özniteliklerinin birleşimiyle uç noktalarına bağlı olan `name` ve `bindingConfiguration`. `binding` Öznitelik tanımlar bağlama hangi bölümde tanımlanmaktadır. `bindingConfiguration` Özniteliği, hangi yapılandırılmış bağlama bağlama bölümü içinde kullanılan tanımlar. Bir bağlama bölümü birkaç yapılandırılmış bağlama tanımlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu, WCF yapılandırma dosyasına örneğidir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
