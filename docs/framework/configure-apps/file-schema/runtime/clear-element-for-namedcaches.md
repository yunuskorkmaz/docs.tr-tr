---
description: 'İçin: öğesi hakkında daha fazla bilgi <clear><namedCaches>'
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: 9d883c102fc76875ce155f353920f730bf9700c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719103"
---
# <a name="clear-element-for-namedcaches"></a>\<namedCaches> için \<clear> Öğesi

`namedCache` `namedCaches` Bir bellek önbelleği için koleksiyondaki tüm girişleri temizler.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a>Syntax  
  
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

- [\<namedCaches> Öğesi (önbellek ayarları)](namedcaches-element-cache-settings.md)
