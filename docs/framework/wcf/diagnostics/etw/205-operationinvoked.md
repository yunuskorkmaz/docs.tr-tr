---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="205---operationinvoked"></a>205 - OperationInvoked
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|205|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yalnızca hizmet modelinin varsayılan önce gösterilen `OperationInvoker` bir yöntemine yapılan bir çağrı başlar.  
  
## <a name="message"></a>İleti  
 '%1' yöntemi bir OperationInvoker çağrılır. Arayan bilgileri: '%2'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.|  
|Arayan Bilgileri|`xs:string`|'IPAddress:PortNumber' biçiminde istemci IP adresi ve bağlantı noktası numarası. İki değer 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' ileti özelliği işlemi bağlamında alınır. TCP olmayan bağlantılarında unutmayın bu değer `null`.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
