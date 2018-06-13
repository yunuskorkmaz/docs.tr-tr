---
title: '&lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: a3d63e3d01c009834717a80a9ed9536fd1bdf838
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750407"
---
# <a name="ltservicecredentialsgt"></a>&lt;serviceCredentials&gt;
Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceCredentials type="String">  
   <clientCertificate>  
   </clientCertificate>  
   <issuedTokenAuthentication>  
   </issuedTokenAuthentication>  
   <peer>  
   </peer>  
   <secureConversationAuthentication>  
   </secureConversationAuthentication>  
   <serviceCertificate>  
   </serviceCertificate>  
   <userNameAuthentication>  
   </userNameAuthentication>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</serviceCredentials>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`type`|Bu yapılandırma öğesi türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|İstemci sertifikası kullanılabilir-bant olduğunda kullanılacak sertifikayı belirtir. Bu öğe ayrıca istemci sertifikasını doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.|  
|[\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Bu hizmet için geçerli verilen belirteç belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Eş düğüm için geçerli kimlik bilgilerini belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<Servicecredential >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|Güvenli bir konuşma için geçerli kimlik bilgilerini belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifika belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.|  
|[\<userNameAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|Kullanıcı adı parola doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.UserNameServiceElement>.|  
|[\<windowsAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|Windows kimlik doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsServiceElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
