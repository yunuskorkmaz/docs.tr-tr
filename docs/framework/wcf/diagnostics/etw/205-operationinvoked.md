---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781985"
---
# <a name="205---operationinvoked"></a>205 - OperationInvoked
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|205|  
|anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, yalnızca hizmet modelin varsayılan önce yayıldığını `OperationInvoker` bir yönteme bir çağrı başlar.  
  
## <a name="message"></a>İleti  
 '%1' yöntemi bir OperationInvoker çağrılır. Arayan bilgileri: '%2'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|CLR adı tarafından çağrılan yöntemin `OperationInvoker`.|  
|Arayan Bilgileri|`xs:string`|'IPAddress:PortNumber' biçimindeki istemci IP adresi ve bağlantı noktası numarası. İki değer işlem bağlamı içinde 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' iletisi özelliğinden alınır. TCP olmayan bağlamalarda unutmayın. Bu değer `null`.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
