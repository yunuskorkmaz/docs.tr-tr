---
title: 'Nasıl yapılır: Kodda Hizmet Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 9f3320b031141246a394191a1924509204707dc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928810"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="b73d3-102">Nasıl yapılır: Kodda Hizmet Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="b73d3-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="b73d3-103">Bu örnekte, bir `ICalculator` anlaşma hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıf ve onun uç noktası burada belirtilen hizmetini kullanmalısınız kod içinde tanımlanan <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b73d3-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="b73d3-104">Yapılandırma yerine kesin kod bağlama ve adres bilgilerini bildirimli olarak belirtmek için genellikle en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b73d3-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="b73d3-105">Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="b73d3-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="b73d3-106">Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek için bunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b73d3-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="b73d3-107">Kod yerine yapılandırma öğelerini kullanarak bu hizmeti yapılandırmak nasıl bir açıklaması için bkz. [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b73d3-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="b73d3-108">BasicHttpBinding hizmet için kullanılacak kodu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="b73d3-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="b73d3-109">Hizmet türü için bir hizmet anlaşmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b73d3-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="b73d3-110">Hizmet sözleşmesi bir hizmet sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b73d3-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="b73d3-111">Barındırma uygulamada, hizmet ve hizmetle birlikte kullanılacak bağlamanın temel adresi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b73d3-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="b73d3-112">Konak hizmeti oluşturun, uç nokta ekleyin ve ardından ana bilgisayar'ı açın.</span><span class="sxs-lookup"><span data-stu-id="b73d3-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="b73d3-113">Bağlama özelliklerin varsayılan değerlerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="b73d3-113">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="b73d3-114">Varsayılan özellik değerlerini birini değiştirmek için <xref:System.ServiceModel.BasicHttpBinding> sınıfı, ana bilgisayar oluşturmadan önce yeni değere bağlama üzerinde özellik değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b73d3-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="b73d3-115">Örneğin, 2 dakika 1 dakikalık varsayılan açık ve kapalı zaman aşımı değerlerini değiştirmek için aşağıdakileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="b73d3-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b73d3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b73d3-116">See also</span></span>

- [<span data-ttu-id="b73d3-117">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b73d3-117">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b73d3-118">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="b73d3-118">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
