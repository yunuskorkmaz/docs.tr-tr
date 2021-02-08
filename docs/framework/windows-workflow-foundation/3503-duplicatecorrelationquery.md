---
description: 'Hakkında daha fazla bilgi edinin: 3503-DuplicateCorrelationQuery'
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: a8e1e41aad3aa1b273d8f8a5d7b0768fabe4e658
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778080"
---
# <a name="3503---duplicatecorrelationquery"></a>3503 - DuplicateCorrelationQuery

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3503|  
|Anahtar sözcükler|WFServices|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Yinelenen bir CorrelationQuery bulundu olduğunu gösterir. Bağıntı hesaplanırken yinelenen sorgu kullanılmayacak.  
  
## <a name="message"></a>İleti  

 Burada = ' %1 ' olan yinelenen bir CorrelationQuery bulundu. Bu yinelenen sorgu, bağıntı hesaplanırken kullanılmayacak.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Konum|xs: String|Bağıntı sorgusunun WHERE kısmı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
