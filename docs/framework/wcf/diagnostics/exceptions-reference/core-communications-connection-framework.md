---
title: 'Temel İletişimler: Bağlantı Çerçevesi'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471982"
---
# <a name="core-communications-connection-framework"></a>Temel İletişimler: Bağlantı Çerçevesi
Bu konu, Windows Communication Foundation (WCF) bağlantı çerçevesi tarafından oluşturulan tüm özel durumları listeler.  
  
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
