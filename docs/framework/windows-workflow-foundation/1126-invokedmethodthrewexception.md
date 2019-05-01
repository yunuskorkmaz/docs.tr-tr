---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 714a98a300426d80c3b494d701ae1bd53a49592f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924013"
---
# <a name="1126---invokedmethodthrewexception"></a>1126 - InvokedMethodThrewException
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1126|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 InvokeMethod etkinlik tarafından çağrılan yöntemi tarafından bir özel durum oluştu gösterir.  
  
## <a name="message"></a>İleti  
 Etkinlik tarafından '%1' adlı bir yöntemde özel durum oluşturuldu. %2  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|InvokeMethod etkinliği görünen adı.|  
|Özel Durum|xs:string|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
