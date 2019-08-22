---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658856"
---
# <a name="clear-element-for-namedcaches"></a>\<namedönbellekler için \<> öğesini Temizle >
Bir bellek `namedCache` önbelleği için `namedCaches` koleksiyondaki tüm girişleri temizler.  
  
 \<System. Runtime. Caching >  
\<memoryCache >  
\<Namedönbellekler >  
\<> Ekle  
  
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
|[\<Namedönbellekler >](namedcaches-element-cache-settings.md)|Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesi `clear` , bir bellek `namedCache` önbelleği için adlandırılmış önbellek koleksiyonundaki tüm girişleri temizler. Koleksiyonda başka bir adlandırılmış `clear` önbellek bulunmadığından emin olmak için `add` , öğesini kullanarak yeni bir adlandırılmış önbellek girişi ekleyebilmeniz için öğesini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Namedönbellekler > öğesi (önbellek ayarları)](namedcaches-element-cache-settings.md)
