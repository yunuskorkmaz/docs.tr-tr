---
title: '&lt;RSA&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dbeb08e6475d4825ad442b0b264e9003bb6fc53d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltrsagt"></a>&lt;RSA&gt;
Bu kimliğe sahip bir uç nokta bağlandığı güvenli bir WCF istemcisi, sunucu tarafından sunulan talepler bu kimliği oluşturmak için kullanılan RSA ortak anahtarı içeren bir talep içeren doğrular.  
  
 \<Kimliği >  
\<RSA >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|value|İsteğe bağlı dize. İstemcide ile Karşılaştırılacak RSA ortak anahtar değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 RSA onay, özellikle kendi RSA anahtarı temel tek bir sertifika kimlik doğrulaması sınırlamanıza olanak sağlar veya kendi RSA anahtar değeri oluşturulabilir. RSA anahtar değeri değiştirilirse bu etkinleştirir daha sıkı kimlik doğrulaması hizmeti ödün verme pahasına belirli bir RSA anahtarı artık mevcut istemciler ile çalışıyor.  
  
 Bir istemci için bir hizmet doğrulamak için kimlik kullanma hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma kodunu bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikası ortak anahtar değerini belirtir.  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
