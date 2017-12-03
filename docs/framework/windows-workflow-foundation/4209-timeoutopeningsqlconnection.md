---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d971a2e5f1257281c453e7eb0c2dc1755098d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4209|  
|Anahtar Sözcükler|WFInstanceStore|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 SQL bağlantısı açılmaya çalışırken zaman aşımı oluştu gösterir.  
  
## <a name="message"></a>İleti  
 SQL bağlantısı açılmaya çalışılırken zaman aşımı. İşlemi %1 ' ayrılan süre içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Zaman aşımı|xs: String|SQL Bağlantısı açmak için zaman aşımı değeri.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
