---
description: 'Hakkında daha fazla bilgi edinin: 206-Errorhandlerçağrıldı'
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: addbcbdea25c7f8e7515b743e98e426476fa0b28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783787"
---
# <a name="206---errorhandlerinvoked"></a>206 - ErrorHandlerInvoked

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|206|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir `ErrorHandler` hizmet işleminde oluşan bir özel durumu işlemeye yönelik bir fırsata sahip olduktan sonra yayınlanır.  
  
## <a name="message"></a>İleti  

 Dağıtıcı, ' %3 ' türünde bir özel durum ile ' %1 ' türünde bir ErrorHandler çağırdı. Errorişlenmiş = = ' %2 '.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Çağrılan türünün CLR FullName değeri `ErrorHandler` .|  
|İşlenenler|`xs:unsignedByte`|`true` hata işleyicisi hatayı işleirse, tersi durumda `false` .|  
|ExceptionTypeName|`xs:string`|İşlenmekte olan özel durumun CLR FullName.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
