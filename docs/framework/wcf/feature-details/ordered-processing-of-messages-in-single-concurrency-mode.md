---
title: Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: baba75fe398d974f989acfda7ef7366986f6813b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598742"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="ab4a3-102">Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi</span><span class="sxs-lookup"><span data-stu-id="ab4a3-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="ab4a3-103">WCF, arka plandaki kanal oturumsuz olmadığı takdirde, iletilerin işlendiği sıra hakkında garanti vermez.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="ab4a3-104">Örneğin, bir oturum kanalı olmayan MsmqInputChannel kullanan bir WCF hizmeti, iletileri sırayla işleyemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="ab4a3-105">Bir geliştiricinin sipariş işleme davranışını tercih edebileceği ancak oturumları kullanmak istemebileceği bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="ab4a3-106">Bu konu, bir hizmet tek bir eşzamanlılık modunda çalışırken bu davranışın nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="ab4a3-107">Sıralı Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="ab4a3-107">In-order Message Processing</span></span>  
 <span data-ttu-id="ab4a3-108">Adlı yeni bir öznitelik <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> eklendi <xref:System.ServiceModel.ServiceBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ab4a3-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="ab4a3-109"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A>True olarak ayarlandığında ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> <xref:System.ServiceModel.ConcurrencyMode.Single> hizmete gönderilen iletilere ayarlandığında, sırayla işlenir.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="ab4a3-110">Aşağıdaki kod parçacığında, bu özniteliklerin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="ab4a3-111"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>Diğer herhangi bir değere ayarlanırsa, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4a3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab4a3-112">See also</span></span>

- [<span data-ttu-id="ab4a3-113">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="ab4a3-113">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="ab4a3-114">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="ab4a3-114">Concurrency</span></span>](../samples/concurrency.md)
