---
description: 'Hakkında daha fazla bilgi edinin: 4210-Sqlexceptionyakalandı'
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 58846d02b6d1e388e3aef2bff76f51cba4990f2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777885"
---
# <a name="4210---sqlexceptioncaught"></a>4210 - SqlExceptionCaught

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4210|  
|Anahtar sözcükler|Wfınstancestore|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir SQL özel durumunun yakalandığını gösterir.  
  
## <a name="message"></a>İleti  

 Yakalanan SQL özel durum numarası %1 ileti %2.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs: String|SQL hata numarası.|  
|ExceptionMessage|xs: String|SQL özel durumunun iletisi.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
