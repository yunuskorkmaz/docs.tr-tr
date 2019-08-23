---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b159488efa2a80a9dea625e4c6dfe2f215dfc457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939180"
---
# <a name="timeouts"></a>\<Zaman aşımları >
Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç nokta >  
\<Ana bilgisayar >  
\<Zaman aşımları >  
  
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
|`closeTimeout`|Hizmet <xref:System.TimeSpan> ana bilgisayarının kapanması için izin verilen zaman aralığını belirten bir değer.|  
|`openTimeout`|Hizmet <xref:System.TimeSpan> ana bilgisayarının açması için izin verilen zaman aralığını belirten bir değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ana bilgisayar >](host.md)|Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Barındırma](../../../wcf/feature-details/hosting.md)
