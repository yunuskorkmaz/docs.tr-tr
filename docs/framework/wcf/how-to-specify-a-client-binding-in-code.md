---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990230"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="75d9c-102">Nasıl yapılır: Kodda İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="75d9c-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="75d9c-103">Bu örnekte, bir Hesaplayıcı hizmeti kullanmak için bir istemci oluşturulur ve bu istemci için bağlama kodda imperatively belirtilir.</span><span class="sxs-lookup"><span data-stu-id="75d9c-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="75d9c-104">İstemci, `ICalculator` arabirimini uygulayan `CalculatorService`öğesine erişir ve hem hizmet <xref:System.ServiceModel.BasicHttpBinding> hem de istemci sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="75d9c-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="75d9c-105">Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="75d9c-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="75d9c-106">Hizmeti oluşturma hakkında bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin.</span><span class="sxs-lookup"><span data-stu-id="75d9c-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="75d9c-107">Ayrıca, istemci bileşenlerini otomatik olarak oluşturmak için [ServiceModel meta veri yardımcı programı aracı 'nı (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)WINDOWS COMMUNICATION FOUNDATION (WCF) kullanır.</span><span class="sxs-lookup"><span data-stu-id="75d9c-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="75d9c-108">Araç, hizmete erişmek için istemci kodunu üretir.</span><span class="sxs-lookup"><span data-stu-id="75d9c-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="75d9c-109">İstemci iki bölümde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="75d9c-109">The client is built in two parts.</span></span> <span data-ttu-id="75d9c-110">Svcutil. exe, `ClientCalculator` `ICalculator` arabirimini uygulayan öğesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75d9c-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="75d9c-111">Bu istemci uygulaması daha sonra bir örneği `ClientCalculator` oluşturup ardından kodda hizmet için bağlama ve adres belirtilerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="75d9c-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="75d9c-112">Bu örneğin kaynak kopyası için bkz. [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="75d9c-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="75d9c-113">Kodda özel bir bağlama belirtmek için</span><span class="sxs-lookup"><span data-stu-id="75d9c-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="75d9c-114">Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil. exe ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="75d9c-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="75d9c-115">Oluşturulan istemci, istemci uygulamasının karşılaması gereken `ICalculator` hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="75d9c-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="75d9c-116">Oluşturulan istemci, `ClientCalculator`uygulamasını da içerir.</span><span class="sxs-lookup"><span data-stu-id="75d9c-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="75d9c-117">Bir istemci uygulamasında <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanan `ClientCalculator` öğesinin bir örneğini oluşturun ve ardından belirtilen adresteki hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="75d9c-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="75d9c-118">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75d9c-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d9c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75d9c-119">See also</span></span>

- [<span data-ttu-id="75d9c-120">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="75d9c-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
