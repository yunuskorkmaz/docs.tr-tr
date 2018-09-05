---
title: "Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma"
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: fd48957f7f8410b4b0df39fe125c35e4fc98cb8e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560301"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="bb2be-102">Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="bb2be-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="bb2be-103">Bu konuda anahatları Windows İşlem Etkinleştirme Hizmetleri (WAS olarak da bilinir) oluşturmak için gereken temel adımlarda barındırılan Windows Communication Foundation (WCF) hizmet.</span><span class="sxs-lookup"><span data-stu-id="bb2be-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="bb2be-104">OLAN HTTP olmayan aktarım kurallarıyla çalışma Internet Information Services (IIS) özellikleri genelleştirilmiş olduğundan yeni işlem Etkinleştirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="bb2be-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="bb2be-105">WCF dinleyici bağdaştırıcı arabirimi gibi TCP ve adlandırılmış kanallar ve Message Queuing, WCF tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletişim kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb2be-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="bb2be-106">WAS etkinleştirme bileşenleri düzgün şekilde yüklenir ve yapılandırılır, ancak uygulamanın bir parçası yazılması için herhangi bir barındırma kod gerektirmeyen bu barındırma seçeneği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bb2be-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="bb2be-107">Yükleme ve WAS'ta yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="bb2be-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bb2be-108">OLUŞTU. web sunucusunun istek işleme ardışık düzeni için Klasik modu olarak ayarlanmışsa etkinleştirme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="bb2be-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="bb2be-109">WAS etkinleştirme kullanılacak ise ardışık düzen işleme, web sunucusu isteği tümleşik moduna ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb2be-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="bb2be-110">WAS içinde barındırılan bir WCF hizmeti, standart bağlamaları normal şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb2be-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="bb2be-111">Ancak, kullanırken <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> WAS barındırılan hizmeti yapılandırmak için bir kısıtlama yerine getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb2be-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="bb2be-112">Farklı uç noktalar aynı taşıma kullandığınızda, aşağıdaki yedi özellikleri eşleştirilecek bağlama ayarları vardır:</span><span class="sxs-lookup"><span data-stu-id="bb2be-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
-   <span data-ttu-id="bb2be-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="bb2be-113">ConnectionBufferSize</span></span>  
  
-   <span data-ttu-id="bb2be-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="bb2be-114">ChannelInitializationTimeout</span></span>  
  
-   <span data-ttu-id="bb2be-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="bb2be-115">MaxPendingConnections</span></span>  
  
-   <span data-ttu-id="bb2be-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="bb2be-116">MaxOutputDelay</span></span>  
  
-   <span data-ttu-id="bb2be-117">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="bb2be-117">MaxPendingAccepts</span></span>  
  
-   <span data-ttu-id="bb2be-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="bb2be-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
-   <span data-ttu-id="bb2be-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="bb2be-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="bb2be-120">Aksi durumda, başlatılmış olan bir uç nokta önce her zaman bu özelliklerin değerlerini belirler ve daha sonra eklenen uç noktaları throw bir <xref:System.ServiceModel.ServiceActivationException> bu ayarları eşleşmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="bb2be-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="bb2be-121">Bu örnekte kaynak kopyası için bkz: [TCP Etkinleştirmesi](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="bb2be-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="bb2be-122">WAS tarafından barındırılan bir temel hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bb2be-122">To create a basic service hosted by WAS</span></span>  
  
1.  <span data-ttu-id="bb2be-123">Hizmet türü için bir hizmet anlaşmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bb2be-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  <span data-ttu-id="bb2be-124">Hizmet sözleşmesi bir hizmet sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bb2be-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="bb2be-125">Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bb2be-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="bb2be-126">Ayrıca, yapılandırma dosyasından bu bilgileri almak için yazılacak kod yok.</span><span class="sxs-lookup"><span data-stu-id="bb2be-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  <span data-ttu-id="bb2be-127">Tanımlamak için bir Web.config dosyası oluşturma <xref:System.ServiceModel.NetTcpBinding> tarafından kullanılacak bağlama `CalculatorService` uç noktaları.</span><span class="sxs-lookup"><span data-stu-id="bb2be-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4.  <span data-ttu-id="bb2be-128">Aşağıdaki kodu içeren bir Service.svc dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bb2be-128">Create a Service.svc file that contains the following code.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  <span data-ttu-id="bb2be-129">IIS sanal dizininde Service.svc dosyası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="bb2be-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="bb2be-130">Hizmeti kullanmak için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bb2be-130">To create a client to use the service</span></span>  
  
1.  <span data-ttu-id="bb2be-131">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.</span><span class="sxs-lookup"><span data-stu-id="bb2be-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="bb2be-132">Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="bb2be-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  <span data-ttu-id="bb2be-133">Oluşturulan istemci uygulaması da uygulamasını içerir `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="bb2be-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="bb2be-134">Adres ve bağlama bilgilerini herhangi bir uygulama hizmetinin içinde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bb2be-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="bb2be-135">Ayrıca, yapılandırma dosyasından bu bilgileri almak için yazılacak kod yok.</span><span class="sxs-lookup"><span data-stu-id="bb2be-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  <span data-ttu-id="bb2be-136">Kullanan istemci yapılandırmasını <xref:System.ServiceModel.NetTcpBinding> svcutil.exe'yi da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bb2be-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="bb2be-137">Bu dosya, Visual Studio kullanırken App.config dosyasında adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb2be-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  <span data-ttu-id="bb2be-138">Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="bb2be-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  <span data-ttu-id="bb2be-139">Derleyin ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bb2be-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2be-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb2be-140">See Also</span></span>  
 [<span data-ttu-id="bb2be-141">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="bb2be-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="bb2be-142">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="bb2be-142">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
