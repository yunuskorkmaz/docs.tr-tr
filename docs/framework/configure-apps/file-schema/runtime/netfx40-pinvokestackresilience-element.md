---
title: '&lt;Netfx40_pınvokestackresilience&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49dc991fd1f30bce6c328725a794750c753145cd
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613290"
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a>&lt;Netfx40_pınvokestackresilience&gt; öğesi
Olup çalışma zamanı düzeltmeleri yanlış platform çağırma bildirimler arasında yavaş geçişler, çalışma zamanında otomatik olarak yönetilen ve yönetilmeyen kod belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
< Netfx40_pınvokestackresilience >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı yanlış platform algılayıp algılamadığını belirtir bildirimleri çağırabilir ve yığın çalışma zamanında 32-bit platformlarda otomatik olarak düzeltir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`0`|Çalışma zamanı sürümünde mimarisi hazırlama daha hızlı bir şekilde birlikte çalışma kullanır [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], hangi algılamazsa ve düzeltme yanlış platform çağırma bildirimleri. Bu varsayılandır.|  
|`1`|Algılayan ve yanlış platform düzeltme çalışma zamanı kullanan daha yavaş geçişleri bildirimleri çağırın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, yanlış platform karşı çalıştırma esnekliği çağırmak için bildirimleri daha hızlı bir şekilde birlikte çalışma hazırlama ticari olanak tanır.  
  
 İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], yönetilen koddan yönetilmeyen koda geçişleri için önemli bir performans geliştirmesi mimarisi hazırlama kolaylaştırılmış bir birlikte çalışabilirlik sağlar. .NET Framework'ün önceki sürümlerinde, sıralama algılanan katman yanlış platform, 32-bit platformlarda bildirimleri çağırın ve yığın otomatik olarak düzeltildi. Yeni sıralama mimarisi, bu adım ortadan kaldırır. Sonuç olarak, geçiş çok hızlı, ancak yanlış bir platform çağırma bildirimi bir program hatalarına neden olabilir.  
  
 Geliştirme sırasında yanlış bildirimleri algılamak kolaylaştırmak için Visual Studio hata ayıklama deneyimi geliştirildi. [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) yönetilen hata ayıklama Yardımcısı (MDA), yanlış platform çağırma bildirimleri uygulamanızı hata ayıklayıcısı ekli çalıştırırken bildirir.  
  
 Burada, uygulamanızın kullandığı derlemeniz olamaz ve kullanabileceğiniz sahip yanlış platform çağırma, bildirimleri, bileşenlerin bir senaryoya `NetFx40_PInvokeStackResilience` öğesi. Bu öğe, uygulama yapılandırma dosyası ekleme `enabled="1"` daha yavaş geçişleri, .NET Framework'ün önceki sürümlerinde davranışını ile bir uyumluluk moduna kabul eder. .NET Framework'ün önceki sürümlerinde karşı derlenen derlemeler bu uyumluluk moduna otomatik olarak tutulur ve bu öğe gerekmez.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği yanlış karşı artan dayanıklılık katılmayı için platform çağırma nasıl arasında yavaş geçişler, bir uygulama için bildirimleri yönetilen ve yönetilmeyen kod.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
