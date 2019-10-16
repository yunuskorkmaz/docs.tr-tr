---
title: 'En İyi Uygulamalar: Aracılar'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: a7c037b5942a404b1ff790638979a8e430394151
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320795"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="5c433-102">En İyi Uygulamalar: Aracılar</span><span class="sxs-lookup"><span data-stu-id="5c433-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="5c433-103">Aracı üzerindeki hizmet tarafı kanalların düzgün şekilde kapatıldığından emin olmak için aracıları çağırırken hataları doğru şekilde işlemek için dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c433-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="5c433-104">Aşağıdaki senaryoyu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5c433-104">Consider the following scenario.</span></span> <span data-ttu-id="5c433-105">İstemci bir aracı için çağrı yapar ve ardından arka uç hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="5c433-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="5c433-106">Arka uç hizmeti bir hata sözleşmesi tanımlamıyor, bu nedenle bu hizmetten oluşturulan herhangi bir hata, türsüz bir hata olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5c433-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="5c433-107">Arka uç hizmeti bir @no__t 0 oluşturur ve WCF hizmet tarafı kanalını doğru bir şekilde iptal eder.</span><span class="sxs-lookup"><span data-stu-id="5c433-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="5c433-108">@No__t-0 ' ı, sonra da aracı için oluşturulan <xref:System.ServiceModel.FaultException> olarak yüzeyler.</span><span class="sxs-lookup"><span data-stu-id="5c433-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="5c433-109">Aracı <xref:System.ApplicationException> ' i yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5c433-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="5c433-110">WCF bunu, ara sunucudan yazılı olmayan bir hata olarak yorumlar ve istemciye iletir.</span><span class="sxs-lookup"><span data-stu-id="5c433-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="5c433-111">Hata alındıktan sonra, hem aracı hem de istemci istemci tarafı kanallarını hatası.</span><span class="sxs-lookup"><span data-stu-id="5c433-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="5c433-112">Ara sunucunun hizmet tarafı kanalı açık kalır, çünkü WCF hata önemli olduğunu bilmez.</span><span class="sxs-lookup"><span data-stu-id="5c433-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="5c433-113">Bu senaryodaki en iyi yöntem, hizmetten gelen hatanın önemli olup olmadığını algılamadır ve bu durumda aracı aşağıdaki kod parçacığında gösterildiği gibi hizmet tarafı kanalını hatasına memelidir.</span><span class="sxs-lookup"><span data-stu-id="5c433-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c433-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c433-114">See also</span></span>

- [<span data-ttu-id="5c433-115">WCF Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="5c433-115">WCF Error Handling</span></span>](wcf-error-handling.md)
- [<span data-ttu-id="5c433-116">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="5c433-116">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
