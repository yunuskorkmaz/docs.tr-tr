---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 9995823753fc78ca3f278cd635fcf6c7d2b84325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238944"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1041|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir iş akışı uygulamasının boşta ve kalıcı olduğunu gösterir. İş akışı uygulaması bırakılacak veya kalıcı olacak.  
  
## <a name="message"></a>İleti  

 WorkflowApplication kimliği: ' %1 ' boşta ve sürekli tablo.  Şu işlem gerçekleştirilecek: %2.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Workflowapplicationıd|xs: String|İş akışı uygulama kimliği|  
|Gerçekleştirilen eylem|xs: String|İş akışı uygulamasında gerçekleştirilecek eylem.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
