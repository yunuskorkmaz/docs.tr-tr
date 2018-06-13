---
title: 'Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: ec1c60bc2b3e966c576de260dfe3b06a05ab84c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488081"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="2e532-102">Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2e532-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="2e532-103">İnceleme veya uygulayarak bir Windows Communication Foundation (WCF) istemci boyunca gelen veya giden iletiler değiştirme bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> ve hizmet çalışma zamanına ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="2e532-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="2e532-104">Daha fazla bilgi için bkz: [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="2e532-104">For more information, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span> <span data-ttu-id="2e532-105">Hizmette eşdeğer bir özelliktir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e532-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="2e532-106">İletileri incelemek veya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e532-106">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="2e532-107">Uygulama <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2e532-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="2e532-108">Uygulama bir <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> kolayca hizmet ileti denetçisi eklemek istediğiniz kapsam bağlı olarak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2e532-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3.  <span data-ttu-id="2e532-109">Çağrılmadan önce davranış Ekle <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> yöntemi <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e532-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2e532-110">Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="2e532-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e532-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e532-111">Example</span></span>  
 <span data-ttu-id="2e532-112">Aşağıdaki kod örnekleri, sırada göster:</span><span class="sxs-lookup"><span data-stu-id="2e532-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="2e532-113">Bir hizmet denetçisi uygulaması.</span><span class="sxs-lookup"><span data-stu-id="2e532-113">A service inspector implementation.</span></span>  
  
-   <span data-ttu-id="2e532-114">Inspector ekler hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="2e532-114">A service behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="2e532-115">Yükleyen ve davranışı bir hizmet uygulaması çalıştıran bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="2e532-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="2e532-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e532-116">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="2e532-117">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="2e532-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
