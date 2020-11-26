---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 4bb76a93ec7a07a735def1f1d5dc79decb7792ad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239841"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1006|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Hata|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir iş akışı uygulamasının işlenmemiş bir özel durumla karşılaşdığını gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowInstance kimliği: ' %1 ' işlenmeyen bir özel durumla karşılaştı.  DisplayName: ' %3 ' olan ' %2 ' etkinliğinden kaynaklanan özel durum.  Şu işlem gerçekleştirilecek: %4.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışının örnek kimliği|  
|Özel durum|`xs:string`|Özel durum için özel durum ayrıntıları|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
