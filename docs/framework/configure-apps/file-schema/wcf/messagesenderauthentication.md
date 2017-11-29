---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 428dbdc65a4f66e5632e4ded7d7ded0d10b7c9d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagesenderauthenticationgt"></a>&lt;messageSenderAuthentication&gt;
Eş sertifikanın bir ileti gönderen tarafından kullanılan kimlik doğrulama ayarlarını belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<Eş >  
\<messageSenderAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<messageSenderAuthentication  
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
|`certificateValidationMode`|İsteğe bağlı numaralandırması. Kimlik bilgilerini doğrulamak için kullanılan beş modlarından birini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır.|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Bir türü ve bir özel tür doğrulamak için kullanılan derleme belirtir. Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`. Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]Varsayılan eş eş sertifikayı güvenilir kişiler deposunda karşı doğrular sertifika Doğrulayıcı sağlar. Sertifika geçerli bir kök zincir olduğunu doğrular. Farklı bir davranışı belirtmek ve bu öznitelik için özel Doğrulayıcı işaret edecek şekilde kullanmak için özel bir doğrulayıcı uygulayabilirsiniz.|  
|`revocationMode`|İsteğe bağlı numaralandırması. Sertifika iptal modunu belirtir. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Sistem eş sertifika tarafından iptal edildi olduğunu doğrular iptal edilen sertifika listesinde bakan. Bu onay çevrimiçi denetleyerek ya da bir önbelleğe alınan iptal listesi karşı gerçekleştirilebilir. İptal denetimi NoCheck için bu öznitelik ayarlayarak kapatılabilir.|  
|`trustedStoreLocation`|İsteğe bağlı numaralandırması. Burada eş sertifika doğrulanmış tarafından güvenilen depolama konumu belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] güvenlik sistemi. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Eş düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, ileti kimlik doğrulaması seçilirse yapılandırılmış olması gerekir. Çıktı kanallar için her ileti tarafından sağlanan sertifika kullanılarak imzalanmıştır [ \<sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Tüm iletiler, uygulamaya teslim önce tarafından belirtilen Doğrulayıcı kullanarak ileti kimlik bilgileri karşı denetlenir `customCertificateValidatorType` bu öğesinin özniteliği. Doğrulayıcı kabul edin veya kimlik bilgisi reddedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [Sertifikalar ile çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Eş kanal ileti kimlik doğrulaması](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Eş kanal özel kimlik doğrulama](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
