---
title: '&lt;claimTypeRequirements&gt; öğesi &lt;temizleme&gt;'
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: c64e5450e01fdb011eb726f3bef1a85a5698d0d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568341"
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a>&lt;claimTypeRequirements&gt; öğesi &lt;temizleme&gt;
Birleştirilmiş kimlik bilgisindeki kaldırılacak talep türlerini belirtir. Bu koleksiyon boş başlar sağlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<wsFederatedBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Gerekli talep türlerinin koleksiyonunu belirtir. Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin. Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir. Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
