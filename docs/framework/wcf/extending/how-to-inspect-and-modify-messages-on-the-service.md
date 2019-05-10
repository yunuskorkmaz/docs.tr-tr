---
title: 'Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 17ec1d974332b38bed9c00d57bdacba708d0e64f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606356"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="97f11-102">Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="97f11-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="97f11-103">İnceleme veya uygulayarak bir Windows Communication Foundation (WCF) istemcisi gelen veya giden iletileri değiştirme bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> ve hizmet çalışma zamanına ekleme.</span><span class="sxs-lookup"><span data-stu-id="97f11-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="97f11-104">Daha fazla bilgi için [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="97f11-104">For more information, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span> <span data-ttu-id="97f11-105">Hizmette eşdeğer özellik <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97f11-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="97f11-106">İletileri denetleme veya değiştirme için</span><span class="sxs-lookup"><span data-stu-id="97f11-106">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="97f11-107"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="97f11-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="97f11-108">Uygulama bir <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> kolayca hizmet ileti Inspector'ı eklemek istediğiniz kapsama bağlı olarak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="97f11-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="97f11-109">Davranış'ınızı çağrılmadan önce Ekle <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodunda <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97f11-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="97f11-110">Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="97f11-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97f11-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="97f11-111">Example</span></span>  
 <span data-ttu-id="97f11-112">Aşağıdaki kod örnekleri, sırada göster:</span><span class="sxs-lookup"><span data-stu-id="97f11-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="97f11-113">Bir hizmet denetçisi uygulaması.</span><span class="sxs-lookup"><span data-stu-id="97f11-113">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="97f11-114">Inspector ekleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="97f11-114">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="97f11-115">Yükleyen ve davranışını bir hizmet uygulamasında çalışan bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="97f11-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="97f11-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97f11-116">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="97f11-117">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="97f11-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
