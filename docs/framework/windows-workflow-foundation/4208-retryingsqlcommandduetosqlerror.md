---
description: 'Hakkında daha fazla bilgi edinin: 4208-RetryingSqlCommandDueToSqlError'
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 11ea2260f6a2ceffc1ffdbfce2cb3e3ce784076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755310"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a>4208 - RetryingSqlCommandDueToSqlError

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4208|  
|Anahtar sözcükler|Wfınstancestore|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 SQL sağlayıcısı 'nın bir SQL hatası nedeniyle bir SQL komutu yeniden denediğini belirtir.  
  
## <a name="message"></a>İleti  

 %1 numaralı SQL hatası nedeniyle bir SQL komutu yeniden deneniyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs: String|SQL hata numarası.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
