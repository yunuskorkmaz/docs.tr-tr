---
description: 'Hakkında daha fazla bilgi edinin: 207-Faultproviderçağrılan'
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 03c4f1669fc61019ccf4d23d2994f136e231fbec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728073"
---
# <a name="207---faultproviderinvoked"></a>207 - FaultProviderInvoked

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|207|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir `FaultProvider` çağrıldıktan sonra yayınlanır.  
  
## <a name="message"></a>İleti  

 Dağıtıcı, ' %2 ' türünde bir özel durum ile ' %1 ' türünde bir FaultProvider çağırdı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Çağrılan türünün CLR FullName değeri `FaultProvider` .|  
|ExceptionTypeName|`xs:string`|Üzerinde işletitilen özel durumun CLR FullName değeri `FaultProvider` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
