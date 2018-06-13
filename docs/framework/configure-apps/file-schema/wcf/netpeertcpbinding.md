---
title: '&lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 1b2e5030c55f8568bc418b507878ddbf202b39fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750888"
---
# <a name="ltnetpeertcpbindinggt"></a>&lt;netPeerTcpBinding&gt;
Eş kanal belirli TCP ileti için bir bağlama tanımlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netPeerTcpBinding>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|ListenIpAddress|Eş düğüm için TCP iletileri dinleyeceği bir IP adresi belirten bir dize. Varsayılan, `null` değeridir.|  
|maxBufferPoolSize|Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı. Varsayılan 524.288 (512 * 1024) bayttır. Pek çok bölümü Windows Communication Foundation (WCF) arabellekleri kullanın. Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır. Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez. Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.|  
|maxReceivedMessageSize|Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. 65536 varsayılandır.|  
|name|Bağlama yapılandırma adını içeren dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|bağlantı noktası|Bu bağlama eş kanal TCP iletilerini işleyecek ağ arabirim bağlantı noktası belirten bir tamsayı. Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>. Varsayılan değer 0'dır.|  
|receiveTimeout|A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10: 00'dır.|  
|sendTimeout|A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<Çözümleyici >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Bir eş çözümlemek için bu bağlama tarafından kullanılan bir eş çözümleyici uç noktası IP adreslerini eş kafes içindeki düğümler için kimliği kafes belirtir.|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bağlama, TCP üzerinden eş aktarım kullanılarak eşler arası veya çok taraflı uygulamalarının oluşturulması için destek sağlar. Her eş düğüm bu bağlama türü ile tanımlanmış birden çok eş kanalı barındırabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir eş kanalı kullanılarak taraflı iletişimi sağlayan NetPeerTcpBinding bağlama kullanmayı gösterir. Bu bağlama işlemini kullanma ayrıntılı senaryo için bkz [Net eş TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)  
 [NET eş TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [Eşler Arası Ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
