---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: d9f8fdf272962916cd08aede484e9bbde55b96a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670293"
---
# <a name="servicecredentials"></a>\<serviceCredentials>
Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
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
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|İstemci sertifikası yok-bant olduğunda kullanılacak sertifikayı belirtir. Bu öğe ayrıca istemci sertifika doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.|  
|[\<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Bu hizmet için geçerli verilen belirteç belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<Servicecredential >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|Geçerli bir güvenli konuşma kimlik bilgilerini belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|Kendisini tanımlamak için bir hizmet tarafından kullanılan sertifikayı belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.|  
|[\<userNameAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|Kullanıcı adı parola doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.UserNameServiceElement>.|  
|[\<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|Windows kimlik doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsServiceElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
