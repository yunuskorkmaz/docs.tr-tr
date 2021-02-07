---
description: 'Daha fazla bilgi edinin: <relativeBindForResources> öğesi'
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: f08d8f8a8fc4bb14d28762254dca99788d44a858
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712928"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> Öğesi

Uydu derlemeleri için araştırmayı iyileştirir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a>Syntax  
  
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

 Genel olarak, kaynakları [paketleme ve dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelendiği gibi, kaynakların araştırmalarını Kaynak Yöneticisi. Yani, bir kaynağın belirli bir yerelleştirilmiş sürümü için Kaynak Yöneticisi araştırdığınızda, genel derleme önbelleğine bakabilir, uygulamanın kod tabanında kültüre özgü bir klasöre bakabilir, uydu Derlemeleriyle ilgili sorgu Windows Installer ve <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay oluşturabilir. `<relativeBindForResources>`Öğesi, uydu derlemeleri için Kaynak Yöneticisi araştırma biçimini iyileştirir. Aşağıdaki koşullarda kaynakları yokladığınızda performansı iyileştirebilir:  
  
- Uydu derlemesi, kod derlemesiyle aynı konumda dağıtıldığında. Diğer bir deyişle, kod derlemesi genel derleme önbelleğinde yüklüyse, uydu derlemelerinin de de yüklü olması gerekir. Kod derlemesi uygulamanın kod tabanında yüklüyse, uydu derlemelerinin de kod tabanında kültüre özgü bir klasöre yüklenmesi gerekir.  
  
- Windows Installer kullanılmazsa veya yalnızca, uydu derlemelerinin isteğe bağlı yüklemesi için nadiren kullanılırsa.  
  
- Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı işlemez.  
  
 Öğesinin, `enabled` `<relativeBindForResources>` `true` uydu derlemeleri için Kaynak Yöneticisi araştırmasını en iyi duruma getirmek için öğesi özniteliği aşağıdaki gibi ayarlanıyor:  
  
- Uydu derlemesini yoklamanız için üst kod derlemesinin konumunu kullanır.  
  
- Uydu derlemeleri için Windows Installer sorgulamaz.  
  
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>Olayı oluşturmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kaynakları Paketleme ve Dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
