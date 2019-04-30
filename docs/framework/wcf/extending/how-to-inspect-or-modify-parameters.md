---
title: 'Nasıl yapılır: Parametreleri İnceleme veya Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 2e294b7970a58fad9385802470a514e5a9240495
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766870"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="c3078-102">Nasıl yapılır: Parametreleri İnceleme veya Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c3078-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="c3078-103">İnceleme veya gelen veya giden iletiler için bir Windows Communication Foundation (WCF) istemci nesnesi veya bir WCF hizmetini sunucuda tek bir işlem uygulayarak değiştirme <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimi ve istemci veya hizmet çalışma zamanına ekleme.</span><span class="sxs-lookup"><span data-stu-id="c3078-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="c3078-104">Genellikle işlem davranışı, tek bir işlem için parametre denetçiler eklemek için kullanılır; diğer davranışlar çalışma zamanı büyük bir kapsamda kolay erişim sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3078-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="c3078-105">Daha fazla bilgi için [genişletme istemciler](../../../../docs/framework/wcf/extending/extending-clients.md) ve [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="c3078-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="c3078-106">İnceleme veya değiştirme parametreleri</span><span class="sxs-lookup"><span data-stu-id="c3078-106">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="c3078-107"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3078-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="c3078-108">Uygulama bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (gerekli kapsamın bağlı olarak), parametre denetçisi eklenecek <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="c3078-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="c3078-109">Davranış'ınızı çağrılmadan önce Ekle <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodunda <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3078-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c3078-110">Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c3078-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3078-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3078-111">Example</span></span>  
 <span data-ttu-id="c3078-112">Aşağıdaki kod örnekleri, sırada göster:</span><span class="sxs-lookup"><span data-stu-id="c3078-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="c3078-113">Bir parametre denetçisi uygulaması.</span><span class="sxs-lookup"><span data-stu-id="c3078-113">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="c3078-114">Parametre Inspector'ı kullanarak ekler davranışını uygulama bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>ve bir <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3078-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="c3078-115">Yükleyen ve istemci üzerinde parametresi Inspector'ı eklemek için bir istemci uygulaması, uç nokta davranışı çalışır bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="c3078-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c3078-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3078-116">See also</span></span>

- [<span data-ttu-id="c3078-117">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="c3078-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
