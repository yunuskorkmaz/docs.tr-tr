---
title: <peer> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50db8eb381249c3b880c4b1dd96ec3813d51ce67
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556121"
---
# <a name="peer-of-servicecredentials"></a>\<peer> / \<serviceCredentials>
Eş düğüm için geçerli kimlik bilgilerini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|Eşler arası hizmetler için iletileri imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir. .|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.|  
|[\<peerAuthentication>](peerauthentication.md)|Eş Hizmetleri için kimlik doğrulama seçeneklerini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Eşler Arası Ağ](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
