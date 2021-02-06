---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: parametreleri Inceleme veya değiştirme'
title: 'Nasıl yapılır: Parametreleri İnceleme veya Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 90358f2fbd7366b11135ec2ebd044f7864d8a1e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653790"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="625cf-103">Nasıl yapılır: Parametreleri İnceleme veya Değiştirme</span><span class="sxs-lookup"><span data-stu-id="625cf-103">How to: Inspect or Modify Parameters</span></span>

<span data-ttu-id="625cf-104"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>Arabirimi uygulayarak ve istemci ya da hizmet çalışma zamanına ekleyerek bir Windows Communication Foundation (WCF) istemci nesnesi veya WCF hizmetinde tek bir işlem için gelen veya giden iletileri inceleyebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="625cf-104">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="625cf-105">Genellikle bir işlem davranışı, tek bir işlem için parametre Inspector eklemek için kullanılır; diğer davranışlar daha büyük bir kapsamdaki çalışma zamanına kolay erişim sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="625cf-105">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="625cf-106">Daha fazla bilgi için bkz. [Istemcileri genişletme](extending-clients.md) ve [dispatchleri genişletme](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="625cf-106">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="625cf-107">Parametreleri İnceleme veya değiştirme</span><span class="sxs-lookup"><span data-stu-id="625cf-107">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="625cf-108"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="625cf-108">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="625cf-109">Ya da <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> özelliklerine parametre denetçisi eklemek için bir, veya (gerekli kapsama bağlı olarak) uygulayın <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="625cf-109">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="625cf-110">' İ çağırmadan önce davranışını <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya metodunu ekleyin <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="625cf-110">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="625cf-111">Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="625cf-111">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="625cf-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="625cf-112">Example</span></span>  

 <span data-ttu-id="625cf-113">Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="625cf-113">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="625cf-114">Bir parametre denetçisi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="625cf-114">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="625cf-115">, Ve bir kullanarak parametre denetçisini ekleyen davranış uygulamasıdır <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="625cf-115">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="625cf-116">İstemciye parametre denetçisi eklemek için bir istemci uygulamasındaki uç nokta davranışını yükleyen ve çalıştıran bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="625cf-116">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="625cf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="625cf-117">See also</span></span>

- [<span data-ttu-id="625cf-118">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="625cf-118">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
