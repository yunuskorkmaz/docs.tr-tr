---
description: 'Hakkında daha fazla bilgi edinin: 1021-Schedulebookmarkworkıtem'
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: 5153d2e90a75bab90c76ee8786dc82d4ddac19a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792823"
---
# <a name="1021---schedulebookmarkworkitem"></a>1021 - ScheduleBookmarkWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1021|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir BookmarkWorkItem zamanlandığı olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir BookmarkWorkItem zamanlandı.  BookmarkName: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|BookmarkName|xs: String|Yer işaretinin adı.|  
|BookmarkScope|xs: String|Yer işaretinin kapsamı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
