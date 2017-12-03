---
title: "En İyi Uygulamalar: Aracılar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfedfbd0177018de4affce67f16ee5f713f7d5de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="9db41-102">En İyi Uygulamalar: Aracılar</span><span class="sxs-lookup"><span data-stu-id="9db41-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="9db41-103">Hizmet tarafı kanalları aracı üzerinde düzgün kapalı olduğundan emin olmak için aracılar çağrılırken doğru hataları işlemek için dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9db41-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="9db41-104">Aşağıdaki senaryoyu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9db41-104">Consider the following scenario.</span></span> <span data-ttu-id="9db41-105">Bir istemci bir arka uç hizmeti çağıran bir aracı için bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="9db41-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="9db41-106">Bu hizmetinden durum hataya türsüz bir hata kabul edilecek şekilde arka uç hizmetine hiçbir hatalı sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9db41-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="9db41-107">Arka uç hizmetine atar bir <xref:System.ApplicationException> ve WCF doğru hizmet tarafı kanal durdurur.</span><span class="sxs-lookup"><span data-stu-id="9db41-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="9db41-108"><xref:System.ApplicationException> Olarak ortaya çıkarır bir <xref:System.ServiceModel.FaultException> aracı için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9db41-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="9db41-109">Aracıyı yeniden oluşturur <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="9db41-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="9db41-110">WCF bu aracı gelen türsüz bir hata olarak yorumlar ve istemci açın iletir.</span><span class="sxs-lookup"><span data-stu-id="9db41-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="9db41-111">Hataya alındıktan sonra hem bir aracı hem de istemci kendi istemci-tarafı kanalları hata.</span><span class="sxs-lookup"><span data-stu-id="9db41-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="9db41-112">WCF hata önemli bilmiyor olduğundan Aracı'nın hizmet tarafı kanal ancak açık kalır.</span><span class="sxs-lookup"><span data-stu-id="9db41-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="9db41-113">En iyi uygulama olarak bu senaryoda hizmetinden gelen önemli bir hatadır ve bu nedenle aracı kendi hizmet tarafı kanal aşağıdaki kod parçacığında gösterildiği gibi hata algılamaktır.</span><span class="sxs-lookup"><span data-stu-id="9db41-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9db41-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9db41-114">See Also</span></span>  
 [<span data-ttu-id="9db41-115">WCF hata işleme</span><span class="sxs-lookup"><span data-stu-id="9db41-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)  
 [<span data-ttu-id="9db41-116">Belirtme ve sözleşme ve hizmetlerde hataları işleme</span><span class="sxs-lookup"><span data-stu-id="9db41-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
