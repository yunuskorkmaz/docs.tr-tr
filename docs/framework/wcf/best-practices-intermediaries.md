---
title: 'En İyi Yöntemler: Aracılar'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 0bd553486bfb89a0ec14c42a1bb7d2ed9c4c540d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608911"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="39b5c-102">En İyi Yöntemler: Aracılar</span><span class="sxs-lookup"><span data-stu-id="39b5c-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="39b5c-103">Doğru hizmet tarafı kanalları aracı düzgün şekilde kapatıldığından emin olmak için aracılar çağrılırken arızları dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39b5c-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="39b5c-104">Aşağıdaki senaryoyu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="39b5c-104">Consider the following scenario.</span></span> <span data-ttu-id="39b5c-105">Bir istemci, daha sonra bir arka uç hizmeti çağıran bir aracı için bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="39b5c-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="39b5c-106">Bu hizmetten oluşan herhangi bir hataya türsüz bir hata kabul edilecek şekilde arka uç hizmeti hiç hata sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39b5c-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="39b5c-107">Arka uç hizmeti oluşturur bir <xref:System.ApplicationException> ve WCF hizmet tarafı kanal doğru durdurur.</span><span class="sxs-lookup"><span data-stu-id="39b5c-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="39b5c-108"><xref:System.ApplicationException> Olarak ortaya çıkarır bir <xref:System.ServiceModel.FaultException> aracı için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39b5c-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="39b5c-109">Aracıyı yeniden harekete <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="39b5c-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="39b5c-110">WCF Bu Aracı'ndan türsüz bir hata olarak yorumlar ve istemci açın iletir.</span><span class="sxs-lookup"><span data-stu-id="39b5c-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="39b5c-111">Hata aldıktan sonra hem bir aracı hem de istemci, istemci tarafı kanalları hata.</span><span class="sxs-lookup"><span data-stu-id="39b5c-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="39b5c-112">WCF hata önemli bilmediği Aracı'nın hizmet tarafı kanal ancak açık kalır.</span><span class="sxs-lookup"><span data-stu-id="39b5c-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="39b5c-113">Bu senaryoda en iyi uygulama, önemli bir hizmetten gelen hata ise ve bu nedenle aracı, hizmet tarafı kanal aşağıdaki kod parçacığında gösterildiği gibi hata algılamaktır.</span><span class="sxs-lookup"><span data-stu-id="39b5c-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="39b5c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39b5c-114">See also</span></span>

- [<span data-ttu-id="39b5c-115">WCF Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="39b5c-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)
- [<span data-ttu-id="39b5c-116">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="39b5c-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
