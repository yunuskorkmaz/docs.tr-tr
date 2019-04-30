---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755538"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|3551|  
|anahtar sözcükler|WFServices|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir yer imi sürdürme başarısız oldu gösterir. Arabellekli alma işlemi hizmet örneği bu belirli bir işlemi hazır olduğunda tekrar denenecek.  
  
## <a name="message"></a>İleti  
 Hizmet örneği '%1' üzerinde '%2' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu belirli bir işlemi hazır olduğunda başka bir deneme yapılır.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|İşlemin adı.|  
|ServiceInstanceId|xs:string|Hizmet örneği kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
