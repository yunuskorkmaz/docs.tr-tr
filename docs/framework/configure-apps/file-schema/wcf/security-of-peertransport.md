---
title: <security> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399776"
---
# <a name="security-of-peertransport"></a>\<security> / \<peerTransport>
Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi bir eş kanalla ilişkili güvenlik ayarlarını içerir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`mode`|Uygulanacak güvenlik türünü belirtir. Varsayılan değer Iletidir. Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .|  
  
## <a name="mode-attribute"></a>mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenlik devre dışı bırakıldı.|  
|`Transport`|Güvenlik, HTTPS kullanılarak sağlanır.|  
|`Message`|SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.|  
|`TransportWithMessageCredential`|HTTPS kimlik doğrulaması ve gizlilik sağlar. SOAP iletileri zengin kimlik bilgisi türleri sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|Özel bağlama için bir eş taşıma tanımlar. Bu öğe, `clientCredentialType` bir hizmetle etkileşim kurarken kullanılacak kimlik bilgilerini belirten bir özniteliğe sahiptir. Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .<br /><br /> Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|Özel bağlama için bir eş taşıma tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Aktarım Güvenliği](../../../wcf/feature-details/transport-security.md)
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
