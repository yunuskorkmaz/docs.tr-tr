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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="b15f0-103">Zaman uyumsuz etkinliklerde hata işleme</span><span class="sxs-lookup"><span data-stu-id="b15f0-103">Error handling in asynchronous activities</span></span>

<span data-ttu-id="b15f0-104">Bir içinde hata işleme sağlamak <xref:System.Activities.AsyncCodeActivity> , hatanın etkinliğin geri çağırma sistemi aracılığıyla yönlendirilmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b15f0-104">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="b15f0-105">Bu konu, SendMail etkinlik örneği kullanılarak, zaman uyumsuz bir işlemde konağa geri döndürülen bir hatanın nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="b15f0-105">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="b15f0-106">Zaman uyumsuz bir etkinlikte oluşan bir hata, konağa geri döndürülüyor</span><span class="sxs-lookup"><span data-stu-id="b15f0-106">Returning an error thrown in an asynchronous activity back to the host</span></span>  

 <span data-ttu-id="b15f0-107">SendMail etkinlik örneğindeki ana bilgisayara geri zaman uyumsuz bir işlemde hata yönlendirme aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="b15f0-107">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="b15f0-108">Sınıfına bir özel durum özelliği ekleyin `SendMailAsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="b15f0-108">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="b15f0-109">Oluşturulan hatayı `SendCompleted` olay işleyicisindeki bu özelliğe kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b15f0-109">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="b15f0-110">Olay işleyicisinde özel durumu oluşturur `EndExecute` .</span><span class="sxs-lookup"><span data-stu-id="b15f0-110">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="b15f0-111">Elde edilen kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="b15f0-111">The resulting code is as follows.</span></span>  
  
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
