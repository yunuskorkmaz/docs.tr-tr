---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: e7c92dcc9ce472c50af6f0aa26c59f55d62fbb9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239945"
---
# <a name="1002---workflowapplicationterminated"></a>1002 - WorkflowApplicationTerminated

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1002|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir iş akışı uygulamasının hatalı durumda bir özel durumla sonlandırdığını gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowApplication kimliği: ' %1 ' sonlandırıldı. Hatalı durumda bir özel durumla tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Workflowapplicationıd|`xs:string`|İş akışı uygulama kimliği|  
|Özel durum|`xs:string`|Özel durum için özel durum ayrıntıları|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
