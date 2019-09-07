---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399634"
---
# <a name="servicecredentials"></a>\<serviceCredentials>
Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCredentials >**  
  
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
|`type`|Bu yapılandırma öğesinin türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](clientcertificate-of-servicecredentials.md)|İstemci sertifikası bant dışı kullanılabilir olduğunda kullanılacak sertifikayı belirtir. Bu öğe istemci sertifikası doğrulama ayarlarını da belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.|  
|[\<IssuedTokenAuthentication >](issuedtokenauthentication-of-servicecredentials.md)|Bu hizmet için geçerli verilen belirteci belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.|  
|[\<eş >](peer-of-servicecredentials.md)|Eş düğüm için geçerli kimlik bilgilerini belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<Securekonuşma kimlik doğrulaması >](secureconversationauthentication-of-servicecredential.md)|Güvenli konuşma için geçerli kimlik bilgilerini belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.|  
|[\<serviceCertificate >](servicecertificate-of-servicecredentials.md)|Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifikayı belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.|  
|[\<userNameAuthentication >](usernameauthentication.md)|Kullanıcı adı parola doğrulama ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserNameServiceElement>.|  
|[\<windowsAuthentication >](windowsauthentication-of-servicecredentials.md)|Windows kimlik bilgisi doğrulama ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsServiceElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
