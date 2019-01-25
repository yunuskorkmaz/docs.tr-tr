---
title: Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: c9f2460a1def19212d3ba866b0b443830e9b69bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745859"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="ed87a-102">Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi</span><span class="sxs-lookup"><span data-stu-id="ed87a-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="ed87a-103">Arka plandaki kanal kapatamaması olmadığı sürece, WCF iletileri işlenme, sipariş tutarlılık garantisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed87a-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="ed87a-104">Örneğin, bir oturum kanalı olmayan MsmqInputChannel kullanan bir WCF hizmet sırası iletileri işlemek başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ed87a-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="ed87a-105">Bir geliştirici burada ancak içinde sipariş davranışı işleme istediğiniz oturumları kullanmak istemiyor bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="ed87a-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="ed87a-106">Bu konu, bir hizmet, tek bir eşzamanlılık modunda çalışırken bu davranışı yapılandırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="ed87a-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="ed87a-107">Sıralı ileti işleme</span><span class="sxs-lookup"><span data-stu-id="ed87a-107">In-order Message Processing</span></span>  
 <span data-ttu-id="ed87a-108">Olarak adlandırılan yeni bir öznitelik <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> eklendi <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ed87a-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="ed87a-109">Zaman <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> ayarlanır true ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ayarlanır <xref:System.ServiceModel.ConcurrencyMode.Single> sırada gönderilen iletileri işlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="ed87a-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="ed87a-110">Aşağıdaki kod parçacığını bu öznitelikler kümesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed87a-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="ed87a-111">Varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> başka herhangi bir değer için ayarlanmış bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ed87a-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed87a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed87a-112">See also</span></span>
- [<span data-ttu-id="ed87a-113">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="ed87a-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="ed87a-114">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="ed87a-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
