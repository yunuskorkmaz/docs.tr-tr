---
title: '&lt;Netfx40_pınvokestackresilience&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cfd8c971edd4537de6e073c49f128f86eb8a042
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749003"
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı yanlış platform algılayıp algılamadığını belirtir bildirimleri çağırma ve yığın çalışma zamanında 32-bit platformlarda otomatik olarak düzeltir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`0`|Çalışma zamanı sürümünde sunulan mimarisi hazırlama daha hızlı birlikte çalışabilirliği kullanır [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], hangi algılamazsa ve düzeltme yanlış platform çağırma bildirimleri. Bu varsayılandır.|  
|`1`|Algılayan ve yanlış platform düzeltme çalışma zamanı kullanır yavaş geçişleri bildirimleri çağırır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, çalışma zamanı esnekliği yanlış platform karşı çağırmak için bildirimleri daha hızlı birlikte çalışma hazırlama ticari olanak sağlar.  
  
 İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], yönetilen koddan yönetilmeyen koda geçişler için önemli performans iyileştirme mimarisi hazırlama kolaylaştırılmış bir birlikte çalışabilirlik sağlar. .NET Framework'ün önceki sürümlerinde, hazırlama algılanan katman yanlış platform 32-bit platformlarda bildirimleri çağırma ve otomatik olarak yığın sabit. Yeni hazırlama mimarisi, bu adım ortadan kaldırır. Sonuç olarak, geçişleri çok hızlı, ancak yanlış bir platform çağırma bildirimi program başarısız olmasına neden olabilir.  
  
 Geliştirme sırasında hatalı bildirimleri algılamak kolaylaştırmak için Visual Studio deneyimi hata ayıklama geliştirilmiştir. [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) yönetilen hata ayıklama Yardımcısı (MDA) bildirir, yanlış platform çağırma bildirimleri hata ayıklayıcısı ekli, uygulamanızı çalıştırırken.  
  
 Burada, uygulamanızın kullandığı derlenir olamaz ve kullanabileceğiniz sahip yanlış platform çağırma, bildirimler, bileşenleri adresi senaryoları için `NetFx40_PInvokeStackResilience` öğesi. Bu öğe ile uygulama yapılandırma dosyasına ekleyerek `enabled="1"` daha yavaş geçişleri, .NET Framework'ün önceki sürümlerinde davranışını ile uyumluluk moduna çevrilir. Karşı .NET Framework'ün önceki sürümlerinde derlenmiş derlemeler bu uyumluluk moduna otomatik olarak tutulur ve bu öğe gerekmez.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği yanlış karşı artan esneklik içine kabul etmek için platform çağırma nasıl bildirimler arasında yavaş geçişler, bir uygulama için yönetilen ve yönetilmeyen kod.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
