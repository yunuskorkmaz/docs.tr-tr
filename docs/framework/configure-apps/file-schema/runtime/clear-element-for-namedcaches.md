---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252753"
---
# <a name="clear-element-for-namedcaches"></a>\<namedCaches> için \<clear> Öğesi
`namedCache` `namedCaches` Bir bellek önbelleği için koleksiyondaki tüm girişleri temizler.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
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
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .|  
  
## <a name="remarks"></a>Açıklamalar  
 `clear`Öğesi, `namedCache` bir bellek önbelleği için adlandırılmış önbellek koleksiyonundaki tüm girişleri temizler. `clear` `add` Koleksiyonda başka bir adlandırılmış önbellek bulunmadığından emin olmak için, öğesini kullanarak yeni bir adlandırılmış önbellek girişi ekleyebilmeniz için öğesini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<namedCaches>Öğesi (önbellek ayarları)](namedcaches-element-cache-settings.md)
