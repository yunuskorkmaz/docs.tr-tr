---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: bd3e7539922e6c430c4ffe5bd96ef1ac7dbd098f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261169"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3552|  
|Anahtar sözcükler|Kota, Wfservice|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 ' Maxpendingiletiperchannel ' limitinin isabet aldığını gösterir.  
  
## <a name="message"></a>İleti  

 ' Maxpendingiletiperchannel ' kısıtlama ' %1 ' sınırına ulaşıldı. Bu sınırı artırmak için, BufferedReceiveServiceBehavior üzerindeki Maxpendingiletiperchannel özelliğini ayarlayın.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Sınır|xs: String|Maxpendingiletiperchannel kısıtlama sınırı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
