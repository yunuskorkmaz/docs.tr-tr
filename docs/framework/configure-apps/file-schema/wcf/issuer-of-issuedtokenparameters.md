---
title: "&lt;issuedTokenParameters&gt; &lt;yayınlayan&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b31214f5552283c40cdc93e6e72a374bbfef9997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a>&lt;issuedTokenParameters&gt; &lt;yayınlayan&gt;
Güvenlik belirteci hizmeti (güvenlik belirteçleri veren STS) belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
\<İssuermetadata >  
\<veren >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Gerekli dize. STS URL'si.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Adres üstbilgileri Oluşturucu oluşturabilirsiniz uç noktaları koleksiyonu.|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Verilen bir belirteç kullanırken, sunucu kimlik doğrulaması istemci etkinleştirme ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İssuermetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Geçerli verilen belirteç belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Özel Bağlamalarla Güvenlik Özellikleri](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
