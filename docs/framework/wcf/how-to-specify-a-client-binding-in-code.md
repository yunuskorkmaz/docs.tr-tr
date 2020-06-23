---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
description: Kodda bir WCF istemci imperatively için bağlamayı belirtmeyi öğrenin. İstemci bu örnekteki bir hizmete erişir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: e5e1dff98121985a598579d83043de838e21e5f1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244510"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="97203-104">Nasıl yapılır: Kodda İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="97203-104">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="97203-105">Bu örnekte, bir Hesaplayıcı hizmeti kullanmak için bir istemci oluşturulur ve bu istemci için bağlama kodda imperatively belirtilir.</span><span class="sxs-lookup"><span data-stu-id="97203-105">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="97203-106">İstemci, `CalculatorService` arabirimini uygulayan öğesine erişir `ICalculator` ve hem hizmet hem de istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="97203-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="97203-107">Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="97203-107">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="97203-108">Hizmeti oluşturma hakkında bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="97203-108">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="97203-109">Ayrıca, istemci bileşenlerini otomatik olarak oluşturmak için [ServiceModel meta veri yardımcı programı aracı 'nı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)WINDOWS COMMUNICATION FOUNDATION (WCF) kullanır.</span><span class="sxs-lookup"><span data-stu-id="97203-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="97203-110">Araç, hizmete erişmek için istemci kodunu üretir.</span><span class="sxs-lookup"><span data-stu-id="97203-110">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="97203-111">İstemci iki bölümde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="97203-111">The client is built in two parts.</span></span> <span data-ttu-id="97203-112">Svcutil.exe, `ClientCalculator` arabirimini uygulayan öğesini oluşturur `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="97203-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="97203-113">Bu istemci uygulaması daha sonra bir örneği `ClientCalculator` oluşturup ardından kodda hizmet için bağlama ve adres belirtilerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97203-113">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="97203-114">Bu örneğin kaynak kopyası için bkz. [BasicBinding](./samples/basicbinding.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="97203-114">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="97203-115">Kodda özel bir bağlama belirtmek için</span><span class="sxs-lookup"><span data-stu-id="97203-115">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="97203-116">Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil.exe kullanın.</span><span class="sxs-lookup"><span data-stu-id="97203-116">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="97203-117">Oluşturulan istemci, `ICalculator` istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="97203-117">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="97203-118">Oluşturulan istemci, uygulamasını da içerir `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="97203-118">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="97203-119">`ClientCalculator`Bir istemci uygulamasında sınıfını kullanan öğesinin bir örneğini oluşturun <xref:System.ServiceModel.BasicHttpBinding> ve ardından belirtilen adresteki hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97203-119">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="97203-120">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="97203-120">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97203-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97203-121">See also</span></span>

- [<span data-ttu-id="97203-122">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="97203-122">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
