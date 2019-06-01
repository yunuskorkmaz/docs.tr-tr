---
title: <legacyCorruptedStateExceptionsPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8733e11aba30ebea30fc71a5350f76dfd041eb4
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456405"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy > öğesi
Ortak dil çalışma zamanı erişim ihlalleri ve diğer bozuk durum özel durumları yakalamak yönetilen kod izin verip vermediğini belirtir.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Uygulama yakalar belirtir erişim ihlalleri gibi özel durum hataları durumu bozan.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Uygulama değil yakalar erişim ihlalleri gibi özel durum hataları durumu bozan. Bu varsayılandır.|  
|`true`|Uygulama yakalar erişim ihlalleri gibi özel durum hataları durumu bozan.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 3.5 ve önceki sürümlerinde, ortak dil çalışma zamanı tarafından bozuk işlem durumları ortaya çıktı özel durumları yakalamak yönetilen kod izin. Erişim ihlali, bu özel durumun türünü örneğidir.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], yönetilen kod artık bu tür özel durumları yakalayan `catch` engeller. Ancak, bu değişikliği geçersiz kılar ve iki yolla bozuk durum özel durumların işlenmesiyle Koru:  
  
- Ayarlama `<legacyCorruptedStateExceptionsPolicy>` öğenin `enabled` özniteliğini `true`. Bu yapılandırma ayarının uygulanan processwide olduğu ve tüm yöntemleri etkiler.  
  
 -veya-  
  
- Uygulama <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> özniteliğini özel durumları içeren yöntemine `catch` blok.  
  
 Bu yapılandırma öğesi, yalnızca .NET Framework 4'teki kullanılabilir ve üzerinde desteklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, uygulama .NET Framework 4 önceki davranış geri dönmek ve tüm bozulan durumu özel durum hatalarını yakalar, belirtmek gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
