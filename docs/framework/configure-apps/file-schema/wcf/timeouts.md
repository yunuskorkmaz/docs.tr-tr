---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118072"
---
# <a name="timeouts"></a>\<zaman aşımı >
Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
\<konak >  
\<zaman aşımı >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> zaman aralığını belirten bir değer izin verilen hizmet konağı kapatın.|  
|`openTimeout`|A <xref:System.TimeSpan> zaman aralığını belirten bir değer açmak hizmet ana bilgisayarı için izin verilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<konak >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
