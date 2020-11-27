---
title: Zaman uyumsuz etkinliklerde hata işleme
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 2c214ce1d0f435cda79deb6976ca9196a5d7aee1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280266"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="76dca-102">Zaman uyumsuz etkinliklerde hata işleme</span><span class="sxs-lookup"><span data-stu-id="76dca-102">Error handling in asynchronous activities</span></span>

<span data-ttu-id="76dca-103">Bir içinde hata işleme sağlamak <xref:System.Activities.AsyncCodeActivity> , hatanın etkinliğin geri çağırma sistemi aracılığıyla yönlendirilmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="76dca-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="76dca-104">Bu konu, SendMail etkinlik örneği kullanılarak, zaman uyumsuz bir işlemde konağa geri döndürülen bir hatanın nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="76dca-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="76dca-105">Zaman uyumsuz bir etkinlikte oluşan bir hata, konağa geri döndürülüyor</span><span class="sxs-lookup"><span data-stu-id="76dca-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  

 <span data-ttu-id="76dca-106">SendMail etkinlik örneğindeki ana bilgisayara geri zaman uyumsuz bir işlemde hata yönlendirme aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="76dca-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="76dca-107">Sınıfına bir özel durum özelliği ekleyin `SendMailAsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="76dca-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="76dca-108">Oluşturulan hatayı `SendCompleted` olay işleyicisindeki bu özelliğe kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="76dca-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="76dca-109">Olay işleyicisinde özel durumu oluşturur `EndExecute` .</span><span class="sxs-lookup"><span data-stu-id="76dca-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="76dca-110">Elde edilen kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="76dca-110">The resulting code is as follows.</span></span>  
  
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
