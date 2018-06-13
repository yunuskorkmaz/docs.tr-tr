---
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: 6dfb3b187f58de2c9573c2d2f6d579e3557c3de8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33466606"
---
# <a name="402---startsignpostevent"></a>402 - StartSignpostEvent
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|402|  
|Anahtar Sözcükler|Sorun giderme|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay bir uçtan uca etkinlik başlangıcını işaretler. Bu etkinliğin adını içerir.  
  
## <a name="message"></a>İleti  
 Etkinlik sınırı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Genişletilmiş verileri|`xs:string`|Etkinlik adı.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
