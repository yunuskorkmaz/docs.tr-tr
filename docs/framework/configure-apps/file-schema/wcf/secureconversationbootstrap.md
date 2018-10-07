---
title: '&lt;secureConversationBootstrap&gt;'
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
author: BrucePerlerMS
ms.openlocfilehash: 703e89342cbfd4a957c10419d6583e85ec6f6d2a
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837462"
---
# <a name="ltsecureconversationbootstrapgt"></a>&lt;secureConversationBootstrap&gt;
Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.  
  
 \<system.serviceModel>  
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
|`allowSerializedSigningTokenOnReply`|İsteğe bağlı. Seri hale getirilmiş bir belirteç üzerinde cevap kullanılıp kullanılmayacağını belirten bir Boole değeri. Varsayılan değer `false` şeklindedir. Bir çift bağlamayı kullanarak ayarı için varsayılan olarak `true` yapılan herhangi bir ayarı yok sayılacak.|  
|`authenticationMode`|Başlarıcı ve Yanıtlayıcı arasında kullanılan SOAP kimlik doğrulama modunu belirtir.<br /><br /> SspiNegotiated varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Güvenlik algoritması paketi Standartlaştırma, Digest, KeyWrap, imza, şifreleme algoritmaları ve KeyDerivation algoritmaları çeşitli tanımlar. Her güvenlik algoritması paketi farklı bu parametrelerin değerleri tanımlar. İleti tabanlı güvenlik, bu algoritmalar kullanılarak elde edilir.<br /><br /> Bu öznitelik, bir dizi varsayılandan farklı algoritmalar için kabul eder, farklı bir platform ile çalışırken kullanılır. Bu ayarda yapılan değişiklikler yaparken, güçlü ve zayıf ilgili algoritmaları farkında olmalıdır. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Varsayılan, `Basic256` değeridir.|  
|`includeTimestamp`|Her iletiye zaman damgalarının dahil edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`keyEntropyMode`|Güvenliğini sağlanmış iletiler için anahtarların hesaplanma yolunu belirtir. Anahtarları istemci anahtar malzemesi üzerinde yalnızca, yalnızca hizmet anahtar malzemesi veya her ikisinin bir birleşiminde temel alabilir. Geçerli değerler şunlardır:<br /><br /> -ClientEntropy: Oturum anahtarı anahtar malzemesi sağlanan istemci temel alır.<br />-ServerEntropy: Oturum anahtarı anahtar malzemesi sağlanan hizmetini devre dışı temel alır.<br />-CombinedEntropy: Oturum anahtarı devre dışı istemci alır ve anahtar malzemesini sağlanmaktadır.<br /><br /> CombinedEntropy varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Sıranın içinde hangi ileti düzeyi güvenlik algoritmasının uygulanacağı ayarlar. Geçerli değerler şunlardır:<br /><br /> -SignBeforeEncrypt: Oturum ilk olarak şifreleyin.<br />-SignBeforeEncryptAndEncryptSignature: Oturum, şifreleme ve imza şifreleme.<br />-EncryptBeforeSign: ilk şifrelemek ve oturum açın.<br /><br /> Karşılıklı sertifikalar ile WS-güvenlik 1.1 kullanırken, SignBeforeEncryptAndEncryptSignature varsayılan değer olan.  SignBeforeEncrypt WS-güvenlik 1.0 ile varsayılan değerdir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Kullanılan WS-güvenlik sürümünü ayarlar. Geçerli değerler şunlardır:<br /><br /> -WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> WSSecurityXXX2005 varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Anahtarları kanıt anahtarlarından türetilip türetilemeyeceğini belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`requireSecurityContextCancellation`|Güvenlik bağlamı verilecek iptal edildi ve artık gerekli olmadığında sonlandırıldı olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`requireSignatureConfirmation`|WS-güvenlik imza doğrulamasının etkin olup olmadığını belirten bir Boole değeri. Ayarlandığında `true`, ileti imzaları Yanıtlayıcı tarafından onaylanır. Varsayılan, `false` değeridir.<br /><br /> İmza onayı isteği tam tanıma hizmet yanıt verdiğini doğrulamak için kullanılır.|  
|`securityHeaderLayout`|Güvenlik üst bilgisindeki öğelerin sıralamasını belirtir. Geçerli değerler şunlardır:<br /><br /> -Katı. Öğeleri güvenlik başlığına göre "kullanılmadan önce bildirme" Genel İlkesi eklenir.<br />-Belirsiz. WSS için onaylar herhangi bir sırada güvenlik üst öğeleri eklendi: SOAP ileti güvenliği.<br />-LaxWithTimestampFirst. WSS için onaylar herhangi bir sırada güvenlik üst öğeleri eklendi: SOAP ileti güvenliği dışında güvenlik üst bilgisi içindeki ilk öğeyi wsse:Timestamp öğesi olmalıdır.<br />-LaxWithTimestampLast. WSS için onaylar herhangi bir sırada güvenlik üst öğeleri eklendi: SOAP ileti güvenliği dışında güvenlik üst bilgisi içindeki son öğeden bir wsse:Timestamp öğesi olmalıdır.<br /><br /> Katı varsayılandır.<br /><br /> Bu öğe türünde <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İssuermetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Geçerli bir verilen belirtecin belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Bu bağlama için yerel bir istemci güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Bu bağlama için yerel bir hizmetin güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
