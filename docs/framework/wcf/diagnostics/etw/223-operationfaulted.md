---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0428d90135823761e7b8a12f560786e34e12734
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|223|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yayılan zaman hizmeti modelinin varsayılan `OperationInvoker` türetme bir özel durumla karşılaştı `FaultException` kendi yöntemi çağrılırken hata.  
  
## <a name="message"></a>İleti  
 '%1' yöntemi bir FaultException OperationInvoker tarafından çağrıldığında oluşturdu. Yöntem çağrısı süre, '%2' ms idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.|  
|Süre|`xs:long`|Geçen milisaniye cinsinden süre `OperationInvoker` yöntemini çağırmak için.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
