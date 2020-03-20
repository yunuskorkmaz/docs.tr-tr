---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184044"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="96647-102">Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="96647-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="96647-103">Bu örnekte, bir hesap makinesi hizmeti kullanmak için bir istemci konsoluygulaması oluşturulur ve bu istemci için bağlama yapılandırmada bildirimsel olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="96647-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="96647-104">`CalculatorService`İstemci, `ICalculator` arabirimi uygulayan , hizmete ve istemciye erişir <xref:System.ServiceModel.BasicHttpBinding> ve sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="96647-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="96647-105">Özetlenen yordam, hesap makinesi hizmetinin çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="96647-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="96647-106">Hizmetin nasıl oluşturulabildiğini öğrenmek için [bkz.](how-to-specify-a-service-binding-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="96647-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="96647-107">Ayrıca, Windows Communication Foundation'ın (WCF) istemci bileşenlerini otomatik olarak oluşturmak için sağladığı [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="96647-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="96647-108">Araç, hizmete erişmek için istemci kodu ve yapılandırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96647-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="96647-109">İstemci iki bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="96647-109">The client is built in two parts.</span></span> <span data-ttu-id="96647-110">Svcutil.exe `ICalculator` arayüzü `ClientCalculator` uygular oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96647-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="96647-111">Bu istemci uygulaması daha sonra bir `ClientCalculator`örnek oluşturarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="96647-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="96647-112">Bağlayıcı ve adres bilgilerini zorunlu olarak kodda değil, yapılandırmada bildirimsel olarak belirtmek genellikle en iyi yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="96647-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="96647-113">Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirilirken kullanılanlardan farklı olduğundan, koddaki uç noktaları tanımlamak genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="96647-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="96647-114">Daha genel olarak, bağlama ve adresleme bilgilerini kodun dışında tutmak, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değişmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="96647-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="96647-115">[Yapılandırma Düzenleyicisi Aracını (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)kullanarak aşağıdaki yapılandırma adımlarının tümlerini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96647-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="96647-116">Bu örneğin kaynak kopyası için [Temel Bağlama](./samples/basicbinding.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="96647-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="96647-117">Yapılandırmada istemci bağlama belirtme</span><span class="sxs-lookup"><span data-stu-id="96647-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="96647-118">Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil.exe'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="96647-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="96647-119">Oluşturulan istemci, istemci `ICalculator` uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="96647-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="96647-120">Oluşturulan istemci de uygulanmasını `ClientCalculator`içerir.</span><span class="sxs-lookup"><span data-stu-id="96647-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="96647-121">Svcutil.exe ayrıca <xref:System.ServiceModel.BasicHttpBinding> sınıfı kullanan istemci için yapılandırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96647-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="96647-122">Visual Studio'yu kullanırken bu dosyayı App.config olarak adlandırın. Adres ve bağlama bilgilerinin hizmetin uygulanması nın herhangi bir yerinde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="96647-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="96647-123">Ayrıca, yapılandırma dosyasından bu bilgileri almak için kod yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="96647-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="96647-124">Bir uygulamadaki `ClientCalculator` nin bir örneğini oluşturun ve ardından servis işlemlerini arayın.</span><span class="sxs-lookup"><span data-stu-id="96647-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="96647-125">İstemciyi derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="96647-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96647-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96647-126">See also</span></span>

- [<span data-ttu-id="96647-127">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="96647-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
