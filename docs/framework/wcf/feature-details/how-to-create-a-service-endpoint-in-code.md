---
title: 'Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 0b51018a5940e01b38b00addb762fa6504495a4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139873"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="7ba2e-102">Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ba2e-102">How to: Create a Service Endpoint in Code</span></span>
<span data-ttu-id="7ba2e-103">Bu örnekte, bir `ICalculator` anlaşma hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıf ve onun uç noktası burada belirtilen hizmetini kullanmalısınız kod içinde tanımlanan <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="7ba2e-104">Yapılandırma yerine kesin kod bağlama ve adres bilgilerini bildirimli olarak belirtmek için genellikle en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="7ba2e-105">Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="7ba2e-106">Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek için bunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="7ba2e-107">Kod içinde hizmet uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ba2e-107">To create a service endpoint in code</span></span>  
  
1.  <span data-ttu-id="7ba2e-108">Hizmet sözleşmesini tanımlayan arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-108">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="7ba2e-109">1. adımda tanımlanan hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-109">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  <span data-ttu-id="7ba2e-110">Barındırma uygulamada, hizmet ve hizmetle birlikte kullanılacak bağlama için temel adresi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-110">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  <span data-ttu-id="7ba2e-111">Konak ve çağrı oluşturma <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> ya da bir ana bilgisayar için hizmet uç noktası eklemek için diğer aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-111">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="7ba2e-112">Kod içinde bağlama belirtilebilir, ancak çalışma zamanı tarafından sağlanan varsayılan uç noktalarını kullanacak şekilde, bas adresi oluşturucuya oluştururken geçirmek <xref:System.ServiceModel.ServiceHost>ve çağırmayın <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-112">To specify the binding in code, but to use the default endpoints provided by the runtime, pass the bass address into constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     <span data-ttu-id="7ba2e-113">Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ba2e-113">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba2e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ba2e-114">See also</span></span>

- [<span data-ttu-id="7ba2e-115">Nasıl yapılır: Kodda Hizmet Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="7ba2e-115">How to: Specify a Service Binding in Code</span></span>](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
