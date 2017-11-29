---
title: 206 - ErrorHandlerInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84470cbaf7ba7951ef59b130c696462079216cde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="206---errorhandlerinvoked"></a>206 - ErrorHandlerInvoked
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|206|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay sonra yayılan bir `ErrorHandler` bir hizmet işlemi oluştu özel bir durumu işlemek için bir fırsat oluşturdu.  
  
## <a name="message"></a>İleti  
 Dağıtıcı '%3' türünde bir özel durum ile '%1' türünde bir ErrorHandler çağrılır. ErrorHandled == '%2'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Çağrılan türünün CLR FullName `ErrorHandler`.|  
|İşlenmiş|`xs:unsignedByte`|`true`hata işleyicisine hatası, aksi takdirde işleniyorsa `false`.|  
|ExceptionTypeName|`xs:string`|İşlenen özel durum CLR tam adı.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
