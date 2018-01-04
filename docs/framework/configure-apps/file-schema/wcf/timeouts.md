---
title: "&lt;zaman aşımları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04003584cf12355116d32cccffdcb2b9990b1b85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttimeoutsgt"></a>&lt;zaman aşımları&gt;
Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi temsil eder.  
  
 \<Sistem. ServiceModel >  
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
