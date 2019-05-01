---
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 4c9ae5fd386fc93ea19578097aa4e0afdda527e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924130"
---
# <a name="1104---workflowactivityresume"></a>1104 - WorkflowActivityResume
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1104|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı etkinliği devam ettirildi gösterir.  
  
## <a name="message"></a>İleti  
 WorkflowInstance ID: '%1' Aktivita E2E  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceID|xs:string|İş akışı örnek kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
