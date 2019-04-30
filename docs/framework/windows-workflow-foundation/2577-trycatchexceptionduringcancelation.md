---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755629"
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 - TryCatchExceptionDuringCancelation
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|2577|  
|anahtar sözcükler|WFActivities|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 TryCatch etkinlik bir alt etkinlik iptal etme sırasında bir özel durum gösterir.  
  
## <a name="message"></a>İleti  
 TryCatch etkinlik '%1' bir alt etkinlik iptal etme sırasında bir özel durum oluşturdu.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|displayName|xs:string|Etkinliğin görünen adı.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
