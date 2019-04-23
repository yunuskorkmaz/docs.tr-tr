---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b2cdd29cda7f82ce555b0f6c1a963567b41ff81b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213005"
---
# <a name="enablewebscript"></a>\<enableWebScript >
Bu öğe, ASP.NET AJAX web sayfalarından hizmet kullanmayı mümkün kılan uç nokta davranışını etkinleştirir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
\<enableWebScript >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<enableWebScript />
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
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Uç nokta davranışları kümesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu davranış yalnızca ya da birlikte kullanılmalıdır [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama veya [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) bağlama öğesi.  Bu davranışı hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [AJAX Tümleştirme ve JSON Desteği](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
