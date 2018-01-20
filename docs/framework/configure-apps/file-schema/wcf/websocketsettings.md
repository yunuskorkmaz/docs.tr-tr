---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01bc858aeeff750baa3f54e813dea5c9779143f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltwebsocketsettingsgt"></a>&lt;webSocketSettings&gt;
Web yuvasını ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.  
  
\<system.ServiceModel>  
\<bağlamaları >  
\<netHttpBinding>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|createNotificationOnConnection|Bağlantıda bir bildirim gönderilip gönderilmeyeceğini belirtir.|  
|disablePayloadMasking|Web yuvasını maskeleme etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|keepAliveInterval|Canlı tutma aralığını belirtir.|  
|maxPendingConnections|Gönderme hizmeti üzerinde bekleyen bağlantı sayısını belirtir.|  
|receiveBufferSize|Alış arabelleğinin boyutunu belirtir.|  
|sendBufferSize|Gönderme arabellek boyutunu belirtir.|  
|subProtocol|Web yuvasını subprotocol belirtir.|  
|transportUsage|Ne zaman Web yuvalarını kullanılacağını belirtir.|  
  
## <a name="transportusage-attribute"></a>transportUsage özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|WhenDuplex|Sözleşme çift yönlü olduğunda Web yuvasını protokolünü kullanır.|  
|Her zaman|Her zaman sözleşme bağımsız olarak Web yuvasını protokolünü kullanır.|  
|Hiçbir zaman|Hiçbir zaman Web yuvasını protokolünü kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<netHttpBinding>|NetHttpBinding belirtir|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir \<webSocketSettings > öğesi.  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
