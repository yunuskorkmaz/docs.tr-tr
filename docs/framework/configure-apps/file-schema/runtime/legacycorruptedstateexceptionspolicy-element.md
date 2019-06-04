---
title: <legacyCorruptedStateExceptionsPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6191ee2169a85725f0367763874e60c0ceb1d7a4
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489436"
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
  
 .NET Framework 4 ile başlayarak, yönetilen kod artık bu tür özel durumları yakalayan `catch` engeller. Ancak, bu değişikliği geçersiz kılar ve iki yolla bozuk durum özel durumların işlenmesiyle Koru:  
  
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
