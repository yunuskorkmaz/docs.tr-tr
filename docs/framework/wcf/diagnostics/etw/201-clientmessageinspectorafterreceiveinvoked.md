---
description: 'Hakkında daha fazla bilgi edinin: 201-ClientMessageInspectorAfterReceiveInvoked'
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 511f8bd039219d031c311f7def7b360b74df1a0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645158"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a>201 - ClientMessageInspectorAfterReceiveInvoked

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|201|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modeli `AfterReceiveReply` bir istemci ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.  
  
## <a name="message"></a>İleti  

 Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' AfterReceiveReply ' çağırdı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Çağrılan Inspector türünün CLR FullName değeri.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
