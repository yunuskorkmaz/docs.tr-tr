---
title: "&lt;synchronousReceive&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a>&lt;synchronousReceive&gt; öğesi
Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında iletileri almak için çalışma zamanı davranışını belirtmek için kullanılır. Herhangi bir öznitelik veya alt öğe yok.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<synchronousReceive >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu davranış varsayılan olarak zaman uyumsuz yerine bir zaman uyumlu alma kullanım kanal dinleyicisi istemek için kullanın. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]Yeni bir iş parçacığı için kabul edilen bir kanalı pompa verir. Çok sayıda kanalları varsa, çalışan iş parçacığı dışında olasılığını yoktur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
