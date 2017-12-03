---
title: '&lt;Connectionpoolsettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3083fe7f8663007cfcc6e335b2dcf4c51d2ebc8a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltnamedpipetransportgt"></a>&lt;Connectionpoolsettings&gt;
İçinde özel bağlama eklendiğinde adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.  
  
\<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<namePipeTransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<namedPipeTransport channelInitializationTimeout="TimeSpan"   
                    connectionBufferSize="Integer"   
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
                    manualAddressing="Boolean"   
                    maxBufferPoolSize="Integer"  
                    maxBufferSize="Integer"  
                    maxOutputDelay="TimeSpan"  
                    maxPendingAccepts="Integer"   
                    maxPendingConnections="Integer"  
                    maxReceivedMessageSize="Integer"   
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">  
  <connectionPoolSettings groupName="String" 
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|ChannelInitializationTimeout|Alır veya ayarlar bir <xref:System.TimeSpan> kesilmeden önce bir kanal başlatma durumu olabilir en uzun süreyi belirler.|  
|ConnectionBufferSize|Alır veya ayarlar istemci veya hizmet hattan serileştirilmiş iletide öbeğini iletmek için kullanılan arabellek boyutu.|  
|hostNameComparisonMode|Alır veya ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer ayarlar.|  
|manualAddressing|Alır veya el ile ileti adresleme gerekip gerekmediğini belirten bir değer ayarlar.|  
|maxBufferPoolSize|Alır veya taşıma tarafından kullanılan tüm arabellek havuzu bayt cinsinden en büyük boyutu ayarlar.|  
|maxBufferSize|Alır veya ayarlar kullanılacak arabelleğin en büyük boyutu. Akış iletileri için bu değer arabelleğe alınan modunda okuma ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.|  
|maxOutputDelay|Alır veya üst aralığı gönderilmeden önce bir ileti veya tam bir ileti öbeğini bellekte arabelleğe alınan kalabileceği süreyi ayarlar.|  
|maxPendingAccepts|Alır veya bir hizmetin hizmetine gelen bağlantıları işlemek için bir dinleyici bekliyor olabilir kanalları sayısının üst sınırını ayarlar.|  
|maxPendingConnections|Alır veya gönderme hizmeti üzerinde bekleyen bağlantı sayısının üst sınırını ayarlar.|  
|MaxReceivedMessageSize|Alır ve izin verilen maksimum ileti boyutu alınabileceğini bayt cinsinden ayarlar.|  
|transferMode|Alır veya iletilerin ara belleğe veya ile bağlantı yönelimli aktarma akışı olup olmadığını belirten bir değer ayarlar.|  
|[\<Tcptransport >, \<Connectionpoolsettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|Bir adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
Bu aktarım "net.pipe://hostname/path" biçiminde URI'ler kullanır. URI bileşenlerle isteğe bağlıdır.  
  
`namedPipeTransport` Öğesidir başlangıç noktası için bir özel, bağlama oluşturma adlandırılmış kanallar aktarım protokolünü uygular. Bu aktarım için makine üzerindeki Windows Communication Foundation (WCF) - to - WCF iletişim kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
[Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)   
[Taşıma seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
[Bağlamaları](../../../../../docs/framework/wcf/bindings.md)   
[Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
[Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
[\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
