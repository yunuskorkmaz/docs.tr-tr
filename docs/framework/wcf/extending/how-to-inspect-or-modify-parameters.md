---
title: "Nasıl yapılır: Parametreleri İnceleme veya Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 71e96dc3cf448b2e67b8a039f28a12df8360c76a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="fb985-102">Nasıl yapılır: Parametreleri İnceleme veya Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fb985-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="fb985-103">İnceleme veya tek bir işlem için gelen veya giden iletiler değiştirin bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci nesnesi veya bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulayarak hizmet <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimi ve istemci veya hizmet çalışma zamanına ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="fb985-103">You can inspect or modify the incoming or outgoing messages for a single operation on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client object or a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="fb985-104">Genellikle bir işlemi davranışı, tek bir işlem için parametre denetçiler eklemek için kullanılır; diğer davranışlar çalışma zamanı büyük bir kapsamda kolay erişim sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb985-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="fb985-105">Daha fazla bilgi için bkz: [genişletme istemcileri](../../../../docs/framework/wcf/extending/extending-clients.md) ve [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="fb985-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="fb985-106">İnceleme veya değiştirme parametreleri</span><span class="sxs-lookup"><span data-stu-id="fb985-106">Inspecting or Modifying Parameters</span></span>  
  
1.  <span data-ttu-id="fb985-107">Uygulama <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fb985-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="fb985-108">Uygulama bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (gerekli kapsam bağlı olarak), parametre denetçisi ya da eklemek için <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fb985-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3.  <span data-ttu-id="fb985-109">Çağrılmadan önce davranış Ekle <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> yöntemi <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb985-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fb985-110">Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="fb985-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb985-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb985-111">Example</span></span>  
 <span data-ttu-id="fb985-112">Aşağıdaki kod örnekleri, sırada göster:</span><span class="sxs-lookup"><span data-stu-id="fb985-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="fb985-113">Bir parametre denetçisi uygulaması.</span><span class="sxs-lookup"><span data-stu-id="fb985-113">A parameter inspector implementation.</span></span>  
  
-   <span data-ttu-id="fb985-114">Kullanarak parametre denetçisi ekler davranışı uygulaması bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>ve bir <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb985-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="fb985-115">Yükler ve istemci üzerindeki parametre denetçisi eklemek için bir istemci uygulamasında uç noktası davranışı çalışan bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="fb985-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fb985-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb985-116">See Also</span></span>  
 [<span data-ttu-id="fb985-117">Yapılandırma ve çalışma zamanını davranışlarla genişletme</span><span class="sxs-lookup"><span data-stu-id="fb985-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
