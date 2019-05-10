---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15156eaf883fc9ec162e0a85525564d49522b01d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592663"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources > öğesi
Araştırma için uydu derlemelerini en iyi duruma getirir.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma zamanı uydu derlemeler için araştırma iyileştirir olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı uydu derlemeler için araştırma iyileştirmez. Varsayılan değer budur.|  
|`true`|Çalışma zamanı araştırma uydu derlemeler için en iyi duruma getirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, Resource Manager açıklandığı gibi kaynaklar için araştırmaları [kaynakları paketleme ve dağıtma](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) konu. Bu belirli bir yerelleştirilmiş sürümünün bir kaynak için Resource Manager araştırmaları, genel derleme önbelleğinde arayın, uygulamanın kodu temel, sorgu Windows Installer kültüre özgü bir klasörde için uydu derlemeleri bakın ve yükseltmek, anlamına gelir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay. `<relativeBindForResources>` Öğesi Resource Manager için uydu derlemeleri araştırmaları şekilde iyileştirir. Aşağıdaki koşullarda kaynaklar için yoklama zaman, performansı geliştirebilir:  
  
- Ne zaman uydu derlemesini, kod derleme ile aynı konumda dağıtılır. Bir kod derlemesi genel derleme önbelleğinde yüklü ise diğer bir deyişle, uydu derlemeleri de vardır yüklenmesi gerekir. Kod bütünleştirilmiş kodu uygulamanın temel yüklü değilse, uydu derlemeleri de kod tabanının bir kültüre özgü klasöre yüklenmelidir.  
  
- Windows Installer ne zaman kullanılmaz veya nadiren kullanılan isteğe bağlı yükleme uydu derlemeleri için.  
  
- Ne zaman uygulama kodunun işlemez <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
 Ayarı `enabled` özniteliği `<relativeBindForResources>` öğesine `true` Resource Manager'ın araştırma için yardımcı derlemeler gibi en iyi duruma getirir:  
  
- Uydu derlemesi için araştırmaya üst kod derleme konumunu kullanır.  
  
- Uydu derlemeleri için Windows Installer sorgulamaz.  
  
- Bunu yükseltmez <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kaynakları Paketleme ve Dağıtma](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
