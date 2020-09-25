---
title: <behavior> / <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: d191b968e1c3fd1db0837ba7e03f210a1b00062d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201505"
---
# <a name="behavior-of-endpointbehaviors"></a>\<behavior> / \<endpointBehaviors>

`behavior`Öğesi, bir uç nokta davranışı için ayarların bir koleksiyonunu içerir. Her davranış tarafından dizine kendi `name`. Uç noktalar, bu ad aracılığıyla her davranışa bağlantı verebilir. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Davranışın yapılandırma adını içeren benzersiz bir dize. Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
|[\<callbackDebug>](callbackdebug.md)|Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.|  
|[\<callbackTimeouts>](callbacktimeouts.md)|İstemci geri çağırması için zaman aşımını belirtir.|  
|[\<clientVia>](clientvia.md)|Bir iletinin gerçekleşmesi gereken yolu belirtir.|  
|[\<dataContractSerializer>](datacontractserializer.md)|DataContractSerializer için yapılandırma verilerini içerir.|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.|  
|[\<enableWebScript>](enablewebscript.md)|Hizmeti ASP.NET AJAX web sayfalarından tüketmek mümkün kılan uç nokta davranışını sağlar. Davranış yalnızca \<webHttpBinding> Standart bağlama veya \<webMessageEncoding> bağlama öğesiyle birlikte kullanılmalıdır.|  
|[\<endpointDiscovery>](endpointdiscovery.md)|Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.|  
|[\<soapProcessing>](soapprocessing.md)|Farklı bağlama türleri ve ileti sürümleri arasındaki iletileri sıralamak için kullanılan istemci uç noktası davranışını tanımlar.|  
|[\<synchronousReceive>](synchronousreceive-element.md)|Bir hizmet veya istemci uygulamasında ileti almak için çalışma zamanı davranışını belirtir. Hiçbir özniteliğe veya alt öğeye sahip değil.|  
|[\<transactedBatching>](transactedbatching.md)|İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.|  
|[\<webHttp>](webhttp.md)|Yapılandırma yoluyla bir uç noktada WebHttpBehavior belirtir. Bu davranış, \<webHttpBinding> Standart bağlama birlikte kullanıldığında BIR WCF hizmeti Için Web programlama modelini sunar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|Uç nokta davranış öğelerinin koleksiyonu.|
