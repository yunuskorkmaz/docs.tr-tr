---
description: 'Hakkında daha fazla bilgi edinin: 1006-WorkflowApplicationUnhandledException'
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: bfccd0d12c5dac4caad1e84e95f1cd096a551aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755596"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1006|  
|Anahtar sözcükler|WFRuntime|  
|Level|Hata|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir iş akışı uygulamasının işlenmemiş bir özel durumla karşılaşdığını gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowInstance kimliği: ' %1 ' işlenmeyen bir özel durumla karşılaştı.  DisplayName: ' %3 ' olan ' %2 ' etkinliğinden kaynaklanan özel durum.  Şu işlem gerçekleştirilecek: %4.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışının örnek kimliği|  
|Özel durum|`xs:string`|Özel durum için özel durum ayrıntıları|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
