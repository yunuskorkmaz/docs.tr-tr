---
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459374"
---
# <a name="214---operationcompleted"></a>214 - OperationCompleted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|214|  
|Anahtar Sözcükler|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yayılan, hizmet modelinin varsayılan `OperationInvoker` bu yöntemi bir özel durum atma bir yöntem çağrısı tamamlandı.  
  
## <a name="message"></a>İleti  
 Bir OperationInvoker '%1' metodu çağrısı tamamlandı. Yöntem çağrısı süre, '%2' ms idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.|  
|Süre|`xs:long`|Geçen milisaniye cinsinden süre `OperationInvoker` yöntemini çağırmak için.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
