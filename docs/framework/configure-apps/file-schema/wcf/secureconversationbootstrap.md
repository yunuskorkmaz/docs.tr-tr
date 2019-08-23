---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: 2ee9a715929641abc605a31ac00fb154b863cc8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935844"
---
# <a name="secureconversationbootstrap"></a>\<Securebir Bootstrap >
Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
\<Securebir Bootstrap >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|`allowSerializedSigningTokenOnReply`|İsteğe bağlı. Seri hale getirilmiş bir belirtecin yanıt olarak kullanılabileceğini belirten bir Boole değeri. Varsayılan değer `false` şeklindedir. İkili bağlama kullanılırken, varsayılan ayar, yapılan ayar olarak `true` yoksayılır.|  
|`authenticationMode`|Başlatıcı ve Yanıtlayıcı arasında kullanılan SOAP kimlik doğrulama modunu belirtir.<br /><br /> Varsayılan değer sspiNegotiated ' dir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Güvenlik algoritması paketi, kurallı kullanım, Özet, KeyWrap, Imza, şifreleme ve anahtar türetme algoritmaları gibi çeşitli algoritmaların tanımlar. Güvenlik algoritması paketlerinin her biri, bu farklı parametrelerin değerlerini tanımlar. İleti tabanlı güvenlik Bu algoritmalar kullanılarak elde edilir.<br /><br /> Bu öznitelik, varsayılandan farklı bir algoritma kümesi için çalışan farklı bir platformda çalışırken kullanılır. Bu ayarda değişiklik yaparken ilgili algoritmaların güçlerinin ve zayıflığının farkında olmanız gerekir. Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Varsayılan, `Basic256` değeridir.|  
|`includeTimestamp`|Her iletiye zaman damgalarının dahil edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`keyEntropyMode`|Güvenli iletiler için anahtarların hesaplanma şeklini belirtir. Anahtarlar yalnızca hizmet anahtarı malzemeden veya her ikisinin bir birleşimi olan istemci anahtar malzemesini temel alabilir. Geçerli değerler şunlardır:<br /><br /> -Cliententrokopyala: Oturum anahtarı, istemci tarafından sunulan anahtar malzemesini temel alarak.<br />-Sunucusentropi: Oturum anahtarı, hizmet tarafından sunulan anahtar malzemeye dayanır.<br />- CombinedEntropy: Oturum anahtarı, istemci ve hizmet tarafından sunulan anahtarlama malzemesini temel alınarak belirlenir.<br /><br /> Varsayılan değer CombinedEntropy ' dir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|İletiye ileti düzeyi güvenlik algoritmalarının uygulanma sırasını ayarlar. Geçerli değerler şunlardır:<br /><br /> -SignBeforeEncrypt: Önce imzala, sonra şifreleyin.<br />-SignBeforeEncryptAndEncryptSignature: İmza imzalama, şifreleme ve şifreleme.<br />-EncryptBeforeSign: Önce şifreleyin, ardından imzalayın.<br /><br /> SignBeforeEncryptAndEncryptSignature, karşılıklı sertifikalar WS-Security 1,1 ile kullanılırken varsayılan değerdir.  SignBeforeEncrypt, WS-Security 1,0 ile varsayılan değerdir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Kullanılan WS-güvenlik sürümünü ayarlar. Geçerli değerler şunlardır:<br /><br /> - WSSecurityJan2004<br />- WSSecurityXXX2005<br /><br /> Varsayılan değer WSSecurityXXX2005 ' dir. Bu öznitelik türü <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Anahtarların orijinal kanıt anahtarlarından türetilip türetilemeyeceğini belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`requireSecurityContextCancellation`|Artık gerekli olmadığında güvenlik bağlamının iptal edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|`requireSignatureConfirmation`|WS-güvenlik imza doğrulamasının etkin olup olmadığını belirten bir Boolean değer. Olarak `true`ayarlandığında ileti imzaları Yanıtlayıcı tarafından onaylanır. Varsayılan, `false` değeridir.<br /><br /> İmza onayı, hizmetin bir isteğin tam olarak farkında olarak yanıt verdiğini doğrulamak için kullanılır.|  
|`securityHeaderLayout`|Güvenlik üst bilgisindeki öğelerin sıralamasını belirtir. Geçerli değerler şunlardır:<br /><br /> Sert. Öğeler güvenlik üstbilgisine "kullanılmadan önce bildir" genel ilkesine göre eklenir.<br />LAX. Öğeler, WSS 'yi doğrulayan herhangi bir sıraya göre güvenlik başlığına eklenir: SOAP Iletisi güvenliği.<br />-Laxwithtimestamp önce. Öğeler, WSS 'yi doğrulayan herhangi bir sıraya göre güvenlik başlığına eklenir: Güvenlik üstbilgisindeki ilk öğe bir WSO: Timestamp öğesi olması dışında SOAP Iletisi güvenliği.<br />-Laxwithtimestamp son. Öğeler, WSS 'yi doğrulayan herhangi bir sıraya göre güvenlik başlığına eklenir: Güvenlik üstbilgisindeki son öğenin bir WSO: Timestamp öğesi olması dışında SOAP Iletisi güvenliği.<br /><br /> Varsayılan değer katı ' dır.<br /><br /> Bu öğe türündedir <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IssuedTokenParameters >](issuedtokenparameters.md)|Geçerli bir verilen belirteç belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](localclientsettings-element.md)|Bu bağlama için yerel bir istemcinin güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](localservicesettings-element.md)|Bu bağlama için yerel bir hizmetin güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
