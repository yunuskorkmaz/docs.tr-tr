---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dd8e5ab11a7c019a8fe967f1c14b88a922a16c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934746"
---
# <a name="rsa"></a>\<RSA >
Bu kimlikle bir uç noktaya bağlanan güvenli bir WCF istemcisi, sunucu tarafından sunulan taleplerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarını içeren bir talep içerdiğini doğrular.  
  
 \<kimlik >  
\<RSA >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|value|İsteğe bağlı dize. İstemci üzerindeki ile Karşılaştırılacak RSA ortak anahtar değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kimlik >](identity.md)|İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir RSA denetimi, kimlik doğrulamasını RSA anahtarına göre veya kendi RSA anahtar değerini oluşturan tek bir sertifika ile kısıtlamanıza olanak sağlar. Bu, RSA anahtar değeri değiştirilirse hizmetin masrafına daha sıkı bir RSA anahtarının daha sıkı şekilde doğrulanmasını, ancak mevcut istemcilerle çalışmamayı mümkün değildir.  
  
 Bir istemciye hizmet doğrulamak üzere kimlik kullanma hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının ortak anahtar değerini belirtir.  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<kimlik >](identity.md)
