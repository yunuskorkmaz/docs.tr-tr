---
description: 'Daha fazla bilgi edinin: zaman uyumsuz etkinliklerde hata işleme'
title: Zaman uyumsuz etkinliklerde hata işleme
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: df223998737259aca01a4dc18ed9f2a911d80366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742413"
---
# <a name="error-handling-in-asynchronous-activities"></a>Zaman uyumsuz etkinliklerde hata işleme

Bir içinde hata işleme sağlamak <xref:System.Activities.AsyncCodeActivity> , hatanın etkinliğin geri çağırma sistemi aracılığıyla yönlendirilmesini içerir. Bu konu, SendMail etkinlik örneği kullanılarak, zaman uyumsuz bir işlemde konağa geri döndürülen bir hatanın nasıl alınacağını açıklamaktadır.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Zaman uyumsuz bir etkinlikte oluşan bir hata, konağa geri döndürülüyor  

 SendMail etkinlik örneğindeki ana bilgisayara geri zaman uyumsuz bir işlemde hata yönlendirme aşağıdaki adımları içerir:  
  
- Sınıfına bir özel durum özelliği ekleyin `SendMailAsyncResult` .  
  
- Oluşturulan hatayı `SendCompleted` olay işleyicisindeki bu özelliğe kopyalayın.  
  
- Olay işleyicisinde özel durumu oluşturur `EndExecute` .  
  
 Elde edilen kod aşağıdaki gibidir.  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;
        }  
    }  
```
