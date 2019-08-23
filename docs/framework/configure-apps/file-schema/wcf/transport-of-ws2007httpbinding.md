---
title: <transport> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911981"
---
# <a name="transport-of-ws2007httpbinding"></a>\<\<WS2007HttpBinding > taşıma >
HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.  
  
 \<system.serviceModel>  
\<bağlama >  
\<ws2007HttpBinding>  
\<bağlama >  
\<Güvenlik >  
\<Taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`clientCredentialType`|Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir. Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir. Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesi. Varsayılan değer boş bir dizedir.<br /><br /> Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir. Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir. Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirleyebilmek için kimlik doğrulama bölgesini sorgulayabilir.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenlik devre dışı bırakıldı.|  
|Temel|Temel kimlik doğrulamasını kullanır.|  
|Bilgisi|Özet kimlik doğrulaması kullanır.|  
|NT|Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.|  
|Windows|Tümleşik Windows kimlik doğrulamasını kullanır.|  
|Sertifika|İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenlik devre dışı bırakıldı.|  
|Temel|Temel kimlik doğrulamasını kullanır.|  
|Bilgisi|Özet kimlik doğrulaması kullanır.|  
|NT|Windows etki alanı ile geri dönüş olarak NTLM kullanır.|  
|Windows|Tümleşik Windows kimlik doğrulamasını kullanır.|  
|Sertifika|İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-ws2007httpbinding.md)|WS2007HttpBinding > öğesinin güvenlik yeteneklerini [ \<](ws2007httpbinding.md) temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
