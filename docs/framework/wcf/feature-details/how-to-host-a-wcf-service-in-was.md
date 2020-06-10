---
title: "Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma"
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 1e338440b3a630840230df838e46579e3725bb60
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593119"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="1396c-102">Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="1396c-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="1396c-103">Bu konuda, Windows Işlem etkinleştirme Hizmetleri (WAS olarak da bilinir) barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1396c-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="1396c-104">, HTTP olmayan taşıma protokolleriyle çalışan Internet Information Services (IIS) özelliklerinin genelleştirilmesi olan yeni işlem etkinleştirme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="1396c-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="1396c-105">WCF, TCP, adlandırılmış kanallar ve Message Queuing gibi WCF tarafından desteklenen HTTP olmayan protokoller üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcısı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1396c-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="1396c-106">Bu barındırma seçeneği, etkinleştirme bileşenlerinin doğru şekilde yüklenip yapılandırılmasını gerektirir, ancak uygulamanın bir parçası olarak herhangi bir barındırma kodunun yazılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="1396c-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="1396c-107">WAS yükleme ve yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF etkinleştirme bileşenlerini yükleme ve yapılandırma](how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="1396c-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1396c-108">Web sunucusunun istek işleme işlem hattı klasik moda ayarlanmışsa etkinleştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1396c-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="1396c-109">WAS etkinleştirme kullanılacaksa Web sunucusunun istek işleme işlem hattının tümleşik moda ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1396c-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="1396c-110">' De bir WCF hizmeti barındırıldığı zaman, standart bağlamalar her zamanki şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1396c-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="1396c-111">Ancak, ve ' ı kullanılarak <xref:System.ServiceModel.NetTcpBinding> <xref:System.ServiceModel.NetNamedPipeBinding> bir barındırılan hizmeti yapılandırmak için, bir kısıtlama karşılanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1396c-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="1396c-112">Farklı uç noktalar aynı aktarımı kullanırken, bağlama ayarlarının aşağıdaki yedi özelliklerde eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="1396c-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="1396c-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="1396c-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="1396c-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="1396c-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="1396c-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="1396c-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="1396c-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="1396c-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="1396c-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="1396c-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="1396c-118">ConnectionPoolSettings. IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="1396c-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="1396c-119">ConnectionPoolSettings. MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="1396c-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="1396c-120">Aksi takdirde, önce başlatılan bitiş noktası bu özelliklerin değerlerini her zaman belirler ve daha sonra eklenen uç noktalar Bu <xref:System.ServiceModel.ServiceActivationException> ayarlarla eşleşmezse bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1396c-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="1396c-121">Bu örneğin kaynak kopyası için bkz. [TCP etkinleştirme](../samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="1396c-121">For the source copy of this example, see [TCP Activation](../samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="1396c-122">Tarafından barındırılan temel bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1396c-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="1396c-123">Hizmet türü için bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1396c-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="1396c-124">Hizmet sözleşmesini bir hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1396c-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="1396c-125">Hizmet uygulamasının içinde adresin veya bağlama bilgilerinin belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1396c-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="1396c-126">Ayrıca, bu bilgileri yapılandırma dosyasından almak için kodun yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1396c-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="1396c-127"><xref:System.ServiceModel.NetTcpBinding>Uç noktalar tarafından kullanılacak bağlamayı tanımlamak için bir Web. config dosyası oluşturun `CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="1396c-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4. <span data-ttu-id="1396c-128">Aşağıdaki kodu içeren bir Service. svc dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1396c-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="1396c-129">Service. svc dosyasını IIS sanal dizininize yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1396c-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="1396c-130">Hizmeti kullanmak üzere bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1396c-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="1396c-131">Hizmet meta verilerinden kod oluşturmak için, komut satırından [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1396c-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="1396c-132">Oluşturulan istemci, `ICalculator` istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="1396c-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="1396c-133">Oluşturulan istemci uygulaması, uygulamasının uygulamasını da içerir `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="1396c-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="1396c-134">Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1396c-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="1396c-135">Ayrıca, bu bilgileri yapılandırma dosyasından almak için kodun yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1396c-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="1396c-136">Tarafından kullanılan istemcinin yapılandırması, <xref:System.ServiceModel.NetTcpBinding> Svcutil. exe tarafından da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1396c-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="1396c-137">Visual Studio kullanılırken bu dosya App. config dosyasında adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1396c-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="1396c-138">Uygulamasının bir örneğini oluşturun `ClientCalculator` ve ardından hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="1396c-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="1396c-139">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1396c-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1396c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1396c-140">See also</span></span>

- [<span data-ttu-id="1396c-141">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1396c-141">TCP Activation</span></span>](../samples/tcp-activation.md)
- <span data-ttu-id="1396c-142">[Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1396c-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
