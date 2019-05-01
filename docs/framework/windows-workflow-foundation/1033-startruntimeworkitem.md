---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924247"
---
# <a name="1033---startruntimeworkitem"></a>1033 - StartRuntimeWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1033|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir RuntimeWorkItem yürütme başlanacağını gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliği için bir çalışma zamanı iş öğesinin yürütme başlatılıyor: '%2', InstanceId: '%3'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs:string|Etkinlik türü adı.|  
|displayName|xs:string|Etkinliğin görünen adı.|  
|InstanceId|xs:string|Etkinlik örneği kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
