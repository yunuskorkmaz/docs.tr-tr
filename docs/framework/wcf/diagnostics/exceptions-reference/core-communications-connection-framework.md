---
title: "Temel İletişimler: Bağlantı Çerçevesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 878d2b01ee22d339115925e101f7349ecd5207bd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-connection-framework"></a>Temel İletişimler: Bağlantı Çerçevesi
Bu konu tarafından oluşturulan tüm özel durumları listeler [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bağlantı çerçevesi.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|CloseTimedOut|Close yöntemi belirlenen süre sonunda zaman aşımına uğradı. Close çağrısına iletilen zaman aşımı değerini artırın veya bağlama üzerinde CloseTimeout değerini artırın. Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.|  
|ContentTypeMismatch|Belirtilen içerik türü belirtilen bekliyordu bir hizmete gönderildi. İstemci ve hizmet bağlamaları eşleşmiyor olabilir.|  
|DuplexChannelAbortedDuringOpen|Belirtilen çift yönlü kanalı açma işlemi sırasında sonlandırıldı.|  
|FramingValueNotAvailable|Bunu değil tam kodunu çözdü için değer erişilemez.|  
|OperationAbortedDuringConnectionEstablishment|Belirtilen bağlantı kurulurken işlemi sona erdirildi.|  
|ReceiveTimedOut2|Alma işlemi belirlenen süre sonunda zaman aşımına uğradı. Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.|  
|SendCannotBeCalledAfterCloseOutputSession|CloseOutputSession çağrıldıktan sonra bir kanalda iletileri gönderemez.|
