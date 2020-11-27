---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 17617e25c5cf8cecae608438529e9ce1a7d506f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251275"
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4203|  
|Anahtar sözcükler|Wfınstancestore|  
|Düzey|Hata|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Kilit sona erme süresi geçtiğinden veya kilit sahibi silindiğinden SQL sağlayıcısı 'nın kilit sona erme süresini genişlemediğini belirtir. SqlWorkflowInstanceStore iptal edilecek.  
  
## <a name="message"></a>İleti  

 Kilit süre sonu genişletilemedi, kilit süre sonu zaten geçti veya kilit sahibi silindi. SqlWorkflowInstanceStore durduruluyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
