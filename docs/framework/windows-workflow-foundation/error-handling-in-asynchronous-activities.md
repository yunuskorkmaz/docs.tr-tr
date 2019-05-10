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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="6ad6b-102">Zaman uyumsuz etkinliklerde hata işleme</span><span class="sxs-lookup"><span data-stu-id="6ad6b-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="6ad6b-103">Hata işleme sağlayan bir <xref:System.Activities.AsyncCodeActivity> etkinliğin geri çağırma sistemi üzerinden hata yönlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6ad6b-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="6ad6b-104">Bu konuda, zaman uyumsuz bir işlemde SendMail etkinlik örneğini kullanarak geri konağa oluşturulan hata açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad6b-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="6ad6b-105">Konağa geri zaman uyumsuz bir etkinlik içinde oluşan bir hata döndürüyor</span><span class="sxs-lookup"><span data-stu-id="6ad6b-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="6ad6b-106">Zaman uyumsuz bir işlem geri SendMail etkinlik örnek konak için bir hata yönlendirme, aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="6ad6b-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="6ad6b-107">Bir özel durum özelliğine Ekle `SendMailAsyncResult` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6ad6b-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="6ad6b-108">Bu özelliği hatadır kopyalayın `SendCompleted` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6ad6b-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="6ad6b-109">Özel durum `EndExecute` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6ad6b-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="6ad6b-110">Sonuçta elde edilen kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="6ad6b-110">The resulting code is as follows.</span></span>  
  
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
