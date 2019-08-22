---
title: <namedCaches> için <remove> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: e9b126cee83bc8109606d915ea48549beea970c9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663470"
---
# <a name="remove-element-for-namedcaches"></a>\<namedönbellekler için \<> öğesini kaldırın >
Bir bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.  
  
 \<System. Runtime. Caching >  
\<memoryCache >  
\<Namedönbellekler >  
\<> Kaldır  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Tür  
 `None`  
  
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
 Öğesi `remove` , bir bellek `namedCache` önbelleğinin adlandırılmış önbellek koleksiyonundan bir girişi kaldırır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Namedönbellekler > öğesi (önbellek ayarları)](namedcaches-element-cache-settings.md)
