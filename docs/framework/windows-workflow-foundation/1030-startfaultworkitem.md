---
description: 'Hakkında daha fazla bilgi edinin: 1030-Startfaultworkıtem'
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 2d148277b2d593cfcf75e17662626f1f486e7c1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668103"
---
# <a name="1030---startfaultworkitem"></a>1030 - StartFaultWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1030|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir FaultWorkItem 'ın yürütmeyi başlatdığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem 'ın yürütülmesi başlatılıyor.  Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs: String|Hata etkinliğinin tür adı.|  
|FaultActivityDisplayName|xs: String|Hata etkinliğinin görünen adı.|  
|Faultactivityınstanceıd|xs: String|Hata etkinliğinin örnek kimliği.|  
|ExceptionActivity|xs: String|Özel durumu oluşturan etkinliğin tür adı.|  
|ExceptionActivityDisplayName|xs: String|Özel durumu oluşturan etkinliğin görünen adı.|  
|Exceptionactivityınstanceıd|xs: String|Özel durumu oluşturan etkinliğin örnek kimliği.|  
|Özel durum|xs: String|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
