---
title: Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: bbbc1f62931abda438c3d06b514518b1199b649e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493926"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="d9b12-102">Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi</span><span class="sxs-lookup"><span data-stu-id="d9b12-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="d9b12-103">Temel alınan kanal süre sonuyla olmadığı sürece WCF garanti iletileri işlenme, sipariş hakkında yapar.</span><span class="sxs-lookup"><span data-stu-id="d9b12-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="d9b12-104">Örneğin, bir süre sonuyla kanal değil, MsmqInputChannel kullanan bir WCF hizmeti işlem iletileri sırasına başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d9b12-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="d9b12-105">Bir geliştirici nerede ancak içinde sipariş davranış işleme istediğiniz oturumları kullanmak istemiyor bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="d9b12-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="d9b12-106">Bu konuda, bir hizmet tek eşzamanlılık modunda çalışırken bu davranışı yapılandırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="d9b12-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="d9b12-107">Düzen dışı ileti işleme</span><span class="sxs-lookup"><span data-stu-id="d9b12-107">In-order Message Processing</span></span>  
 <span data-ttu-id="d9b12-108">Yeni bir öznitelik adı verilen <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> eklendi <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d9b12-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="d9b12-109">Zaman <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> ayarlanmış true ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ayarlanır <xref:System.ServiceModel.ConcurrencyMode.Single> sırada hizmete gönderilen iletileri işlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="d9b12-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="d9b12-110">Aşağıdaki kod parçacığını nasıl bu öznitelikler ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9b12-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="d9b12-111">Varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> başka herhangi bir değer için ayarlanmış bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d9b12-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b12-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b12-112">See Also</span></span>  
 [<span data-ttu-id="d9b12-113">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="d9b12-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="d9b12-114">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="d9b12-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
