---
title: Zaman uyumsuz etkinliklerde hata işleme
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: c63ce231687b03bdba57edd38c32270eabeff834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182943"
---
# <a name="error-handling-in-asynchronous-activities"></a>Zaman uyumsuz etkinliklerde hata işleme
Hata işlemeyi sağlamak, <xref:System.Activities.AsyncCodeActivity> hatanın etkinliğin geri arama sistemi aracılığıyla yönlendirmesini gerektirir. Bu konu, SendMail etkinlik örneğini kullanarak eşzamanlı bir işlemle ana bilgisayara geri atılan bir hatanın nasıl alınılacağını açıklar.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Eşzamanlı bir etkinlikte atılan bir hatayı ana bilgisayara geri döndürme  
 SendMail etkinlik örneğindeki bir eşzamanlı işlemdeki bir hatayı ana bilgisayara yönlendirme, aşağıdaki adımları içerir:  
  
- `SendMailAsyncResult` Sınıfa bir Özel Durum özelliği ekleyin.  
  
- Atılan hatayı olay işleyicisi olarak bu özelliğe kopyalayın. `SendCompleted`  
  
- Olay işleyicisi `EndExecute` özel durum atın.  
  
 Ortaya çıkan kod aşağıdaki gibidir.  
  
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
