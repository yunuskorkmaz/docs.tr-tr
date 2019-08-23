---
title: <issuerMetadata> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: d9d7d41277eff1de43f717816b35fdc10d52192e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928872"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a>\<IssuedTokenParameters > \<IssuerMetadata >
\<system.serviceModel>  
\<bağlama >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
\<IssuedTokenParameters >  
\<IssuerMetadata >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Gerekli. Uç noktanın adresini belirten bir dize. Adres, mutlak bir URI olmalıdır. Varsayılan değer boş bir dizedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üst bilgiler >](headers-element.md)|Adres üst bilgileri koleksiyonu.|  
|[\<kimlik >](identity.md)|Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IssuedTokenParameters >](issuedtokenparameters.md)|Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Özel Bağlamalarla Güvenlik Özellikleri](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
