---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: 6a418fc546313b74bb965a0b223eca9c2e5acc08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115796"
---
# <a name="relativebindforresources-element"></a>\<Relativeforresources > öğesi
Uydu derlemeleri için araştırmayı iyileştirir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources >**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma zamanının uydu derlemeleri için araştırmayı iyileştirip iyileştirmediğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirmez. Varsayılan değer budur.|  
|`true`|Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, kaynakları [paketleme ve dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelendiği gibi, kaynakların araştırmalarını Kaynak Yöneticisi. Yani, bir kaynağın belirli bir yerelleştirilmiş sürümü için Kaynak Yöneticisi yokladığınızda, genel derleme önbelleğine bakabilir, uygulamanın kod tabanında kültüre özgü bir klasöre bakabilir, uydu Derlemeleriyle ilgili sorgu Windows Installer ve <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı. `<relativeBindForResources>` öğesi, uydu derlemeleri için Kaynak Yöneticisi araştırma şeklini iyileştirir. Aşağıdaki koşullarda kaynakları yokladığınızda performansı iyileştirebilir:  
  
- Uydu derlemesi, kod derlemesiyle aynı konumda dağıtıldığında. Diğer bir deyişle, kod derlemesi genel derleme önbelleğinde yüklüyse, uydu derlemelerinin de de yüklü olması gerekir. Kod derlemesi uygulamanın kod tabanında yüklüyse, uydu derlemelerinin de kod tabanında kültüre özgü bir klasöre yüklenmesi gerekir.  
  
- Windows Installer kullanılmazsa veya yalnızca, uydu derlemelerinin isteğe bağlı yüklemesi için nadiren kullanılırsa.  
  
- Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını işlemez.  
  
 `<relativeBindForResources>` öğesinin `enabled` özniteliğini `true` olarak ayarlamak, aşağıdaki gibi uydu derlemeleri için Kaynak Yöneticisi araştırmasını iyileştirir:  
  
- Uydu derlemesini yoklamanız için üst kod derlemesinin konumunu kullanır.  
  
- Uydu derlemeleri için Windows Installer sorgulamaz.  
  
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını yükseltmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kaynakları Paketleme ve Dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
