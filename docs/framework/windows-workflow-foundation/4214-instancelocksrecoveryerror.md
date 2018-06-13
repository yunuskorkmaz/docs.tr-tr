---
title: 4214 - InstanceLocksRecoveryError
ms.date: 03/30/2017
ms.assetid: d28fb2d5-bf15-4648-8d20-8141ad16f04b
ms.openlocfilehash: 247b105cf4e5a9d5c3c4b4d36a282763044658a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511913"
---
# <a name="4214---instancelocksrecoveryerror"></a>4214 - InstanceLocksRecoveryError
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4214|  
|Anahtar Sözcükler|WFInstanceStore|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Örnek kilitleri kurtarma, bir özel durum nedeniyle başarısız oldu.  
  
## <a name="message"></a>İleti  
 Kurtarılan örneğini kilitleri şu özel durum nedeniyle başarısız oldu  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Özel Durum|xs: String|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
