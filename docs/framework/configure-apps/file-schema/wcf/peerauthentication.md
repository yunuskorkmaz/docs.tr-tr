---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: b627105dc4aae49557b0a6684569719622e13f08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180602"
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
- [Eş kanal ileti kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
