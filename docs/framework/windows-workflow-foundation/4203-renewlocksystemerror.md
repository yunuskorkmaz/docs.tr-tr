---
description: 'Hakkında daha fazla bilgi edinin: 4203-RenewLockSystemError'
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 0e62c501391fcaec56f2016631707832170775ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792784"
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4203|  
|Anahtar sözcükler|Wfınstancestore|  
|Level|Hata|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Kilit sona erme süresi geçtiğinden veya kilit sahibi silindiğinden SQL sağlayıcısı 'nın kilit sona erme süresini genişlemediğini belirtir. SqlWorkflowInstanceStore iptal edilecek.  
  
## <a name="message"></a>İleti  

 Kilit süre sonu genişletilemedi, kilit süre sonu zaten geçti veya kilit sahibi silindi. SqlWorkflowInstanceStore durduruluyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
