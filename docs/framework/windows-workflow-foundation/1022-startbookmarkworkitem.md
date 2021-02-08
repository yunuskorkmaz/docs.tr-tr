---
description: 'Hakkında daha fazla bilgi edinin: 1022-Startbookmarkworkıtem'
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 37d1ec1216df26a928b39189ca299dbb5b6c3d4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792836"
---
# <a name="1022---startbookmarkworkitem"></a>1022 - StartBookmarkWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1022|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir BookmarkWorkItem 'ın yürütülmeye başlandığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir BookmarkWorkItem 'ın yürütülmesi başlatılıyor.  BookmarkName: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|BookmarkName|xs: String|Yer işaretinin adı.|  
|BookmarkScope|xs: String|Yer işaretinin kapsamı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
