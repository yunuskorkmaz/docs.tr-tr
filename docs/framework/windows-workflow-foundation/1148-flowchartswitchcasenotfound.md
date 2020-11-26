---
title: 1148 - FlowchartSwitchCaseNotFound
ms.date: 03/30/2017
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
ms.openlocfilehash: fb9f4be3dba0f8632f1ae074ad9ddb726c5d84ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241713"
---
# <a name="1148---flowchartswitchcasenotfound"></a>1148 - FlowchartSwitchCaseNotFound

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1148|  
|Anahtar sözcükler|WFActivities|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir akış çizelgesi anahtarındaki eşleşen bir Case veya default Case bulunamadığını gösterir. Akış çizelgesi yürütme sona acaktır.  
  
## <a name="message"></a>İleti  

 Akış Çizelgesi ' %1 '/FlowSwitch-bir Case etkinliği veya Ifade sonucuyla eşleşen bir varsayılan durum bulamıyor. Akış çizelgesi yürütme sona acaktır.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|FlowChart|xs: String|Akış çizelgesinin görünen adı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
