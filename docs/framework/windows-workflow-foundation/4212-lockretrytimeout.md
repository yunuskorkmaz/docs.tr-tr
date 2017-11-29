---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 897e6ef8b739654a61058106966c870c47f8129a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="4212---lockretrytimeout"></a>4212 - LockRetryTimeout
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4212|  
|Anahtar Sözcükler|WFInstanceStore|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 SQL sağlayıcısı örneği kilidi çalışılırken zaman aşımıyla karşılaştı.  
  
## <a name="message"></a>İleti  
 Örnek kilidi çalışılırken zaman aşımı.  İşlemi %1 ' ayrılan süre içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Gecikme|xs: String|Denemeler arasındaki gecikme.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
