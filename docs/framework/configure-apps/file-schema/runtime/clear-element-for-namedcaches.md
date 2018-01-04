---
title: "&lt;Clear&gt; öğesi için &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 501371346b3c1496122d93a98eb89dd4afc6bcd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a>&lt;Clear&gt; öğesi için &lt;namedCaches&gt;
Tüm temizler `namedCache` girişleri `namedCaches` bir önbellek için koleksiyonu.  
  
 \<System.Runtime.Caching >  
\<memoryCache >  
\<namedCaches >  
\<ekleme >  
  
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
|[\<namedCaches >](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Yapılandırma ayarları adlandırılmış bir koleksiyonu içerir <xref:System.Runtime.Caching.MemoryCache> örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `clear` Öğesi temizler tüm `namedCache` adlandırılmış önbellek koleksiyonu için bir önbellek girdileri. Kullanabileceğiniz `clear` kullanmadan önce öğesi `add` vardır başka emin olmak için yeni bir adlandırılmış önbellek girdisi eklemek için öğe koleksiyonda önbellekleri adlı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<namedCaches > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
