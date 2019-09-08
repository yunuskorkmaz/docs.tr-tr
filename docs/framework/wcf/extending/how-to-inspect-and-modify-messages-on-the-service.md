---
title: 'Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 1356983361c483170d9d7365932b788f2421bf09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795608"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="f3f2c-102">Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f3f2c-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="f3f2c-103">Bir Windows Communication Foundation (WCF) istemcisinde gelen veya giden iletileri, bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> oluşturup hizmet çalışma zamanına ekleyerek inceleyebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="f3f2c-104">Daha fazla bilgi için bkz. [Dispatchleri genişletme](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="f3f2c-104">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="f3f2c-105">Hizmetin eşdeğer özelliği <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="f3f2c-106">İletileri incelemek veya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f3f2c-106">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="f3f2c-107"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="f3f2c-108">Hizmet ileti denetçinizi kolayca <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> eklemek istediğiniz kapsama bağlı olarak <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>,veyaarabiriminiuygulayın <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="f3f2c-109"><xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> Metodu<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>üzerinde çağrılmadan önce davranışınızı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3f2c-110">Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="f3f2c-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f2c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3f2c-111">Example</span></span>  
 <span data-ttu-id="f3f2c-112">Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f3f2c-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="f3f2c-113">Bir hizmet denetçisi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-113">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="f3f2c-114">Inspector 'ı ekleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-114">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="f3f2c-115">Bir hizmet uygulamasında davranışı yükleyen ve çalıştıran bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f3f2c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3f2c-116">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="f3f2c-117">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="f3f2c-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
