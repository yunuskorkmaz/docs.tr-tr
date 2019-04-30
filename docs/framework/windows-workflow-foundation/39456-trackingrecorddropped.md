---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774432"
---
# <a name="39456---trackingrecorddropped"></a>39456 - TrackingRecordDropped
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|39456|  
|anahtar sözcükler|WFTracking|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 ETW oturumu sağlayıcı tarafından izin verilen maksimum boyutunu aştığı için bir izleme kaydını bırakıldı gösterir.  
  
## <a name="message"></a>İleti  
 ETW oturumu tarafından %2 sağlayıcısı için izin verilen en fazla kayıt %1 izleme boyutunu aşıyor  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Özel Durum|xs:string|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
