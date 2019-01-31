---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 8962a0c018442ed590b62e53ea8323d80e334df7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290101"
---
# <a name="peertransport"></a>\<peerTransport >
Özel bağlama için bir eş tanımlar.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<peerTransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|listenIpAddress|Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize. Varsayılan, `null` değeridir.|  
|maxBufferPoolSize|Arabellek havuzu en büyük boyutunu belirten pozitif bir tamsayı. 524288 varsayılandır.<br /><br /> WCF pek çok bölümünün arabellekler kullanın. Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır. Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün. Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.|  
|maxReceivedMessageSize|En büyük ileti boyutu üst bilgiler dahil bayt cinsinden tanımlayan pozitif bir tamsayı. İleti alıcısı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır.|  
|bağlantı noktası|Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı. Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>. Varsayılan değer 0'dır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Bu aktarım için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu aktarım işlemleri istek/yanıt sözleşmeleriyle kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
