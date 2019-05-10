---
title: Zaman uyumsuz etkinliklerde hata işleme
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 7a1db144e4738870d3ff5fe68df11b2fb06ef3d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640957"
---
# <a name="error-handling-in-asynchronous-activities"></a>Zaman uyumsuz etkinliklerde hata işleme
Hata işleme sağlayan bir <xref:System.Activities.AsyncCodeActivity> etkinliğin geri çağırma sistemi üzerinden hata yönlendirme gerektirir. Bu konuda, zaman uyumsuz bir işlemde SendMail etkinlik örneğini kullanarak geri konağa oluşturulan hata açıklar.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Konağa geri zaman uyumsuz bir etkinlik içinde oluşan bir hata döndürüyor  
 Zaman uyumsuz bir işlem geri SendMail etkinlik örnek konak için bir hata yönlendirme, aşağıdaki adımları içerir:  
  
- Bir özel durum özelliğine Ekle `SendMailAsyncResult` sınıfı.  
  
- Bu özelliği hatadır kopyalayın `SendCompleted` olay işleyicisi.  
  
- Özel durum `EndExecute` olay işleyicisi.  
  
 Sonuçta elde edilen kod aşağıdaki gibidir.  
  
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
