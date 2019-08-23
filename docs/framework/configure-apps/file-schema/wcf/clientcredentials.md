---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: c3e756f49b7054d6553eb6c3f1850f0fbce14943
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926125"
---
# <a name="clientcredentials"></a>\<clientCredentials >
Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<Endpointdavranışlar >  
\<davranış >  
\<clientCredentials >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`supportInteractive`|Etkileşimli bir kullanıcının çalışma zamanında istemci kimlik bilgilerini seçmeye dahil edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan değer `true` şeklindedir.|  
|`type`|Bu yapılandırma öğesinin türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](clientcertificate-of-clientcredentials-element.md)|Hizmetin istemcinin kimliğini doğrulamak için kullanılan sertifikayı belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest >](httpdigest-element.md)|İstemci kimliğini hizmette doğrulamak için kullanılan bir Özet belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<IssuedToken >](issuedtoken.md)|İstemcinin kimliğini bir güvenli belirteç hizmeti 'ne (STS) doğrulamak için kullanılan özel bir belirteç türünü belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<eş >](peer-of-clientcredentials-element.md)|Geçerli bir eş kimlik bilgisi belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate >](servicecertificate-of-clientcredentials-element.md)|İstemciye hizmetin kimliğini doğrulamak için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar. Bu sertifika, hizmetten istemciye bant dışı verilmelidir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<Windows >](windows-of-clientcredentials-element.md)|Windows kimlik bilgilerini belirtir. Varsayılan değer, geçerli iş parçacığının kimlik bilgileridir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İstemci kimlik bilgileri, karşılıklı kimlik doğrulamanın gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır. Bu yapılandırma bölümü, istemcinin hizmet sertifikası ile iletileri güvenli hale getirmek zorunda olduğu senaryolara yönelik hizmet sertifikalarını belirtmek için de kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
