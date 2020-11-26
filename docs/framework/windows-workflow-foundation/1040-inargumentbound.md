---
title: 1040 - InArgumentBound
ms.date: 03/30/2017
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
ms.openlocfilehash: 04a61892ea817d5168ccbfccf68c0b74ee43e983
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238957"
---
# <a name="1040---inargumentbound"></a>1040 - InArgumentBound

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1040|  
|Anahtar sözcükler|WFActivities|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir ın bağımsız değişkeninin bağlandığını belirtir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %3 ', InstanceId: ' %4 ' olan ' %2 ' etkinliğindeki ' %1 ' bağımsız değişkeninde %5 değeri ile bağlı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InArgument 'ı|xs: String|InArgument adı.|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|Değer|xs: String|Değer InArgument 'a bağlanır.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
