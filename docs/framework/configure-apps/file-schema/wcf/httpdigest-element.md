---
title: <httpDigest> Öğesi
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: f392ebf4eeb6a008952fd4d5ef4e301e57f6eb31
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397986"
---
# <a name="httpdigest-element"></a>\<httpDigest > öğesi
İstemcinin bir hizmette kimlik doğrulaması yapılırken kullanılan Özet türü kimlik bilgilerini belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`impersonationLevel`|İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar. İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz. Geçerli değerler şunlardır:<br /><br /> İsi Sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.<br />Ation Sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.<br />Verilmesini Sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.<br />Deðeri Sunucu, istemciyi taklit edemez veya tanımlamıyor.<br />Seçim Kimliğe bürünme düzeyi atanmadı.<br /><br /> Varsayılan değer kimliğidir. Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](clientcredentials.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özet, bir algoritma ve bir giriş kümesi kullanılarak belirlenen bir karmadır. Kimlik doğrulayıcı ve kimlik doğrulaması, bir algoritmaya karşı kabul ediyorum ve girdi olarak kullanılan verileri değiş tokuş ediyor. İstemci karmayı hesaplayabilir ve hizmete gönderebilir. Hizmet ayrıca karmayı hesaplar ve değerleri karşılaştırır. Bir eşleşme istemciyi doğrular.  
  
 Bu özelliğin Windows ve Internet Information Services (IIS) üzerinde Active Directory etkinleştirilmesi gerekir. Daha fazla bilgi için bkz. [ııs 6,0 'de Özet kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
