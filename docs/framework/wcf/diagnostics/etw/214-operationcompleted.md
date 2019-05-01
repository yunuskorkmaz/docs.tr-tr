---
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968005"
---
# <a name="214---operationcompleted"></a>214 - OperationCompleted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|214|  
|anahtar sözcükler|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yayılan olduğunda hizmet modelinin varsayılan `OperationInvoker` bir yönteme bir çağrı o yöntemi bir özel durum tamamlandı.  
  
## <a name="message"></a>İleti  
 '%1' yöntemine çağrı bir OperationInvoker tamamlandı. Yöntem çağrısı süresi '%2' ms idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|CLR adı tarafından çağrılan yöntemin `OperationInvoker`.|  
|Süresi|`xs:long`|Geçen milisaniye cinsinden zaman `OperationInvoker` yöntemini çağırmak için.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
