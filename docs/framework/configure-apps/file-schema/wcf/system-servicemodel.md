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
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399451"
---
# \<system.serviceModel>
Bu yapılandırma bölümü, tüm Windows Communication Foundation (WCF) ServiceModel yapılandırma öğelerini içerir.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
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
 Yok  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|Bu bölüm, ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .  Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar. Her davranış öğesi, benzersiz özniteliği tarafından tanımlanır `name` .|  
|[\<bindings>](bindings.md)|Bu bölüm, standart ve özel bağlamaların bir koleksiyonunu içerir. Her giriş, benzersiz olarak tanımlanır `name` . Hizmetler, kullanarak bağlama yoluyla bağlamaları kullanır `name` .|  
|[\<client>](client.md)|Bu bölüm, bir istemcinin hizmete bağlanmak için kullandığı uç noktaların listesini içerir.|  
|[\<comContracts>](comcontracts.md)|Bu bölümde, WCF ve COM birlikte çalışma için etkinleştirilen COM sözleşmeleri tanımlanmaktadır.|  
|[\<commonBehaviors>](commonbehaviors.md)|Bu bölüm yalnızca Machine. config dosyasında tanımlanabilir. Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .  Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.  Bir davranış hem hem de bölümlerinde tanımlanmışsa `<commonBehaviors>` `<behaviors>` , \<behaviors> bölümdeki davranışa tercih edilir.|  
|[\<diagnostics>](diagnostics.md)|Bu bölüm, WCF 'nin tanılama özelliklerinin ayarlarını içerir. Kullanıcı izlemeyi, performans sayaçlarını ve WMI sağlayıcısını etkinleştirebilir/devre dışı bırakabilir ve özel ileti filtreleri ekleyebilir.|  
|[\<extensions>](extensions-section.md)|Bu bölüm, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantı yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.|  
|[\<protocolMapping>](protocolmapping.md)|Bu bölüm, Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vb.) ve WCF bağlamaları arasında bir varsayılan protokol eşlemesi kümesi tanımlar.|  
|[\<routing>](routing.md)|Bu bölüm, gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü ve <xref:System.ServiceModel.Dispatcher.MessageFilter> bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlar.|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Bu bölüm, belirli bir aktarım için hizmet barındırma ortamının ne tür bir örneklenme olduğunu tanımlar. Bu bölüm boşsa, varsayılan tür kullanılır.|  
|[\<services>](services.md)|Bölüm bir hizmetler koleksiyonu içerir. Derlemede tanımlanan her hizmet için bu öğe, `service` hizmetin ayarlarını belirten bir öğesi içerir.|  
|[\<standardEndpoints>](standardendpoints.md)|Bu bölüm bir standart uç nokta koleksiyonunu tanımlar, bu, önceden yapılandırılmış son nokta olarak kullanılabilir. Standart bir uç noktada bir veya daha fazla adres, bağlama ve anlaşma özniteliği sabit bir değere ayarlanmış olur. Örneğin, bulma uç noktasında sözleşmenin düzeltilmesi. Ayrıca, özel bağlamaları tanımlamaya benzer yeni özelliklerle hizmet uç noktasını genişletmek için standart uç noktaları kullanabilirsiniz.|
|[\<tracking>](tracking-of-wcf.md)|Bu bölüm, bir iş akışı hizmeti için izleme ayarlarını tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<configuration>|Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 WCF, diğer ürünlerin yapılandırma bölümlerine öğe eklemez.  
  
 WCF Hizmetleri, `services` yapılandırma dosyasının bölümünde tanımlanmıştır. Bir derleme, herhangi bir sayıda hizmeti içerebilir. Her hizmetin kendi `service` yapılandırma bölümü vardır. Bölümü ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.  
  
 Yalnızca bir hizmetin `name` özniteliği gereklidir.  Varsayılan olarak, bir hizmetin adı bir hizmeti uygulamak için kullanılan temel CLR türünü tanımlar; Ancak, <xref:System.ServiceModel.ServiceContractAttribute> clr türü gereksinimini geçersiz kılmak için bir üzerinde ConfigurationName özelliğini değiştirebilirsiniz.  
  
 `behaviorConfiguration`Özniteliği isteğe bağlıdır. Bir hizmet tarafından kullanılan hizmet davranışını tanımlar. Bu öznitelik tarafından belirtilen davranışın aynı yapılandırma dosyası kapsamında (yani aynı dosya veya bir üst dosya) tanımlanmış bir hizmet davranışına bağlanması gerekir.  
  
 Her hizmet bir öğede tanımlanan bir veya daha fazla uç noktayı kullanıma sunar `endpoint` . Her uç noktanın kendi adresi ve bağlaması vardır. Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.  
  
 Bağlamalar, ve öznitelikleri birleşimi aracılığıyla uç noktalara bağlanır `name` `bindingConfiguration` . `binding`Özniteliği, bağlamanın hangi bölümünde tanımlandığını tanımlar. `bindingConfiguration`Özniteliği, bağlama bölümünde hangi yapılandırılan bağlamanın kullanıldığını tanımlar. Bağlama bölümü, yapılandırılmış çeşitli bağlamaları tanımlayabilir.  
  
## <a name="example"></a>Örnek  
 Bu, WCF yapılandırma dosyasına bir örnektir.  
  
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
