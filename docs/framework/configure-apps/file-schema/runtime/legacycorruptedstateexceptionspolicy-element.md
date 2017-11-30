---
title: "&lt;legacyCorruptedStateExceptionsPolicy&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4379f6f38c886504905483cefd7c7a6bbd519ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a>&lt;legacyCorruptedStateExceptionsPolicy&gt; öğesi
Ortak dil çalışma zamanı erişim ihlalleri ve diğer bozuk durumda özel durumları yakalamak yönetilen kod izin verip vermeyeceğini belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<legacyCorruptedStateExceptionsPolicy >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Uygulama yakalar belirtir durumu özel durum hataları erişim ihlali gibi bozulmasını.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Uygulama değil yakalar durumu özel durum hataları erişim ihlali gibi bozulmasını. Bu varsayılandır.|  
|`true`|Uygulama yakalar durumu özel durum hataları erişim ihlali gibi bozulmasını.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 3.5 ve önceki sürümlerde, ortak dil çalışma zamanı tarafından bozuk işlemi Devletleri ortaya çıktı durumları yakalamak yönetilen kod izin verilir. Erişim ihlali, bu özel durumun türünü örneğidir.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], yönetilen kod artık bu tür özel durumları yakalar `catch` engeller. Ancak, bu değişikliği geçersiz kılar ve iki yolla bozuk durumda özel durumları işleme Koru:  
  
-   Ayarlama `<legacyCorruptedStateExceptionsPolicy>` öğenin `enabled` özniteliğini `true`. Bu yapılandırma ayarının uygulanan processwide olduğundan ve tüm yöntemleri etkiler.  
  
 veya  
  
-   Uygulama <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> özniteliğini özel durumları içerir yöntemine `catch` bloğu.  
  
 Bu yapılandırma öğesi yalnızca kullanılabilir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, uygulamanın önceki davranışını için geri belirtmek gösterilmiştir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ve tüm bozulan durumu özel durum hataları yakalayın.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
