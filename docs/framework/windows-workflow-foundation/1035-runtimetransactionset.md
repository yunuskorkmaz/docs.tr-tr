---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924858"
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1035|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir etkinliğin çalışma zamanı işlem ayarladı gösterir.  
  
## <a name="message"></a>İleti  
 Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlanmış: '%2', InstanceId: '%3'.  '%4', DisplayName etkinlik için yalıtılmış yürütme: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs:string|Etkinlik türü adı.|  
|displayName|xs:string|Etkinliğin görünen adı.|  
|InstanceId|xs:string|Etkinlik örneği kimliği.|  
|IsolatedActivity|xs:string|İşlem için yalıtılmış etkinlik türü adı.|  
|IsolatedActivityDisplayName|xs:string|İşlem için yalıtılmış etkinliğin görünen adı.|  
|IsolatedActivityInstanceId|xs:string|İşlem için yalıtılmış etkinlik örneği kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
