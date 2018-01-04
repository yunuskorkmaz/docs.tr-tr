---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02bf740794b1551d3b130922939dbb27e572578e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemservicemodelgt"></a>&lt;system.serviceModel&gt;
Bu yapılandırma bölümü tüm içeren [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel yapılandırma öğeleri.  
  
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
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışları >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Bu bölümde adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından tüketilen davranışı öğeleri tanımlar. Her davranış öğesi kendi benzersiz tanımlanır `name` özniteliği.|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu bölümde, standart ve özel bağlamaları koleksiyonu tutar. Her giriş kendi benzersiz tarafından tanımlanan `name`. Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`.|  
|[\<İstemci >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Bu bölüm, bir istemcinin bir hizmete bağlanmak için kullandığı bitiş noktaları listesini içerir.|  
|[\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Bu bölümde, WCF ve COM birlikte çalışma için etkin COM sözleşmeleri tanımlar.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|Bu bölümü yalnızca machine.config dosyasındaki tanımlanabilir. Adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her bir koleksiyon tarafından tüketilen davranışı öğeleri tanımlayan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uç noktaları ve hizmetler makinedeki sırasıyla.  Bir davranış ikisi de tanımlanmışsa `<commonBehaviors>` ve `<behaviors>` bölümlerinde, davranış \<davranışları > bölümü tercih verilen.|  
|[\<Uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Bu bölüm, kullanıcı tanımlı bağlamalar, davranışları ve diğer yönlerini uzantıları oluşturmak kullanıcı etkinleştirme uzantıları koleksiyonu içerir.|  
|[\<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Bu bölümde WCF'nin tanılama özelliklerine yönelik ayarları içerir. Kullanıcı etkinleştirebilir/izleme, performans sayaçları ve WMI sağlayıcısı devre dışı bırakabilir ve özel ileti filtreleri ekleyebilirsiniz.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Bu bölümde Aktarım Protokolü düzenleri (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokolü eşleme kümesini tanımlar.|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Bu bölümde türünü belirleme yönlendirme bir filtre kümesi tanımlar [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman bir filtre ile eşleşen iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Bu bölümde, ne tür bir barındırma ortamı için özel bir taşıma başlatır hizmeti tanımlar. Bu bölümde boşsa, varsayılan türü kullanılır.|  
|[\<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Bölüm hizmetler koleksiyonu içerir. Derlemede tanımlanan her hizmet için bu öğeyi içeren bir `service` öğesi hizmeti ayarlarını belirtme.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Bu bölümde, yeniden kullanılabilir önceden yapılandırılmış uç nokta standart uç noktaları koleksiyonu tanımlar. Standart bir uç noktası bir erişebilir veya adresi, bağlama ve sözleşme öznitelikleri daha fazla sabit bir değere ayarlayın. Örneğin, bulma uç sözleşme sabittir. Standart uç noktaları, özel bağlamaları tanımlamak için benzer yeni özelliklerle Hizmeti uç noktası genişletmek için de kullanabilirsiniz.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<Yapılandırma >|Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]öğeleri diğer ürünleri yapılandırma bölümlerini eklemez.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]Hizmetleri tanımlanmış `services` yapılandırma dosyasının. Bir derlemeyi Hizmetleri herhangi bir sayıda içerebilir. Her hizmetin kendi vardır `service` yapılandırma bölümü. Bölüm ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktalarına tanımlayın.  
  
 Yalnızca bir hizmetin `name` özniteliği gereklidir.  Varsayılan olarak, bir hizmetin adı bir hizmet uygulamak için kullanılan temel CLR türü açıklanır; Ancak, üzerinde ConfigurationName özelliği değişebilir bir <xref:System.ServiceModel.ServiceContractAttribute> CLR türü gereksinimini geçersiz kılmak için.  
  
 `behaviorConfiguration` Özniteliği isteğe bağlıdır. Bir hizmeti tarafından kullanılan hizmet davranışını tanımlar. Bu özniteliği tarafından belirtilen davranışı aynı yapılandırma dosyasının (yani aynı dosya veya bir üst dosyası) kapsamda tanımlı bir hizmet davranışı bağlanmanız gerekir.  
  
 Her hizmet bir gösterir ya da daha fazla uç noktaları tanımlanan bir `endpoint` öğesi. Her uç nokta kendi adres ve bağlama vardır. Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.  
  
 Bağlamaları uç noktaları özniteliklerini birleşimi yoluyla bağlı `name` ve `bindingConfiguration`. `binding` Öznitelik tanımlar bağlama hangi bölümünde tanımlanır. `bindingConfiguration` Öznitelik tanımlar bağlama bölüm içinde yapılandırılmış hangi bağlama kullanılır. Bir bağlama bölümü birkaç yapılandırılmış bağlamaları tanımlayabilirsiniz.  
  
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
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
