---
title: '&lt;etwEnable&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 267a4a29282881d18201d0cb2062e91b4ff974a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltetwenablegt-element"></a>&lt;etwEnable&gt; öğesi
Olay izleme için ortak dil çalışma zamanı olayları Windows (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<etwEnabled >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> ETW etkin olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|ETW etkinleştirin. Windows Vista ve Windows Server 2008 işletim sistemleri ile başlayan Windows sürümleri için varsayılan değer budur.|  
|false|ETW devre dışı bırakın. Önceki Windows sürümleri için varsayılan değer budur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows Vista ile başlayarak, ETW varsayılan olarak etkindir. ETW bir uygulama için devre dışı bırakmak için bu öğeyi kullanın. Önceki Windows sürümlerinde bu öğe için bir uygulama ETW etkinleştirmek için kullanın.  
  
> [!NOTE]
>  ETW etkin veya genel bir sunucuda, bir kayıt defteri ayarını kullanarak devre dışı. Bkz: [.NET Framework günlük kaydını denetleme](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama ETW izlemeyi etkinleştirmek gösterilmiştir.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [.NET Framework Günlük Kaydını Denetleme](../../../../../docs/framework/performance/controlling-logging.md)
