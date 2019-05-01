---
title: 1103 - WorkflowActivitySuspend
ms.date: 03/30/2017
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
ms.openlocfilehash: 4311bd8dc1c5e2c43bf21b411a4c52a7bfc7b230
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052787"
---
# <a name="1103---workflowactivitysuspend"></a>1103 - WorkflowActivitySuspend
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1103|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı etkinlik askıya alındı gösterir.  
  
## <a name="message"></a>İleti  
 WorkflowInstance ID: '%1' Aktivita E2E  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceID|xs:string|İş akışı örnek kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
