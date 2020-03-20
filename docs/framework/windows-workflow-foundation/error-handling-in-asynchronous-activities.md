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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="b99cf-102">Zaman uyumsuz etkinliklerde hata işleme</span><span class="sxs-lookup"><span data-stu-id="b99cf-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="b99cf-103">Hata işlemeyi sağlamak, <xref:System.Activities.AsyncCodeActivity> hatanın etkinliğin geri arama sistemi aracılığıyla yönlendirmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b99cf-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="b99cf-104">Bu konu, SendMail etkinlik örneğini kullanarak eşzamanlı bir işlemle ana bilgisayara geri atılan bir hatanın nasıl alınılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b99cf-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="b99cf-105">Eşzamanlı bir etkinlikte atılan bir hatayı ana bilgisayara geri döndürme</span><span class="sxs-lookup"><span data-stu-id="b99cf-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="b99cf-106">SendMail etkinlik örneğindeki bir eşzamanlı işlemdeki bir hatayı ana bilgisayara yönlendirme, aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="b99cf-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="b99cf-107">`SendMailAsyncResult` Sınıfa bir Özel Durum özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b99cf-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="b99cf-108">Atılan hatayı olay işleyicisi olarak bu özelliğe kopyalayın. `SendCompleted`</span><span class="sxs-lookup"><span data-stu-id="b99cf-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="b99cf-109">Olay işleyicisi `EndExecute` özel durum atın.</span><span class="sxs-lookup"><span data-stu-id="b99cf-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="b99cf-110">Ortaya çıkan kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="b99cf-110">The resulting code is as follows.</span></span>  
  
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
