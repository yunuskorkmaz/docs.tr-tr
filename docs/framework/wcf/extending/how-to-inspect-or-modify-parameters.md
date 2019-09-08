---
title: 'Nasıl yapılır: Parametreleri İnceleme veya Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: b4a673f97f06e8d489d9acc85d84e1ecea4656e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795590"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="8734a-102">Nasıl yapılır: Parametreleri İnceleme veya Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8734a-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="8734a-103"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> Arabirimi uygulayarak ve istemci ya da hizmet çalışma zamanına ekleyerek bir Windows Communication Foundation (WCF) istemci nesnesi veya WCF hizmetinde tek bir işlem için gelen veya giden iletileri inceleyebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8734a-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="8734a-104">Genellikle bir işlem davranışı, tek bir işlem için parametre Inspector eklemek için kullanılır; diğer davranışlar daha büyük bir kapsamdaki çalışma zamanına kolay erişim sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8734a-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="8734a-105">Daha fazla bilgi için bkz. [Istemcileri genişletme](extending-clients.md) ve [dispatchleri genişletme](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="8734a-105">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="8734a-106">Parametreleri İnceleme veya değiştirme</span><span class="sxs-lookup"><span data-stu-id="8734a-106">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="8734a-107"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="8734a-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="8734a-108"><xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> Ya <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> da özelliklerine parametre denetçisi eklemek için bir, veya (gerekli kapsama bağlı olarak) uygulayın. <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8734a-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="8734a-109">' <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> İçağırmadan<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> önce davranışını veya metodunu ekleyin. <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8734a-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8734a-110">Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="8734a-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8734a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8734a-111">Example</span></span>  
 <span data-ttu-id="8734a-112">Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8734a-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="8734a-113">Bir parametre denetçisi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8734a-113">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="8734a-114"><xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType> ,<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> Ve<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>bir kullanarak parametre denetçisini ekleyen davranış uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8734a-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="8734a-115">İstemciye parametre denetçisi eklemek için bir istemci uygulamasındaki uç nokta davranışını yükleyen ve çalıştıran bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="8734a-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8734a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8734a-116">See also</span></span>

- [<span data-ttu-id="8734a-117">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="8734a-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
