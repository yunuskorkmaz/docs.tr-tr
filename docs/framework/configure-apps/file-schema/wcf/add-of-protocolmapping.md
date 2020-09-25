---
title: <add> / <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 46ba21b65f524f88bfce81739f0cd73040a2ad45
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205015"
---
# <a name="add-of-protocolmapping"></a>\<add> / \<protocolMapping>

Bir Aktarım Protokolü şeması (örn. http, net. TCP, net. pipe, vb.) ve bir Windows Communication Foundation (WCF) bağlaması arasındaki varsayılan protokol eşlemesini temsil eder. Çalışma zamanında varsayılan uç noktalar oluştururken, WCF yapılandırılan eşlemelere bakar ve belirli bir tabanlı adres için hangi bağlamanın kullanılacağına karar verir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|Varsayılan uç nokta oluşturma sırasında bir uç nokta için kullanılacak bağlama türünü belirten bir dize.|  
|bindingConfiguration|Başvurulacak bağlama yapılandırma bölümünün adını belirten bir dize.|  
|düzen|Varsayılan uç nokta için kullanılacak Aktarım Protokolü şeması.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vs.) ve Windows Communication Foundation (WCF) bağlamaları arasında varsayılan protokol eşlemelerini tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki yapılandırma örneği machine.config dosyasında varsayılan protokol eşlemesini gösterir. machine.config dosyasını değiştirerek makine düzeyinde bu varsayılan eşlemeyi geçersiz kılabilirsiniz. Ya da uygulamayı yalnızca bir uygulamanın kapsamında geçersiz kılmak istiyorsanız, uygulama yapılandırma dosyanızda bu bölümü geçersiz kılabilir ve ayrı protokol şemaları için eşlemeyi değiştirebilirsiniz.  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
