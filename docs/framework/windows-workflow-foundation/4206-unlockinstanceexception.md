---
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 3c981888b491f2797a431c2103ba3f5f0bd17046
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774328"
---
# <a name="4206---unlockinstanceexception"></a>4206 - UnlockInstanceException
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4206|  
|anahtar sözcükler|WFInstanceStore|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir örneği kilidini çalışılırken bir özel durumla karşılaşıldı gösterir.  
  
## <a name="message"></a>İleti  
 Örnek kilidini açmak çalışırken karşılaşılan %1 özel durumu.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:string|SQL özel durum ileti.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
