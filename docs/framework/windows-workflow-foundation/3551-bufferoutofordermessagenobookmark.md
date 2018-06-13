---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512238"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|3551|  
|Anahtar Sözcükler|WFServices|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Yer işareti sürdürme başarısız oldu gösterir. Arabellekli alma işlemi hizmet örneği belirli bu işlemi hazır olduğunda yeniden denenecek.  
  
## <a name="message"></a>İleti  
 Hizmet örneği '%1' işlemi '%2', şu anda gerçekleştirilemiyor. Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs: String|İşlemin adı.|  
|Serviceınstanceıd|xs: String|Hizmet örneği kimliği.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
