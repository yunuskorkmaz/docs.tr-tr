---
title: 4205 - FoundProcessingError
ms.date: 03/30/2017
ms.assetid: f2235a15-dd87-439e-8cb9-8b1b89a3dacf
ms.openlocfilehash: 732632ddc9a7712169ace984c1d6d0098a7ae608
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774341"
---
# <a name="4205---foundprocessingerror"></a>4205 - FoundProcessingError
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4205|  
|anahtar sözcükler|WFInstanceStore|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 SQL sağlayıcı komutu başarısız oldu gösterir.  
  
## <a name="message"></a>İleti  
 Komutu başarısız oldu: %1  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:string|SQL özel durum ileti.|  
|Özel Durum|xs:string|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
