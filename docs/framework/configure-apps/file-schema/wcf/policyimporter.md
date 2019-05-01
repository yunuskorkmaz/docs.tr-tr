---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 81f38d2a163163ca7255ca546bbddbbb58fa3a1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783194"
---
# <a name="policyimporter"></a>\<policyImporter >
Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen bir ilke içeri Aktarıcı belirtir.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<meta veri >  
\<policyImporters >  
\<policyImporter >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`type`|Bu öğenin türü.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<policyImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen tüm ilke ımporters belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İlke içeri Aktarıcı yanı sıra arama özellikleri bağlama hakkında özel ilke onaylamalarını onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [WCF İstemci Yapılandırması](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [İstemciler](../../../../../docs/framework/wcf/feature-details/clients.md)
