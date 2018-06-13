---
title: '&lt;relativeBindForResources&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ae5d1ca6403d84c9828dcf9550e9fbf40b28e1b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752305"
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativeBindForResources&gt; öğesi
Araştırması için uydu derlemelerini en iyi duruma getirir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<relativeBindForResources > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma zamanı için uydu derlemelerini araştırma iyileştirir olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı için uydu derlemelerini araştırma iyileştirmez. Varsayılan değer budur.|  
|`true`|Çalışma zamanı araştırma için uydu derlemelerini en iyi duruma getirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, Resource Manager açıklandığı gibi kaynaklar için yoklamaları [paketleme ve dağıtma kaynakları](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) konu. Bu belirli yerelleştirilmiş bir sürümün bir kaynağın için Resource Manager araştırmaları, onu genel derleme önbelleğinde arayın, kültüre özgü bir klasörde sorgusunda uygulamanın kodu temel, Windows Installer'ın için uydu derlemelerini bakın ve yükseltmek anlamına gelir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay. `<relativeBindForResources>` Öğesi Resource Manager için uydu derlemelerini yoklamaları şekilde iyileştirir. Aşağıdaki koşullarda kaynaklar için yoklama zaman, performansı geliştirebilir:  
  
-   Uydu bütünleştirilmiş kod derleme ile aynı konumda dağıtıldığında. Kod derleme genel derleme önbelleğinde yüklü değilse, diğer bir deyişle, uydu derlemelerini Ayrıca var. yüklenmesi gerekir. Kod derleme temel uygulamanın kodu yüklüyse, kod temeli kültüre özgü klasöründe uydu derlemelerini ayrıca yüklenmesi gerekir.  
  
-   Windows Installer zaman kullanılmaz veya nadiren kullanılan isteğe bağlı yüklemesinin uydu derlemelerini.  
  
-   Ne zaman uygulama kodu işlemiyor <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
 Ayarı `enabled` özniteliği `<relativeBindForResources>` öğesine `true` Resource Manager'ın araştırma için uydu derlemelerini gibi en iyi duruma getirir:  
  
-   Uydu derlemesi için araştırma için üst kod derleme konumunu kullanır.  
  
-   Windows Installer için uydu derlemelerini sorgulamaz.  
  
-   Değil Yükselt <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynakları Paketleme ve Dağıtma](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
