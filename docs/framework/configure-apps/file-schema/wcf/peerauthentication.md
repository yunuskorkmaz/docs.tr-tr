---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: ff050a1abe11b85dc85cd844892886fc168e53a4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257817"
---
# <a name="peerauthentication"></a>\<peerAuthentication >
Bir eş düğüm tarafından kullanılan bir eş sertifika kimlik doğrulaması ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<Eş >  
\<peerAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`certificateValidationMode`|İsteğe bağlı sabit listesi. Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Bir tür ve özel bir tür doğrulamak için kullanılan bir derleme belirtir. Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`. Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Windows Communication Foundation (WCF) varsayılan eş eş sertifikayı güvenilir Kişiler deposuna karşı doğrular sertifika Doğrulayıcı sağlar. Ayrıca, sertifika bir geçerli köke olduğunu doğrular. Farklı bir davranış belirtin ve bu öznitelik için özel Doğrulayıcı noktası özel Doğrulayıcı sağlayıcısı uygulayabilirsiniz.|  
|`revocationMode`|İsteğe bağlı sabit listesi. Sertifika iptal modunu belirtir. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Eş sertifika tarafından iptal edildi, sistem doğrular iptal edilen sertifika listesine aranıyor. Bu onay, çevrimiçi işaretleyerek ya da bir önbelleğe alınan iptal listesine karşı gerçekleştirilebilir. İptal denetimi bu öznitelik için NoCheck ayarlayarak kapatılabilir.|  
|`trustedStoreLocation`|İsteğe bağlı sabit listesi. WCF güvenlik sistemi tarafından eş sertifika nerede doğrulanır güvenilir depo konumunu belirtir. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<authentication>` Karşılık gelen öğe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı. Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir. Yeni bir eş komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgisi eşe geçirir. Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır. Ağ içinde bir eş bağlantı kurulsa hem eşleri karşılıklı kimlik doğrulaması, her iki ucunda anlamı doğrulayıcıları çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal ileti kimlik doğrulaması](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [Eş kanal özel kimlik doğrulama](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
