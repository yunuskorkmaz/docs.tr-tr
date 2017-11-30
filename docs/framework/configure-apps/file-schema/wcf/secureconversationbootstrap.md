---
title: '&lt;secureConversationBootstrap&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8b29b9b4253e51f8cc1d0625fb27998a2d10b3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecureconversationbootstrapgt"></a>&lt;secureConversationBootstrap&gt;
Güvenli Konuşmayla hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
\<secureConversationBootstrap >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<secureConversationBootstrap  
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
   defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
   requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
   messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean" >  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean" />  
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|İsteğe bağlı. Serileştirilmiş belirteci üzerinde cevap kullandıysanız belirten bir Boole değeri. Varsayılan değer `false` şeklindedir. Bir çift bağlama kullanırken, ayarı varsayılan olarak `true` yapılan herhangi bir ayarı göz ardı edilir.|  
|`authenticationMode`|Başlatıcı hem Yanıtlayıcı arasında kullanılan SOAP kimlik doğrulama modunu belirtir.<br /><br /> SspiNegotiated varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Standartlaştırma, Özet, KeyWrap, imza, şifreleme algoritmalarının ve KeyDerivation algoritmaları çeşitli güvenlik algoritması paketi tanımlar. Her güvenlik algoritması paketlerinin farklı Bu parametreler için değerler tanımlar. İleti tabanlı güvenlik, bu algoritmalar kullanılarak gerçekleştirilir.<br /><br /> Bu öznitelik, bir dizi varsayılandan farklı algoritmalar için çevrilir farklı bir platform ile çalışırken kullanılır. Bu ayardaki değişiklikler yaparken gücü ve ilgili algoritmalarının zayıf farkında olmalıdır. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Varsayılan, `Basic256` değeridir.|  
|`includeTimestamp`|Zaman damgaları yer alan her ileti dahil olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`keyEntropyMode`|İletileri güvenli hale getirme için anahtar hesaplanır yolunu belirtir. Anahtarları istemci anahtar malzemesi üzerinde yalnızca, hizmet anahtar malzemesi yalnızca veya her ikisinin birleşimini temel alabilir. Geçerli değerler şunlardır:<br /><br /> -ClientEntropy: Oturum anahtarı anahtar malzemesi sağlanan istemci temel alır.<br />-ServerEntropy: Oturum anahtarı anahtar malzemesi sağlanan hizmeti devre dışı temel alır.<br />-CombinedEntropy: Oturum anahtarı devre dışı istemci temel alır ve anahtar malzemesini sağlanmaktadır.<br /><br /> CombinedEntropy varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Hangi iletisinde düzeyi güvenlik algoritmaları iletiye uygulanma sırası ayarlar. Geçerli değerler şunlardır:<br /><br /> -SignBeforeEncrypt: ilk kez oturum sonra şifreleyin.<br />-SignBeforeEncryptAndEncryptSignature: Oturum, şifreleme ve imza şifrelemek.<br />-EncryptBeforeSign: ilk şifrelemek sonra oturum açın.<br /><br /> WS güvenliği 1.1 ile karşılıklı sertifikalar kullanılarak olduğunda, SignBeforeEncryptAndEncryptSignature varsayılan değeri kullanır.  SignBeforeEncrypt WS-Security 1.0 ile varsayılan değerdir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Kullanılan WS-güvenlik sürümünü ayarlar. Geçerli değerler şunlardır:<br /><br /> -WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> WSSecurityXXX2005 varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Özgün kanıtını anahtarları anahtarları türetilmiş olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`requireSecurityContextCancellation`|Güvenlik bağlamı iptal ve gerekir artık gerekli olmadığında sonlandırıldı olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`requireSignatureConfirmation`|WS güvenliği imza onayı etkin olup olmadığını belirten bir Boole değeri. Ayarlandığında `true`, ileti imzalarını Yanıtlayıcı tarafından onaylanır. Varsayılan, `false` değeridir.<br /><br /> İmza onayı hizmet isteği tam tanıma yanıt verdiğini doğrulamak için kullanılır.|  
|`securityHeaderLayout`|Güvenlik üstbilgi öğeleri sıralama belirtir. Geçerli değerler şunlardır:<br /><br /> -Kesin. Öğeler "kullanılmadan önce bildirmek" Genel İlkesi göre güvenlik üstbilgisi eklenir.<br />-Belirsiz. Öğeleri için WSS onaylar herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP iletisi güvenlik.<br />-LaxWithTimestampFirst. Öğeleri için WSS onaylar herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP iletisi güvenlik dışında güvenlik üstbilgisi ilk öğe wsse:Timestamp öğesi olması gerekir.<br />-LaxWithTimestampLast. Öğeleri için WSS onaylar herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP iletisi güvenlik dışında güvenlik üstbilgisi son öğesi wsse:Timestamp öğesi olması gerekir.<br /><br /> Strict varsayılandır.<br /><br /> Bu öğe türünde <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İssuermetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Geçerli bir verilen belirteç belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Bu bağlama için yerel bir istemci güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Bu bağlama için yerel bir hizmet güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel bağlama güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
