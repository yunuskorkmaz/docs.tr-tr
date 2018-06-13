---
title: 2578 - TryCatchExceptionFromCatchOrFinally
ms.date: 03/30/2017
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
ms.openlocfilehash: 46fb52e665d49ed7a0336dbeeb6ed07f0d479fb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511533"
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a>2578 - TryCatchExceptionFromCatchOrFinally
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|2578|  
|Anahtar Sözcükler|WFActivities|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Son olarak, etkinlik bir özel durum oluşturdu veya bir Catch gösterir.  
  
## <a name="message"></a>İleti  
 Catch veya Finally TryCatch etkinliği '%1' ile ilişkili etkinliği bir özel durum oluşturdu.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Görünen adı|xs: String|Etkinliğin görünen adı.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
