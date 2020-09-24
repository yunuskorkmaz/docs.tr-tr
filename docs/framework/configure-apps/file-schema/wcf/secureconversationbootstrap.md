---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: 02072c55e299d9e3a5d53b61c891a9ee9837ada0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183721"
---
# \<secureConversationBootstrap>

Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationBootstrap>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
                             authenticationMode="AuthenticationMode"
                             defaultAlgorithmSuite="SecurityAlgorithmSuite"
                             includeTimestamp="Boolean"
                             requireDerivedKeys="Boolean"
                             keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
                             messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
                             messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
                             requireDerivedKeys="Boolean"
                             requireSecurityContextCancellation="Boolean"
                             requireSignatureConfirmation="Boolean"
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
|`allowSerializedSigningTokenOnReply`|İsteğe bağlı. Seri hale getirilmiş bir belirtecin yanıt olarak kullanılabileceğini belirten bir Boole değeri. Varsayılan değer: `false`. İkili bağlama kullanılırken, varsayılan ayar, yapılan ayar olarak `true` yoksayılır.|  
|`authenticationMode`|Başlatıcı ve Yanıtlayıcı arasında kullanılan SOAP kimlik doğrulama modunu belirtir.<br /><br /> Varsayılan değer sspiNegotiated ' dir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Configuration.AuthenticationMode> .|  
|`defaultAlgorithmSuite`|Güvenlik algoritması paketi, kurallı kullanım, Özet, KeyWrap, Imza, şifreleme ve anahtar türetme algoritmaları gibi çeşitli algoritmaların tanımlar. Güvenlik algoritması paketlerinin her biri, bu farklı parametrelerin değerlerini tanımlar. İleti tabanlı güvenlik Bu algoritmalar kullanılarak elde edilir.<br /><br /> Bu öznitelik, varsayılandan farklı bir algoritma kümesi için çalışan farklı bir platformda çalışırken kullanılır. Bu ayarda değişiklik yaparken ilgili algoritmaların güçlerinin ve zayıflığının farkında olmanız gerekir. Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> . Varsayılan değer: `Basic256`.|  
|`includeTimestamp`|Her iletiye zaman damgalarının dahil edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan değer: `true`.|  
|`keyEntropyMode`|Güvenli iletiler için anahtarların hesaplanma şeklini belirtir. Anahtarlar yalnızca hizmet anahtarı malzemeden veya her ikisinin bir birleşimi olan istemci anahtar malzemesini temel alabilir. Geçerli değerler:<br /><br /> -Cliententrokopyala: oturum anahtarı, istemci tarafından sunulan anahtar malzemesini temel alarak.<br />-Sunucusentropi: oturum anahtarı, hizmet tarafından sunulan anahtar malzemeye dayanır.<br />-CombinedEntropy: oturum anahtarı, istemci ve hizmet tarafından sunulan anahtarlama malzemesini temel alınarak belirlenir.<br /><br /> Varsayılan değer CombinedEntropy ' dir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .|  
|`messageProtectionOrder`|İletiye ileti düzeyi güvenlik algoritmalarının uygulanma sırasını ayarlar. Geçerli değerler şunlardır:<br /><br /> -SignBeforeEncrypt: önce Imzala, sonra şifreleyin.<br />-SignBeforeEncryptAndEncryptSignature: imza, şifreleme ve şifrelemeyi imzalama.<br />-EncryptBeforeSign: önce şifreleyin, ardından imzalayın.<br /><br /> SignBeforeEncryptAndEncryptSignature, karşılıklı sertifikalar WS-Security 1,1 ile kullanılırken varsayılan değerdir.  SignBeforeEncrypt, WS-Security 1,0 ile varsayılan değerdir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Security.MessageProtectionOrder> .|  
|`messageSecurityVersion`|Kullanılan WS-güvenlik sürümünü ayarlar. Geçerli değerler şunlardır:<br /><br /> - WSSecurityJan2004<br />- WSSecurityXXX2005<br /><br /> Varsayılan değer WSSecurityXXX2005 ' dir. Bu öznitelik türü <xref:System.ServiceModel.MessageSecurityVersion> .|  
|`requireDerivedKeys`|Anahtarların orijinal kanıt anahtarlarından türetilip türetilemeyeceğini belirten bir Boole değeri. Varsayılan değer: `true`.|  
|`requireSecurityContextCancellation`|Artık gerekli olmadığında güvenlik bağlamının iptal edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan değer: `true`.|  
|`requireSignatureConfirmation`|WS-güvenlik imza doğrulamasının etkin olup olmadığını belirten bir Boolean değer. Olarak ayarlandığında `true` ileti imzaları Yanıtlayıcı tarafından onaylanır. Varsayılan değer: `false`.<br /><br /> İmza onayı, hizmetin bir isteğin tam olarak farkında olarak yanıt verdiğini doğrulamak için kullanılır.|  
|`securityHeaderLayout`|Güvenlik üst bilgisindeki öğelerin sıralamasını belirtir. Geçerli değerler:<br /><br /> Sert. Öğeler güvenlik üstbilgisine "kullanılmadan önce bildir" genel ilkesine göre eklenir.<br />LAX. Öğeler, güvenlik başlığına, WSS: SOAP Ileti güvenliği olduğunu doğrulayan herhangi bir sırada eklenir.<br />-Laxwithtimestamp önce. Güvenlik üst bilgisindeki ilk öğe bir WSO: Timestamp öğesi olması dışında, güvenlik başlığına, WSS: SOAP Iletisi güvenliği olan herhangi bir sırada öğeler eklenir.<br />-Laxwithtimestamp son. Güvenlik üst bilgisindeki en son öğe bir WSO: Timestamp öğesi olması dışında, güvenlik başlığına, WSS: SOAP Iletisi güvenliği olan herhangi bir sırada öğeler eklenir.<br /><br /> Varsayılan değer katı ' dır.<br /><br /> Bu öğe türündedir <xref:System.ServiceModel.Channels.SecurityHeaderLayout> .|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Geçerli bir verilen belirteç belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement> .|  
|[\<localClientSettings>](localclientsettings-element.md)|Bu bağlama için yerel bir istemcinin güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement> .|  
|[\<localServiceSettings>](localservicesettings-element.md)|Bu bağlama için yerel bir hizmetin güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
