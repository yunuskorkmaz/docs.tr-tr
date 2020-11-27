---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: b8bf8431c4e2b82c6aac95820eb45de2a404e976
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294280"
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1035|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir etkinliğin çalışma zamanı işlemini ayarlamış olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 Çalışma zamanı işlemi, DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' etkinliğine göre ayarlandı.  Yürütme, DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğine yalıtılmış.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|Isotedactivity|xs: String|İşlemin yalıtılmış olduğu etkinliğin tür adı.|  
|Isotedactivitydisplayname|xs: String|İşlemin yalıtılmış olduğu etkinliğin görünen adı.|  
|Isotedactivityınstanceıd|xs: String|İşlemin yalıtılmış olduğu etkinliğin örnek kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
