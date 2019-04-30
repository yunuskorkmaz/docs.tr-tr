---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755590"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a>3550 - BufferOutOfOrderMessageNoInstance
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|3550|  
|anahtar sözcükler|WFServices|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Arabelleğe alınmış alma işlemi başarısız oldu gösterir. Hizmet örneği bu belirli bir işlemi hazır olduğunda işlem yeniden denenecek.  
  
## <a name="message"></a>İleti  
 '%1' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu belirli bir işlemi hazır olduğunda başka bir deneme yapılır.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|İşlemin adı.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
