---
title: "Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma"
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
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ae688c0f6de534db3e0cdc707bc56301ddb94c8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="ce1a0-102">Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce1a0-102">How to: Create a Service Endpoint in Code</span></span>
<span data-ttu-id="ce1a0-103">Bu örnekte, bir `ICalculator` anlaşma hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıfı ve kendi uç noktası burada belirtilen hizmet kullanmalısınız kodda tanımlanan <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="ce1a0-104">Bağlama ve adres bilgilerini yapılandırma yerine imperatively kod bildirimli olarak belirtmek için genellikle en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="ce1a0-105">Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="ce1a0-106">Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodu dışında yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="ce1a0-107">Kod içinde hizmet uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ce1a0-107">To create a service endpoint in code</span></span>  
  
1.  <span data-ttu-id="ce1a0-108">Hizmet sözleşmesini tanımlayan arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-108">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="ce1a0-109">1. adımda tanımlanan hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-109">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  <span data-ttu-id="ce1a0-110">Barındırma uygulamasında hizmet ve hizmetle birlikte kullanılacak bağlama için taban adresi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-110">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  <span data-ttu-id="ce1a0-111">Ana bilgisayar ve çağrı oluşturma <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> veya ana bilgisayar Hizmeti uç noktası eklemek için diğer aşırı yüklemeler biri.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-111">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="ce1a0-112">Kodda bağlama belirtmek için ancak çalışma zamanı tarafından sağlanan varsayılan uç noktaları kullanmak için Bas adresi oluşturucuya oluştururken geçirmek <xref:System.ServiceModel.ServiceHost>ve çağırmayın <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-112">To specify the binding in code, but to use the default endpoints provided by the runtime, pass the bass address into constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ce1a0-113">Varsayılan uç noktaları için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ce1a0-113"> default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce1a0-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce1a0-114">See Also</span></span>  
 [<span data-ttu-id="ce1a0-115">Nasıl yapılır: kodda hizmet bağlama belirtme</span><span class="sxs-lookup"><span data-stu-id="ce1a0-115">How to: Specify a Service Binding in Code</span></span>](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
