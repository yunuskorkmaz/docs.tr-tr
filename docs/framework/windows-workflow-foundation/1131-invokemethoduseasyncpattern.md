---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512673"
---
# <a name="1131---invokemethoduseasyncpattern"></a>1131 - InvokeMethodUseAsyncPattern
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1131|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 CacheMetadata adımı sırasında InvokeMethod etkinlik, zaman uyumsuz desen yöntemi çağrılırken kullandığını belirtir.  
  
## <a name="message"></a>İleti  
 InvokeMethod '%1' - '%2' ve '%3' zaman uyumsuz desen yöntemi kullanır.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs: String|InvokeMethod etkinlik görünen adı.|  
|BeginMethod|xs: String|Begin yöntemi adı.|  
|EndMethod|xs: String|End yöntemi adı.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
