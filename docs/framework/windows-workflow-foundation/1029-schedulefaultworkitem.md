---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ba1ae69caff2e08da58e824d35341d3781ea8ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
