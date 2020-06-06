---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855056"
---
# \<policyImporter>
Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen bir ilke İçeri Aktarıcı belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
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
 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [WCF İstemci Yapılandırması](../../../wcf/feature-details/client-configuration.md)
- [İstemciler](../../../wcf/feature-details/clients.md)
