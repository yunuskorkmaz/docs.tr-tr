---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: hizmette Iletileri Inceleme ve değiştirme'
title: 'Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 5fd3a5e49bdd35a3095e5855b399533337e133a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668883"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="651e9-103">Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="651e9-103">How to: Inspect and Modify Messages on the Service</span></span>

<span data-ttu-id="651e9-104">Bir Windows Communication Foundation (WCF) istemcisinde gelen veya giden iletileri, bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> oluşturup hizmet çalışma zamanına ekleyerek inceleyebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="651e9-104">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="651e9-105">Daha fazla bilgi için bkz. [Dispatchleri genişletme](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="651e9-105">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="651e9-106">Hizmetin eşdeğer özelliği <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="651e9-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="651e9-107">İletileri incelemek veya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="651e9-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="651e9-108"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="651e9-108">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="651e9-109"><xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> Hizmet ileti denetçinizi kolayca eklemek istediğiniz kapsama bağlı olarak, veya arabirimini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="651e9-109">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="651e9-110">Metodu üzerinde çağrılmadan önce davranışınızı ekleyin <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="651e9-110">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="651e9-111">Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="651e9-111">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="651e9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="651e9-112">Example</span></span>  

 <span data-ttu-id="651e9-113">Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="651e9-113">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="651e9-114">Bir hizmet denetçisi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="651e9-114">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="651e9-115">Inspector 'ı ekleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="651e9-115">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="651e9-116">Bir hizmet uygulamasında davranışı yükleyen ve çalıştıran bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="651e9-116">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="651e9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="651e9-117">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="651e9-118">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="651e9-118">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
