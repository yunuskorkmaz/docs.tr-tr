---
title: Zaman uyumsuz etkinlikleri işleme hatası
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 4a7cbecef596eec6eaa128b8ffc7bc5c6e4b79bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511988"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="10009-102">Zaman uyumsuz etkinlikleri işleme hatası</span><span class="sxs-lookup"><span data-stu-id="10009-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="10009-103">Hata olarak işleme sağlayan bir <xref:System.Activities.AsyncCodeActivity> etkinliğin geri çağırma sistemi aracılığıyla hata yönlendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="10009-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="10009-104">Bu konu, zaman uyumsuz bir işlem SendMail etkinliği örneği kullanarak geri konağa durum bir hata alıyorsunuz açıklar.</span><span class="sxs-lookup"><span data-stu-id="10009-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="10009-105">Zaman uyumsuz bir etkinlikte konağa geri durum bir hata döndürüyor</span><span class="sxs-lookup"><span data-stu-id="10009-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="10009-106">Zaman uyumsuz bir işlem SendMail etkinlik örnekteki konağa hata yönlendirme aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="10009-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="10009-107">Bir özel durum özelliği Ekle `SendMailAsyncResult` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="10009-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="10009-108">Bu özelliğe kopyalama atılmış hatası `SendCompleted` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="10009-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="10009-109">Özel durum `EndExecute` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="10009-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="10009-110">Sonuçta elde edilen kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="10009-110">The resulting code is as follows.</span></span>  
  
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
