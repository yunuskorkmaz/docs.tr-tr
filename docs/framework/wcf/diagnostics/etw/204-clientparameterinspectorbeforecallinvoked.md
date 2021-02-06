---
description: 'Hakkında daha fazla bilgi edinin: 204-Clientparameterınspectorbefoyeniden hesaplama Linvoked'
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: fa5646da7c48f624dc40f4fcc54a890c0758b4ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645002"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a>204 - ClientParameterInspectorBeforeCallInvoked

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|204|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modeli `BeforeCall` bir istemci parametresi denetçisinde yöntemi çağırdıktan sonra yayınlanır.  
  
## <a name="message"></a>İleti  

 Dağıtıcı, ' %1 ' türünde bir Clientparameterınspector üzerinde ' Befohatırla ' çağırdı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Çağrılan Inspector türünün CLR FullName değeri.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
