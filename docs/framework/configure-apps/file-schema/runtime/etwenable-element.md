---
title: '&lt;etwEnable&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6ea2f8a32a18dfce6be54ce52ce8fef4abf92ce
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610781"
---
# <a name="ltetwenablegt-element"></a>&lt;etwEnable&gt; öğesi
Olay İzleme (ETW) Windows için ortak dil çalışma zamanı olayları için etkinleştirilip etkinleştirilmeyeceğini belirtir.  
  
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
|Etkin|Gerekli öznitelik.<br /><br /> ETW etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|ETW etkinleştirin. Bu Windows Vista ve Windows Server 2008 işletim sistemlerinin başlayarak Windows sürümleri için varsayılandır.|  
|false|ETW devre dışı bırakın. Önceki Windows sürümleri için varsayılan değer budur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 ETW, Windows Vista ile başlayarak, varsayılan olarak etkindir. ETW bir uygulama için devre dışı bırakmak için bu öğeyi kullanırsınız. Önceki Windows sürümlerinde, bir uygulama için ETW etkinleştirmek için bu öğeyi kullanırsınız.  
  
> [!NOTE]
>  ETW, etkin veya genel olarak bir sunucuda, kayıt defteri ayarını kullanarak devre dışı. Bkz: [.NET Framework günlük kaydını denetleme](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama için ETW izlemenin nasıl etkinleştirileceği gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [.NET Framework Günlük Kaydını Denetleme](../../../../../docs/framework/performance/controlling-logging.md)
