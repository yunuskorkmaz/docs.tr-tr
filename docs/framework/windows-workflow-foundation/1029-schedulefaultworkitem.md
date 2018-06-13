---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509736"
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1029|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir FaultWorkItem zamanlanmış gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliği için bir FaultWorkItem zamanlandı: '%2', örnek kimliği: '%3'.  Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs: String|Hataya etkinlik türü adı.|  
|FaultActivityDisplayName|xs: String|Hataya etkinlik görünen adı.|  
|FaultActivityInstanceId|xs: String|Hataya etkinlik örnek kimliği.|  
|ExceptionActivity|xs: String|Özel durum oluşturdu etkinlik türü adı.|  
|ExceptionActivityDisplayName|xs: String|Özel durum oluşturdu etkinliğin görünen adı.|  
|ExceptionActivityInstanceId|xs: String|Özel durum oluşturdu etkinlik örnek kimliği.|  
|Özel Durum|xs: String|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
