---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938961"
---
# <a name="synchronousreceive-element"></a>\<synchronousReceive > öğesi
Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti almaya yönelik çalışma zamanı davranışını belirtmek için kullanılır. Hiçbir özniteliğe veya alt öğeye sahip değil.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<Endpointdavranışlar >  
\<davranış >  
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
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kanal dinleyicisine varsayılan, zaman uyumsuz yerine zaman uyumlu alma kullanmasını söylemek için bu davranışı kullanın. Windows Communication Foundation (WCF), kabul edilen her kanal için yeni bir iş parçacığı yayınlar. Çok sayıda kanal varsa, iş parçacıklarının tükenme olasılığı vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
