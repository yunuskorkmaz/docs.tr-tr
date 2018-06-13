---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510763"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1006|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı uygulaması işlenmeyen bir özel durumla karşılaştı gösterir.  
  
## <a name="message"></a>İleti  
 İş akışı örneği kimliği: '%1' işlenmeyen bir özel durumla karşılaştı.  Özel durum '%2', DisplayName etkinliğinden kaynaklanan: '%3'.  Aşağıdaki işlem yapılmaz: %4.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceID|`xs:string`|İş akışı için örnek kimliği|  
|Özel Durum|`xs:string`|Özel durum için özel durum ayrıntıları|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
