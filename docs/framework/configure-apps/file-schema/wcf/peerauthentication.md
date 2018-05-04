---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: a8cc52fb2179bb5fc38635e4de0063a1dc1b1833
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltpeerauthenticationgt"></a>&lt;peerAuthentication&gt;
Eş düğüm tarafından kullanılan bir eş sertifika kimlik doğrulaması ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<Eş >  
\<peerAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`certificateValidationMode`|İsteğe bağlı numaralandırması. Kimlik bilgilerini doğrulamak için kullanılan üç modlarından birini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır.|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Bir türü ve bir özel tür doğrulamak için kullanılan derleme belirtir. Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`. Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Windows Communication Foundation (WCF) varsayılan eş eş sertifikayı güvenilir kişiler deposunda karşı doğrular sertifika Doğrulayıcı sağlar. Sertifika geçerli bir kök zincir olduğunu doğrular. Farklı bir davranışı belirtmek ve bu öznitelik için özel Doğrulayıcı işaret edecek şekilde kullanmak için özel bir doğrulayıcı uygulayabilirsiniz.|  
|`revocationMode`|İsteğe bağlı numaralandırması. Sertifika iptal modunu belirtir. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Sistem eş sertifika tarafından iptal edildi olduğunu doğrular iptal edilen sertifika listesinde bakan. Bu onay çevrimiçi denetleyerek ya da bir önbelleğe alınan iptal listesi karşı gerçekleştirilebilir. İptal denetimi NoCheck için bu öznitelik ayarlayarak kapatılabilir.|  
|`trustedStoreLocation`|İsteğe bağlı numaralandırması. Burada eş sertifika doğrulanmış tarafından güvenilen depolama konumu belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] güvenlik sistemi. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Eş düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<authentication>` Öğesi karşılık gelen <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı. Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir. Yeni bir eş komşu bağlantısı kurmaya çalıştığında, yanıt vermeyen eşler arası kendi kimlik bilgisi geçirir. Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır. Mesh bir eş bağlantı olduğunda, hem eş karşılıklı kimlik doğrulaması, iki ucunda anlamı doğrulayıcıları çağrılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Eşler Arası Ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Eş kanal ileti kimlik doğrulaması](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Eş kanal özel kimlik doğrulama](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
