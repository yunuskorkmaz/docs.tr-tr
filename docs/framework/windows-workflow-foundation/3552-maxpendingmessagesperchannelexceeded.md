---
description: 'Hakkında daha fazla bilgi edinin: 3552-Maxpendingiletiperchannelexcebaşında'
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: 5fb2d27f7d68716cebf2cfaafd21851226a456e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631443"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3552|  
|Anahtar sözcükler|Kota, Wfservice|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 ' Maxpendingiletiperchannel ' limitinin isabet aldığını gösterir.  
  
## <a name="message"></a>İleti  

 ' Maxpendingiletiperchannel ' kısıtlama ' %1 ' sınırına ulaşıldı. Bu sınırı artırmak için, BufferedReceiveServiceBehavior üzerindeki Maxpendingiletiperchannel özelliğini ayarlayın.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Sınır|xs: String|Maxpendingiletiperchannel kısıtlama sınırı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
