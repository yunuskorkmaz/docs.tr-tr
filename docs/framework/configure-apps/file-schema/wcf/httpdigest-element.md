---
title: '&lt;httpDigest&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 4f3edb4a525429bfc55c4e4cfaffbfc5726dcef8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43477964"
---
# <a name="lthttpdigestgt-element"></a>&lt;httpDigest&gt; Öğesi
Bir Özet belirtir bir hizmeti istemcisi kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini yazın.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors >  
\<davranışı >  
\<clientCredentials >  
\<httpDigest >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`impersonationLevel`|Sunucuya istemcinin iletişim kurduğu kimliğe bürünme tercihini ayarlar. İstemcinin kimliğe bürünme modu, sunucuda zorlanmaz. Geçerli değerler şunlardır:<br /><br /> -Kimlik: Sunucu kimliğini ve istemci ayrıcalıkları elde edebilirsiniz, ancak istemci kimliğine bürünülemedi.<br />-Kimliğe bürünme: Sunucu istemcinin güvenlik bağlamı yerel sistemde kimliğine bürünebilir.<br />-Temsilci: Sunucu uzak sistemlerdeki güvenlik bağlamı istemcinin kimliğine bürünebilir.<br />-Anonim: Sunucusu özelliklerini veya istemci kimliği.<br />-Yok: Bir kimliğe bürünme düzeyi atanmadı.<br /><br /> Varsayılan kimliğidir. Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir Özet bir algoritma ve girişleri kümesi kullanılarak tanımlandığı karmasıdır. Authenticator'ı ve kimliği doğrulanmış bir algoritma kabul edin ve girdi olarak kullanılan veri değişimi. İstemci, karmayı hesaplar ve hizmetine gönderir. Hizmet ayrıca karmayı hesaplar ve değerlerini karşılaştırır. Bir eşleşme istemci doğrular.  
  
 Bu özellik, Windows ve Internet Information Services (IIS) üzerinde Active Directory ile etkinleştirilmelidir. Daha fazla bilgi için [Özet kimlik doğrulaması IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)  
 [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
