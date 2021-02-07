---
description: 'Hakkında daha fazla bilgi edinin: 1031-Completefaultworkıtem'
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: dc5cb4988df2aab9710fd7ec875d9b4004bfa7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668077"
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1031|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir FaultWorkItem 'ın tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem tamamlandı. Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.  
  
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
