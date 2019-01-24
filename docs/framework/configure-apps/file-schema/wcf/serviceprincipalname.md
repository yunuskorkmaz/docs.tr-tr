---
title: '&lt;servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 5d65b5956491e30066ece54a48374f1d7014552e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657612"
---
# <a name="ltserviceprincipalnamegt"></a>&lt;servicePrincipalName&gt;
Bir hizmet tarafından hizmet asıl adı (SPN) kimliğini belirtir.  
  
 SPN hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<Kimliği >  
\<servicePrincipalName >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|value|Adı, bir istemci bir hizmet örneğini benzersiz şekilde tanımlar. Bir ormandaki bilgisayarlarda bir hizmet birden çok örneğini yükleyin, her örnek kendi SPN olması gerekir. İstemci kimlik doğrulaması için kullanıyor olabileceğiniz birden fazla adı varsa, verili hizmet örneğine birden çok SPN'ler olabilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken SPN kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
