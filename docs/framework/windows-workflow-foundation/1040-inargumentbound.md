---
description: 'Şu konuda daha fazla bilgi edinin: 1040-ınargumentbağlanmadı'
title: 1040 - InArgumentBound
ms.date: 03/30/2017
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
ms.openlocfilehash: f604a2503bcaf407a9a690b5a681208815fd245a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667804"
---
# <a name="1040---inargumentbound"></a>1040 - InArgumentBound

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1040|  
|Anahtar sözcükler|WFActivities|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir ın bağımsız değişkeninin bağlandığını belirtir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %3 ', InstanceId: ' %4 ' olan ' %2 ' etkinliğindeki ' %1 ' bağımsız değişkeninde %5 değeri ile bağlı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InArgument 'ı|xs: String|InArgument adı.|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|Değer|xs: String|Değer InArgument 'a bağlanır.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
