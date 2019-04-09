---
title: <clear> öğe için <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: eb0a50919e163a795abc70d132bd45f1d05192ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146867"
---
# <a name="clear-element-for-namedcaches"></a>\<Temizle > öğesi için \<namedCaches >
Tüm temizler `namedCache` girişleri `namedCaches` koleksiyonu için bir önbellek.  
  
 \<System.Runtime.Caching >  
\<memoryCache>  
\<namedCaches>  
\<Ekle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 `None`  
  
### <a name="child-elements"></a>Alt Öğeler  
 `None`  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Yapılandırma ayarları için adlandırılmış bir koleksiyonunu içeren <xref:System.Runtime.Caching.MemoryCache> örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `clear` Öğesi tümünü temizler `namedCache` girişleri adlandırılmış önbelleği koleksiyondaki bir önbellek. Kullanabileceğiniz `clear` kullanmadan önce öğesi `add` vardır başka hiçbir emin olmak için yeni bir adlandırılmış önbellek girdisi eklemek için öğesi adlı önbellekler koleksiyondaki.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<namedCaches > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
