---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 3a05c60b6e68f87c31e74774bf0b50e535477b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498377"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="96ef5-102">Nasıl yapılır: Kodda İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="96ef5-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="96ef5-103">Bu örnekte, bir istemci bir hesap makinesi hizmeti kullanacak şekilde oluşturulur ve istemci için bağlama imperatively kodda belirtilir.</span><span class="sxs-lookup"><span data-stu-id="96ef5-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="96ef5-104">İstemcisinin eriştiği `CalculatorService`, hangi uygulayan `ICalculator` arabirimi ve hizmet ve Kullan istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="96ef5-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="96ef5-105">Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="96ef5-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="96ef5-106">Hizmet oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="96ef5-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="96ef5-107">Ayrıca kullanır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)istemci bileşenlerini otomatik olarak oluşturmak için Windows Communication Foundation (WCF) sağlar.</span><span class="sxs-lookup"><span data-stu-id="96ef5-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="96ef5-108">Aracı hizmete erişim için istemci kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96ef5-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="96ef5-109">İstemci iki parça halinde yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="96ef5-109">The client is built in two parts.</span></span> <span data-ttu-id="96ef5-110">Svcutil.exe oluşturur `ClientCalculator` uygulayan `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="96ef5-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="96ef5-111">Bu istemci uygulaması örneğini oluşturarak sonra oluşturulan `ClientCalculator` ve ardından kodda bağlama ve hizmet adresini belirtme.</span><span class="sxs-lookup"><span data-stu-id="96ef5-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="96ef5-112">Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="96ef5-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="96ef5-113">Özel bağlama kodda belirtmek için</span><span class="sxs-lookup"><span data-stu-id="96ef5-113">To specify a custom binding in code</span></span>  
  
1.  <span data-ttu-id="96ef5-114">Hizmet meta verilerinden kodu oluşturmak için komut satırından svcutil.exe kullanma.</span><span class="sxs-lookup"><span data-stu-id="96ef5-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="96ef5-115">Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="96ef5-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  <span data-ttu-id="96ef5-116">Oluşturulan istemci uygulamasını da içerir `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="96ef5-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  <span data-ttu-id="96ef5-117">Bir örneğini oluşturmak `ClientCalculator` kullanan <xref:System.ServiceModel.BasicHttpBinding> sınıfı bir istemci uygulaması ve hizmet işlemleri belirtilen adresinde çağırın.</span><span class="sxs-lookup"><span data-stu-id="96ef5-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  <span data-ttu-id="96ef5-118">Derleme ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96ef5-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ef5-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96ef5-119">See Also</span></span>  
 [<span data-ttu-id="96ef5-120">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="96ef5-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
