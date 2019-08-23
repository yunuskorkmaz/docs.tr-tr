---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c1d3662b2ceda83eb32abe99244e926332214698
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931317"
---
# <a name="messagesenderauthentication"></a>\<Iletienderauthentication >
İleti gönderici tarafından kullanılan eş sertifika için kimlik doğrulama ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<serviceCredentials>  
\<eş >  
\<Iletienderauthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`certificateValidationMode`|İsteğe bağlı sabit listesi. Kimlik bilgilerini doğrulamak için kullanılan beş moddan birini belirtir. Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir. Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır. Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar. Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular. Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.|  
|`revocationMode`|İsteğe bağlı sabit listesi. Sertifika iptal modunu belirtir. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular. Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir. İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.|  
|`trustedStoreLocation`|İsteğe bağlı sabit listesi. Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<eş >](peer-of-servicecredentials.md)|Eş düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir. Çıkış kanalları için her ileti, [ \<sertifika >](certificate-element.md)tarafından belirtilen sertifika kullanılarak imzalanır. Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin `customCertificateValidatorType` özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir. Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../wcf/feature-details/securing-peer-channel-applications.md)
