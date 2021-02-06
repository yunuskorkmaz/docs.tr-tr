---
description: 'Hakkında daha fazla bilgi edinin: 202-Clientmessageınspectorbeforesendıned'
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 0267304ba805c8f23109c820c8516a27958c3040
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645054"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a>202 - ClientMessageInspectorBeforeSendInvoked

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|202|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modeli `BeforeSendRequest` bir istemci ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.  
  
## <a name="message"></a>İleti  

 Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' BeforeSendRequest ' çağırdı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Çağrılan Inspector türünün CLR FullName değeri.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
