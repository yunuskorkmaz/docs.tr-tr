---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: b16f4b062f7f97a5855b06bdcf348911ee0497d2
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320856"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="70cfb-102">Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="70cfb-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="70cfb-103">Bu örnekte, bir hesap makinesi hizmeti kullanmak için bir istemci konsol uygulaması oluşturulur ve bu istemcinin bağlaması yapılandırmada bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="70cfb-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="70cfb-104">İstemci, `ICalculator` arabirimini uygulayan `CalculatorService`erişir ve hem hizmet hem de istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="70cfb-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="70cfb-105">Özetlenen yordamda, hesap makinesi hizmetinin çalıştığı varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70cfb-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="70cfb-106">Hizmeti oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="70cfb-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="70cfb-107">Ayrıca, istemci bileşenlerini otomatik olarak oluşturmak için Windows Communication Foundation (WCF) tarafından sağlanan [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="70cfb-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="70cfb-108">Araç, hizmete erişmek için istemci kodunu ve yapılandırmasını üretir.</span><span class="sxs-lookup"><span data-stu-id="70cfb-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="70cfb-109">İstemci iki bölümde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="70cfb-109">The client is built in two parts.</span></span> <span data-ttu-id="70cfb-110">Svcutil. exe `ICalculator` arabirimini uygulayan `ClientCalculator` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70cfb-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="70cfb-111">Bu istemci uygulaması daha sonra bir `ClientCalculator`örneği oluşturarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="70cfb-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="70cfb-112">Genellikle, bağlama ve adres bilgilerini, kod içinde imperatively yerine bildirimli olarak yapılandırmaya göre belirlemek en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="70cfb-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="70cfb-113">Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="70cfb-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="70cfb-114">Daha genel olarak, bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="70cfb-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="70cfb-115">[Yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md)kullanarak aşağıdaki yapılandırma adımlarının tümünü gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70cfb-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="70cfb-116">Bu örneğin kaynak kopyası için bkz. [BasicBinding](./samples/basicbinding.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="70cfb-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="70cfb-117">Yapılandırmada İstemci bağlaması belirtme</span><span class="sxs-lookup"><span data-stu-id="70cfb-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="70cfb-118">Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil. exe ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="70cfb-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="70cfb-119">Oluşturulan istemci, istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan `ICalculator` arabirimini içerir.</span><span class="sxs-lookup"><span data-stu-id="70cfb-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="70cfb-120">Oluşturulan istemci Ayrıca `ClientCalculator`uygulamasını da içerir.</span><span class="sxs-lookup"><span data-stu-id="70cfb-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="70cfb-121">Svcutil. exe, <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanan istemcinin yapılandırmasını da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70cfb-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="70cfb-122">Visual Studio 'Yu kullanırken, bu dosyayı App. config olarak adlandırın. Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70cfb-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="70cfb-123">Ayrıca, bu bilgileri yapılandırma dosyasından almak için kodun yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="70cfb-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. <span data-ttu-id="70cfb-124">Bir uygulamada `ClientCalculator` örneği oluşturun ve ardından hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="70cfb-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="70cfb-125">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70cfb-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cfb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70cfb-126">See also</span></span>

- [<span data-ttu-id="70cfb-127">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="70cfb-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
