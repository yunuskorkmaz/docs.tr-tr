---
title: "Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma"
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184908"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="4b427-102">Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="4b427-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="4b427-103">Bu konu, Windows Process Etkinleştirme Hizmetleri (WAS olarak da bilinir) windows communication foundation (WCF) hizmeti barındırılan oluşturmak için gereken temel adımları özetler.</span><span class="sxs-lookup"><span data-stu-id="4b427-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="4b427-104">WAS, HTTP dışı aktarım protokolleriyle çalışan Internet Bilgi Hizmetleri (IIS) özelliklerinin genelleştirilmesi olan yeni işlem etkinleştirme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="4b427-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="4b427-105">WCF, TCP, adlandırılmış borular ve İleti Sıralama gibi WCF tarafından desteklenen HTTP dışı protokoller üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcıarabını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b427-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="4b427-106">Bu barındırma seçeneği, WAS etkinleştirme bileşenlerinin düzgün şekilde yüklenmesini ve yapılandırılmasını gerektirir, ancak uygulamanın bir parçası olarak herhangi bir barındırma kodunun yazılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4b427-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="4b427-107">WAS'ı yükleme ve yapılandırma hakkında daha fazla bilgi için [bkz: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)</span><span class="sxs-lookup"><span data-stu-id="4b427-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4b427-108">Web sunucusunun istek işleme ardışık adı Klasik modda ayarlanmışsa WAS etkinleştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4b427-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="4b427-109">WAS etkinleştirme kullanılacaksa, web sunucusunun istek işleme ardışık adı Tümleşik moduna ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b427-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="4b427-110">Bir WCF hizmeti WAS'da barındırıldığında, standart bağlamalar her zamanki gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b427-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="4b427-111">Ancak, WAS <xref:System.ServiceModel.NetTcpBinding> barındırılan bir hizmeti <xref:System.ServiceModel.NetNamedPipeBinding> yapılandırmak ve yapılandırmak için kullanırken, bir kısıtlamanın karşılanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b427-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="4b427-112">Farklı uç noktalar aynı aktarımı kullandığında, bağlama ayarlarıaşağıdaki yedi özellikte eşleşir:</span><span class="sxs-lookup"><span data-stu-id="4b427-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="4b427-113">BağlantıBufferSize</span><span class="sxs-lookup"><span data-stu-id="4b427-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="4b427-114">KanalInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="4b427-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="4b427-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="4b427-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="4b427-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="4b427-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="4b427-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="4b427-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="4b427-118">BağlantıPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="4b427-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="4b427-119">BağlantıPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="4b427-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="4b427-120">Aksi takdirde, ilk olarak başlatılır bitiş noktası her zaman bu özelliklerin <xref:System.ServiceModel.ServiceActivationException> değerlerini belirler ve daha sonra eklenen uç noktaları bu ayarlarla eşleşmiyorsa bir atımı yapar.</span><span class="sxs-lookup"><span data-stu-id="4b427-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="4b427-121">Bu örneğin kaynak kopyası için [TCP Etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4b427-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="4b427-122">WAS tarafından barındırılan temel bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4b427-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="4b427-123">Hizmet türü için bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4b427-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="4b427-124">Hizmet sözleşmesini bir hizmet sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4b427-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="4b427-125">Hizmetin uygulanması içinde adres veya bağlama bilgilerinin belirtilmedigini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4b427-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="4b427-126">Ayrıca, yapılandırma dosyasından bu bilgileri almak için kod yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4b427-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="4b427-127">Uç noktalartarafından kullanılacak bağlamayı <xref:System.ServiceModel.NetTcpBinding> tanımlamak için bir Web.config dosyası oluşturun. `CalculatorService`</span><span class="sxs-lookup"><span data-stu-id="4b427-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="4b427-128">Aşağıdaki kodu içeren bir Service.svc dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4b427-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="4b427-129">Service.svc dosyasını IIS sanal dizininize yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="4b427-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="4b427-130">Hizmeti kullanmak için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4b427-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="4b427-131">Hizmet meta verilerinden kod oluşturmak için komut satırından [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b427-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="4b427-132">Oluşturulan istemci, istemci `ICalculator` uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b427-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="4b427-133">Oluşturulan istemci uygulaması da uygulanmasını `ClientCalculator`içerir.</span><span class="sxs-lookup"><span data-stu-id="4b427-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="4b427-134">Adres ve bağlama bilgilerinin hizmetin uygulanması nın herhangi bir yerinde belirtilmemiş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4b427-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="4b427-135">Ayrıca, yapılandırma dosyasından bu bilgileri almak için kod yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4b427-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="4b427-136">Kullanan istemci <xref:System.ServiceModel.NetTcpBinding> için yapılandırma da Svcutil.exe tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4b427-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="4b427-137">Visual Studio'yu kullanırken bu dosya App.config dosyasında adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b427-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="4b427-138">Bir uygulamadaki `ClientCalculator` nin bir örneğini oluşturun ve ardından servis işlemlerini arayın.</span><span class="sxs-lookup"><span data-stu-id="4b427-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="4b427-139">İstemciyi derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="4b427-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b427-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b427-140">See also</span></span>

- [<span data-ttu-id="4b427-141">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4b427-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- <span data-ttu-id="4b427-142">[Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4b427-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
