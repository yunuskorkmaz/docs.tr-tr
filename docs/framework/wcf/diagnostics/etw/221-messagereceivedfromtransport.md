---
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781725"
---
# <a name="221---messagereceivedfromtransport"></a>221 - MessageReceivedFromTransport
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|221|  
|anahtar sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring,|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, hizmet modeli, aktarımdan bir ileti aldığı zaman yayınlanır.  
  
## <a name="message"></a>İleti  
 Dağıtıcı taşımadan bir ileti alındı. Bağıntı Kimliği '%1' ==.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Bağıntı Kimliği|`xs:GUID`|Etkinlik ilişkilendirmek için kullanılan bir `MessageSentToTransport` , karşılık gelen bir hizmet veya istemci olayı `MessageReceivedFromTransport` diğer ucundaki.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
