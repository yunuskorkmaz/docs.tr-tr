---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2441fd7507c5bb368405685598480650114b76a9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="a7467-102">Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="a7467-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="a7467-103">Bu örnekte, bir istemci konsol uygulaması hesaplayıcı hizmetini kullanmak için oluşturulur ve bu istemci için bağlama bildirimli olarak yapılandırma dosyasında belirtilen.</span><span class="sxs-lookup"><span data-stu-id="a7467-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="a7467-104">İstemcisinin eriştiği `CalculatorService`, hangi uygulayan `ICalculator` arabirimi ve hizmet ve Kullan istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a7467-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="a7467-105">Özetlenen yordamı hesap makinesi hizmetinin çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="a7467-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="a7467-106">Hizmet oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a7467-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="a7467-107">Ayrıca kullanır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] istemci bileşenlerini otomatik olarak oluşturmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7467-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] provides to automatically generate the client components.</span></span> <span data-ttu-id="a7467-108">Aracı istemci kodu ve hizmete erişim için yapılandırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7467-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="a7467-109">İstemci iki parça halinde yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="a7467-109">The client is built in two parts.</span></span> <span data-ttu-id="a7467-110">Svcutil.exe oluşturur `ClientCalculator` uygulayan `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a7467-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="a7467-111">Bu istemci uygulaması örneğini oluşturarak sonra oluşturulan `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a7467-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="a7467-112">Bağlama ve adres bilgilerini yapılandırma yerine imperatively kod bildirimli olarak belirtmek için genellikle en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="a7467-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="a7467-113">Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="a7467-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="a7467-114">Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodu dışında yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7467-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="a7467-115">Tüm aşağıdaki yapılandırma adımlarını kullanarak yerine [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a7467-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="a7467-116">Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="a7467-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="a7467-117">Bir istemci yapılandırmasında bağlama belirtme</span><span class="sxs-lookup"><span data-stu-id="a7467-117">Specifying a client binding in configuration</span></span>  
  
1.  <span data-ttu-id="a7467-118">Hizmet meta verilerinden kodu oluşturmak için komut satırından svcutil.exe kullanma.</span><span class="sxs-lookup"><span data-stu-id="a7467-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="a7467-119">Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a7467-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  <span data-ttu-id="a7467-120">Oluşturulan istemci uygulamasını da içerir `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a7467-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  <span data-ttu-id="a7467-121">Svcutil.exe ayrıca kullanan istemci yapılandırması oluşturur <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a7467-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="a7467-122">Visual Studio kullanırken, bu App.config dosyasının adı. Adres ve bağlama bilgileri herhangi bir yere hizmet uygulaması içinde belirtilmedi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a7467-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="a7467-123">Ayrıca, bu bilgileri yapılandırma dosyasından almak için yazılacak kodu yok.</span><span class="sxs-lookup"><span data-stu-id="a7467-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  <span data-ttu-id="a7467-124">Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="a7467-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  <span data-ttu-id="a7467-125">Derleme ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a7467-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7467-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7467-126">See Also</span></span>  
 [<span data-ttu-id="a7467-127">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a7467-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
