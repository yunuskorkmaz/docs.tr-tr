---
description: 'Hakkında daha fazla bilgi edinin: 4212-LockRetryTimeout'
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: a2299d0d9643fb60ff420519fb43199e3f747c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667089"
---
# <a name="4212---lockretrytimeout"></a>4212 - LockRetryTimeout

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4212|  
|Anahtar sözcükler|Wfınstancestore|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 SQL sağlayıcısı örnek kilidini edinmeye çalışırken bir zaman aşımıyla karşılaştı.  
  
## <a name="message"></a>İleti  

 Örnek kilidi alınmaya çalışılırken zaman aşımı oluştu.  İşlem ayrılan %1 zaman aşımı süresi içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Gecikme|xs: String|Yeniden denemeler arasındaki gecikme.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
