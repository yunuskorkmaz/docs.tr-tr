---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
description: Bir yapılandırma dosyasında bir WCF istemcisi için bağlamayı bildirimli olarak belirtmeyi öğrenin. İstemci bu örnekteki bir hizmete erişir.
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 28778b6ae853199c5d7943f329bb087760f4bb11
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244497"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="226cf-104">Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="226cf-104">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="226cf-105">Bu örnekte, bir hesap makinesi hizmeti kullanmak için bir istemci konsol uygulaması oluşturulur ve bu istemcinin bağlaması yapılandırmada bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="226cf-105">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="226cf-106">İstemci, `CalculatorService` arabirimini uygulayan öğesine erişir `ICalculator` ve hem hizmet hem de istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="226cf-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="226cf-107">Özetlenen yordamda, hesap makinesi hizmetinin çalıştığı varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="226cf-107">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="226cf-108">Hizmeti oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="226cf-108">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="226cf-109">Ayrıca, istemci bileşenlerini otomatik olarak oluşturmak için Windows Communication Foundation (WCF) tarafından sağlanan [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="226cf-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="226cf-110">Araç, hizmete erişmek için istemci kodunu ve yapılandırmasını üretir.</span><span class="sxs-lookup"><span data-stu-id="226cf-110">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="226cf-111">İstemci iki bölümde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="226cf-111">The client is built in two parts.</span></span> <span data-ttu-id="226cf-112">Svcutil.exe, `ClientCalculator` arabirimini uygulayan öğesini oluşturur `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="226cf-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="226cf-113">Bu istemci uygulaması daha sonra bir örneği oluşturarak oluşturulur `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="226cf-113">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="226cf-114">Genellikle, bağlama ve adres bilgilerini, kod içinde imperatively yerine bildirimli olarak yapılandırmaya göre belirlemek en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="226cf-114">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="226cf-115">Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="226cf-115">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="226cf-116">Daha genel olarak, bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="226cf-116">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="226cf-117">[Yapılandırma Düzenleyicisi aracını (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)kullanarak aşağıdaki yapılandırma adımlarının tümünü gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="226cf-117">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="226cf-118">Bu örneğin kaynak kopyası için bkz. [BasicBinding](./samples/basicbinding.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="226cf-118">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="226cf-119">Yapılandırmada İstemci bağlaması belirtme</span><span class="sxs-lookup"><span data-stu-id="226cf-119">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="226cf-120">Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil.exe kullanın.</span><span class="sxs-lookup"><span data-stu-id="226cf-120">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="226cf-121">Oluşturulan istemci, `ICalculator` istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="226cf-121">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="226cf-122">Oluşturulan istemci, uygulamasını da içerir `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="226cf-122">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="226cf-123">Svcutil.exe Ayrıca, sınıfını kullanan istemcinin yapılandırmasını da oluşturur <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="226cf-123">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="226cf-124">Visual Studio 'Yu kullanırken, bu dosyanın adını App.config. Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="226cf-124">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="226cf-125">Ayrıca, bu bilgileri yapılandırma dosyasından almak için kodun yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="226cf-125">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="226cf-126">Uygulamasının bir örneğini oluşturun `ClientCalculator` ve ardından hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="226cf-126">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="226cf-127">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="226cf-127">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226cf-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="226cf-128">See also</span></span>

- [<span data-ttu-id="226cf-129">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="226cf-129">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
