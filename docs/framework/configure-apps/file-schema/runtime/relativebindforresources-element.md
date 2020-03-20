---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153912"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> Öğesi
Sondayı uydu montajları için optimize eder.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma süresinin uydu derlemeleri için sondayı optimize edip etmediğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma süresi, sondayı uydu derlemeleri için optimize etmez. Varsayılan değer budur.|  
|`true`|Çalışma süresi uydu meclisleri için sonda optimize eder.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, Kaynak Yöneticisi, [Kaynakları Paketleme ve Dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelenen kaynaklar için sondalar. Bu, Kaynak Yöneticisi bir kaynağın belirli bir yerelleştirilmiş sürümünü incelediğinde, genel derleme önbelleğine bakabileceği, uygulamanın kod tabanında kültüre özgü bir klasöre <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> bakabileceği, uydu derlemeleri için Windows Yükleyici'yi sorgulayabileceği ve olayı yükseltebileceği anlamına gelir. Öğe, `<relativeBindForResources>` Kaynak Yöneticisi'nin uydu derlemeleri için araştırma şeklini optimize eder. Aşağıdaki koşullar altında kaynaklar için sondalama performansı artırabilir:  
  
- Uydu derlemesi kod derlemesi ile aynı konumda dağıtıldığında. Başka bir deyişle, kod derlemesi genel montaj önbelleğine yüklenmişse, uydu derlemeleri de burada yüklenmiş olmalıdır. Kod derlemesi uygulamanın kod tabanına yüklenmişse, uydu derlemelerinin kod tabanında kültüre özgü bir klasöre de yüklenmesi gerekir.  
  
- Windows Installer kullanılmadığında veya uydu derlemelerinin isteğe bağlı olarak yüklenmesi için nadiren kullanıldığında.  
  
- Uygulama kodu olayı işlemiyorsa. <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>  
  
 Kaynak Yöneticisi'nin `<relativeBindForResources>` uydu `true` derlemeleri için sondasını en iyi duruma getirmek için öğenin özniteliğini aşağıdaki gibi ayarlar: `enabled`  
  
- Uydu derlemesini araştırmak için ana kod derlemesinin konumunu kullanır.  
  
- Uydu derlemeleri için Windows Installer sorgusu yapmaz.  
  
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> Olayı yükseltmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kaynakları Paketleme ve Dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
