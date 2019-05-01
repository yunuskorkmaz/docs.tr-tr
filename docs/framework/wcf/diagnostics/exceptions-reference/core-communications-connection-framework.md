---
title: 'Temel İletişimler: Bağlantı Çerçevesi'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998692"
---
# <a name="core-communications-connection-framework"></a>Temel İletişimler: Bağlantı Çerçevesi
Bu konu, Windows Communication Foundation (WCF) bağlantı Framework tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|CloseTimedOut|Close yöntemi belirtilen zamandan sonra zaman aşımına uğradı. Close çağrısına geçirilen zaman aşımı değerini artırın ya da binding üstündeki CloseTimeout değerini artırın. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.|  
|ContentTypeMismatch|Belirtilen içerik türü, belirtilen bekliyor bir hizmete gönderildi. İstemci ve hizmet bağlamaları eşleşmiyor olabilir.|  
|DuplexChannelAbortedDuringOpen|Belirtilen çift yönlü kanalı açma işlemi sırasında sonlandırıldı.|  
|FramingValueNotAvailable|Bu değil tam olduğu için kodu çünkü değer erişilemez.|  
|OperationAbortedDuringConnectionEstablishment|Belirtilen bağlantı kurarken işlemi sonlandırıldı.|  
|ReceiveTimedOut2|Alma işlemi belirtilen zamandan sonra zaman aşımına uğradı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.|  
|SendCannotBeCalledAfterCloseOutputSession|CloseOutputSession çağrıldıktan sonra bir kanalda ileti gönderemezsiniz.|
