---
description: 'Hakkında daha fazla bilgi edinin: 4209-TimeoutOpeningSqlConnection'
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9c7540e328530fdc01b9f065dfb75b92c467bd43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788000"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4209|  
|Anahtar sözcükler|Wfınstancestore|  
|Level|Hata|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir SQL bağlantısı açılmaya çalışılırken zaman aşımıyla karşılaşıldı.  
  
## <a name="message"></a>İleti  

 SQL bağlantısı açılmaya çalışılırken zaman aşımı oluştu. İşlem ayrılan %1 zaman aşımı süresi içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Zaman aşımı|xs: String|SQL bağlantısını açmak için zaman aşımı değeri.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
