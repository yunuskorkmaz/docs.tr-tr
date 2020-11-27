---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: e1e64824ee9a95757ed7c00aa17fa80898219401
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270334"
---
# <a name="3503---duplicatecorrelationquery"></a>3503 - DuplicateCorrelationQuery

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3503|  
|Anahtar sözcükler|WFServices|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Yinelenen bir CorrelationQuery bulundu olduğunu gösterir. Bağıntı hesaplanırken yinelenen sorgu kullanılmayacak.  
  
## <a name="message"></a>İleti  

 Burada = ' %1 ' olan yinelenen bir CorrelationQuery bulundu. Bu yinelenen sorgu, bağıntı hesaplanırken kullanılmayacak.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Konum|xs: String|Bağıntı sorgusunun WHERE kısmı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
