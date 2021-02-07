---
description: 'Hakkında daha fazla bilgi edinin: 1029-Schedulefaultworkıtem'
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: e5f0463626882d6c8c48412326582fafa7be4670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755453"
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1029|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir FaultWorkItem zamanlandığı olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem zamanlandı.  Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.  
  
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
