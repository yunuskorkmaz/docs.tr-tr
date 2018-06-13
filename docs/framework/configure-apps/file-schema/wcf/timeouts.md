---
title: '&lt;zaman aşımları&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 1f0638f85177d2acb6f61e3246a1a5ee9a4e2f5c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753007"
---
# <a name="lttimeoutsgt"></a>&lt;zaman aşımları&gt;
Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi temsil eder.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
\<ana bilgisayar >  
\<zaman aşımı >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> hizmet ana bilgisayarı kapatmak izin verilen zaman aralığını belirtir değer.|  
|`openTimeout`|A <xref:System.TimeSpan> açmak hizmet ana bilgisayarı için izin verilen zaman aralığını belirtir değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ana bilgisayar >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Hizmet ana bilgisayarı ayarlarını belirtir. bir yapılandırma öğesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
