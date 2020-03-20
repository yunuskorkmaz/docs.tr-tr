---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184051"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="9b798-102">Nasıl yapılır: Kodda İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="9b798-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="9b798-103">Bu örnekte, bir hesap makinesi hizmeti kullanmak için bir istemci oluşturulur ve bu istemci için bağlama zorunlu olarak kod olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9b798-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="9b798-104">`CalculatorService`İstemci, `ICalculator` arabirimi uygulayan , hizmete ve istemciye erişir <xref:System.ServiceModel.BasicHttpBinding> ve sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b798-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="9b798-105">Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="9b798-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="9b798-106">Hizmet oluşturma hakkında daha fazla bilgi için [bkz: Yapılandırmada Bir Hizmet Bağlama belirtin.](how-to-specify-a-service-binding-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9b798-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="9b798-107">Ayrıca [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) istemci bileşenlerini otomatik olarak oluşturmak için sağlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b798-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="9b798-108">Araç, hizmete erişmek için istemci kodunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b798-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="9b798-109">İstemci iki bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="9b798-109">The client is built in two parts.</span></span> <span data-ttu-id="9b798-110">Svcutil.exe `ICalculator` arayüzü `ClientCalculator` uygular oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b798-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="9b798-111">Bu istemci uygulaması daha sonra bir `ClientCalculator` örnek oluşturarak ve daha sonra kod içinde hizmet için bağlama ve adres belirterek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9b798-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="9b798-112">Bu örneğin kaynak kopyası için [Temel Bağlama](./samples/basicbinding.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="9b798-112">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="9b798-113">Kodda özel bir bağlama belirtmek için</span><span class="sxs-lookup"><span data-stu-id="9b798-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="9b798-114">Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil.exe'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9b798-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="9b798-115">Oluşturulan istemci, istemci `ICalculator` uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="9b798-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="9b798-116">Oluşturulan istemci de uygulanmasını `ClientCalculator`içerir.</span><span class="sxs-lookup"><span data-stu-id="9b798-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="9b798-117">İstemci uygulamasında `ClientCalculator` <xref:System.ServiceModel.BasicHttpBinding> sınıfı kullananların bir örneğini oluşturun ve ardından belirtilen adresteki servis işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9b798-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="9b798-118">İstemciyi derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="9b798-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b798-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b798-119">See also</span></span>

- [<span data-ttu-id="9b798-120">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9b798-120">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
