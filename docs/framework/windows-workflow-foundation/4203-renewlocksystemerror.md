---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4203|  
|Anahtar Sözcükler|WFInstanceStore|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 SQL sağlayıcısı kilitleme sona ermesi zaten geçirilen ya da kilitleme sona erme nedeniyle genişletmek başarısız oldu veya kilit sahibi silindi gösterir. SqlWorkflowInstanceStore iptal edilecek.  
  
## <a name="message"></a>İleti  
 Kilitleme sona erme genişletmek için başarısız oldu, zaten kilitleme sona erme geçirilen veya kilit sahibi silindi. SqlWorkflowInstanceStore durduruluyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
