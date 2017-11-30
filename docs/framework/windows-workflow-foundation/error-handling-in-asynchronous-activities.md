---
title: "Zaman uyumsuz etkinlikleri işleme hatası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7606aeeeb3e2e583f9a217b78bcae4aebc6d8662
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-in-asynchronous-activities"></a>Zaman uyumsuz etkinlikleri işleme hatası
Hata olarak işleme sağlayan bir <xref:System.Activities.AsyncCodeActivity> etkinliğin geri çağırma sistemi aracılığıyla hata yönlendirme içerir. Bu konu, zaman uyumsuz bir işlem SendMail etkinliği örneği kullanarak geri konağa durum bir hata alıyorsunuz açıklar.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Zaman uyumsuz bir etkinlikte konağa geri durum bir hata döndürüyor  
 Zaman uyumsuz bir işlem SendMail etkinlik örnekteki konağa hata yönlendirme aşağıdaki adımları içerir:  
  
-   Bir özel durum özelliği Ekle `SendMailAsyncResult` sınıfı.  
  
-   Bu özelliğe kopyalama atılmış hatası `SendCompleted` olay işleyicisi.  
  
-   Özel durum `EndExecute` olay işleyicisi.  
  
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
