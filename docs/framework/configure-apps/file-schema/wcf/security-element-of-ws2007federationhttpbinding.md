---
title: "&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 79976b015f35bdd71a5f95a018d85c0ba41ce0b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a>&lt;ws2007FederationHttpBinding&gt; &lt;güvenlik&gt; öğesi
Güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<ws2007FederationHttpBinding >  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`mode`|İsteğe bağlı. Uygulanan güvenlik türünü belirtir. Varsayılan değer `Message` şeklindedir. Bu öznitelik türünde <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|SOAP iletisi aktarımı sırasında güvenli değildir.|  
|İleti|Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması SOAP iletisi güvenlik kullanılarak sağlanır. Varsayılan olarak, gövde imzalı ve şifrelenir. Hizmeti bir sertifikayla yapılandırılmalıdır. İstemci kimlik doğrulaması istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç temel alır.|  
|TransportWithMessageCredential|Bütünlük, gizlilik ve sunucu kimlik doğrulaması HTTPS tarafından sağlanır. Hizmeti bir sertifikayla yapılandırılmalıdır. İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır ve istemci için bir güvenlik belirteci hizmeti tarafından verilen belirteç dayanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İleti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|İleti düzeyi güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Tüm bağlama özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bir kimlik bilgisi türü seçme](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
