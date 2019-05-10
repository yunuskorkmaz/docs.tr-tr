---
title: < Crst_DisableSpinWait > öğesi
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89f0558c11e229fef2ca3cd619e3c033f12c858
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754667"
---
# <a name="crstdisablespinwait-element"></a>\<Crst_DisableSpinWait > öğesi

Döndürme-waıtıng contended olduğunda önemli bir bölümü için devre dışı bırakılıp bırakılmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<Crst_DisableSpinWait >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**Etkin**|Döndürme-contended kritik bölümlere bekleniyor devre dışı bırakılıp bırakılmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|1.|Kritik bir bölüm alınamıyor, döndürme bekleyen devre dışı bırakın.|  
|0|Kritik bir bölüm alınamıyor, döndürme bekleyen devre dışı bırakmayın. Varsayılan değer budur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çeşitli çalışma zamanı yapılandırma ayarları hakkında bilgi içerir.|  
  
## <a name="example"></a>Örnek  

Döndürme bekleme contended olduğunda önemli bölümleri aşağıdaki örnek devre dışı bırakır.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
