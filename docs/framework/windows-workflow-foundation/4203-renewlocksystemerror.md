---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774354"
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4203|  
|anahtar sözcükler|WFInstanceStore|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 SQL sağlayıcısı zaten geçirilen ya da kilit zaman aşımı nedeniyle kilit zaman aşımı genişletmek başarısız oldu veya kilit sahibi silindi gösterir. SqlWorkflowInstanceStore iptal edilecek.  
  
## <a name="message"></a>İleti  
 Kilit zaman aşımı genişletmek için başarısız oldu, kilit zaman aşımı zaten geçirildi veya kilit sahibi silindi. SqlWorkflowInstanceStore durduruluyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
