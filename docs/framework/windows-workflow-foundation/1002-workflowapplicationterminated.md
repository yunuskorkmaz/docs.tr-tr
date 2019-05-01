---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008661"
---
# <a name="1002---workflowapplicationterminated"></a>1002 - WorkflowApplicationTerminated
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1002|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Faulted durumunda bir özel durum ile bir iş akışı uygulaması sonlandırıldı gösterir.  
  
## <a name="message"></a>İleti  
 WorkflowApplication ID: '%1' sonlandırıldı. Faulted durumunda bir özel durum ile tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|İş akışı uygulama kimliği|  
|Özel Durum|`xs:string`|Özel durum için özel durum ayrıntıları|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
