---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 81e9b4b5949d3a89749911a30ad199c4f0da300f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091570"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="ded01-102">Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="ded01-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="ded01-103">Bu örnekte, bir hesap makinesi hizmetini kullanması için bir istemci konsol uygulaması oluşturulur ve o istemci için bağlama bildirimli olarak yapılandırmasında belirtilen.</span><span class="sxs-lookup"><span data-stu-id="ded01-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="ded01-104">İstemcisinin eriştiği `CalculatorService`, uygulayan `ICalculator` arabirimi ve hizmet ve Kullan istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ded01-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="ded01-105">Özetlenen yordamı, hesap makinesi hizmetinin çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="ded01-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="ded01-106">Derleme hizmeti hakkında daha fazla bilgi için bkz: [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ded01-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="ded01-107">Ayrıca kullanan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci bileşenlerini otomatik olarak oluşturmak için Windows Communication Foundation (WCF) sağlar.</span><span class="sxs-lookup"><span data-stu-id="ded01-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="ded01-108">Araç istemci kodu ve hizmete erişim yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ded01-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="ded01-109">İstemci, iki parça halinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ded01-109">The client is built in two parts.</span></span> <span data-ttu-id="ded01-110">Svcutil.exe oluşturur `ClientCalculator` uygulayan `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ded01-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="ded01-111">Bu istemci uygulaması, ardından bir örneğini oluşturarak oluşturulur `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="ded01-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="ded01-112">Yapılandırma yerine kesin kod bağlama ve adres bilgilerini bildirimli olarak belirtmek için genellikle en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="ded01-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="ded01-113">Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="ded01-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="ded01-114">Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek için bunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ded01-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="ded01-115">Tüm aşağıdaki yapılandırma adımlarını kullanarak gerçekleştirebileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ded01-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="ded01-116">Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="ded01-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="ded01-117">Bir istemci yapılandırmasında bağlama belirtme</span><span class="sxs-lookup"><span data-stu-id="ded01-117">Specifying a client binding in configuration</span></span>  
  
1.  <span data-ttu-id="ded01-118">Komut satırından hizmet meta verilerinden kod üretmek için Svcutil.exe kullanımı.</span><span class="sxs-lookup"><span data-stu-id="ded01-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="ded01-119">Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ded01-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  <span data-ttu-id="ded01-120">Oluşturulan istemci uygulamasını da içeren `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="ded01-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  <span data-ttu-id="ded01-121">Svcutil.exe ayrıca kullanan istemci yapılandırmasını oluşturur <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ded01-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="ded01-122">Visual Studio kullanarak, bu App.config dosyasının adı. Bağlama bilgileri ve adresi herhangi bir uygulama hizmetinin içinde belirtilmeyen olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ded01-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="ded01-123">Ayrıca, yapılandırma dosyasından bu bilgileri almak için yazılacak kod yok.</span><span class="sxs-lookup"><span data-stu-id="ded01-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  <span data-ttu-id="ded01-124">Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ded01-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  <span data-ttu-id="ded01-125">Derleyin ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ded01-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded01-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ded01-126">See also</span></span>

- [<span data-ttu-id="ded01-127">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ded01-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
