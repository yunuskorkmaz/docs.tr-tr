---
title: "Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bfa798bf2f2c758905512df32e03214634b6c2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="7223e-102">Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="7223e-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="7223e-103">Bir Windows İşlem Etkinleştirme barındırılan Hizmetleri'nı (WAS olarak da bilinir) oluşturmak için gereken temel adımlarda bu konuda özetlenir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="7223e-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="7223e-104">EDİLDİ Genelleştirme HTTP olmayan aktarım protokolleri ile iş Internet Information Services (IIS) özellikleri olan yeni işlem Etkinleştirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="7223e-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7223e-105">Dinleyici Bağdaştırıcısı arabirimi tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletişim kurmak için kullandığı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]TCP, Adlandırılmış Kanallar ve Message Queuing gibi.</span><span class="sxs-lookup"><span data-stu-id="7223e-105"> uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="7223e-106">Bu barındırma seçeneği WAS etkinleştirme bileşenleri düzgün bir şekilde yüklenir ve yapılandırılır, ancak uygulamanın bir parçası yazılması için herhangi bir barındırma kod gerektirmeyen gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7223e-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7223e-107">Yükleme ve WAS yapılandırma Bkz [nasıl yapılır: yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="7223e-107"> installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="7223e-108">Web sunucunuzun istek işleme ardışık Klasik moda ayarladıysanız etkinleştirme desteklenmeyen OLUŞTU.</span><span class="sxs-lookup"><span data-stu-id="7223e-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="7223e-109">WAS etkinleştirme kullanılacak ise web sunucusunun istek işleme ardışık tümleşik moduna ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7223e-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="7223e-110">Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WAS içinde barındırılan hizmetin, standart bağlamaları normal şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7223e-110">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="7223e-111">Ancak, kullanırken <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> WAS barındırılan hizmeti yapılandırmak için bir kısıtlama yerine getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7223e-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="7223e-112">Farklı uç noktalar aynı aktarım kullandığınızda, aşağıdaki yedi özellikleri eşleştirilecek bağlama ayarları vardır:</span><span class="sxs-lookup"><span data-stu-id="7223e-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
-   <span data-ttu-id="7223e-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="7223e-113">ConnectionBufferSize</span></span>  
  
-   <span data-ttu-id="7223e-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="7223e-114">ChannelInitializationTimeout</span></span>  
  
-   <span data-ttu-id="7223e-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="7223e-115">MaxPendingConnections</span></span>  
  
-   <span data-ttu-id="7223e-116">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="7223e-116">MaxOutputDelay</span></span>  
  
-   <span data-ttu-id="7223e-117">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="7223e-117">MaxPendingAccepts</span></span>  
  
-   <span data-ttu-id="7223e-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="7223e-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
-   <span data-ttu-id="7223e-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="7223e-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="7223e-120">Aksi takdirde başlatılmış uç nokta önce her zaman bu özelliklerin değerlerini belirler ve daha sonra eklenen uç noktaları throw bir <xref:System.ServiceModel.ServiceActivationException> bu ayarları eşleşmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="7223e-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="7223e-121">Bu örnekte kaynak kopyası için bkz: [TCP etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="7223e-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="7223e-122">WAS tarafından barındırılan temel bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7223e-122">To create a basic service hosted by WAS</span></span>  
  
1.  <span data-ttu-id="7223e-123">Hizmet türü için bir hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="7223e-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  <span data-ttu-id="7223e-124">Bir hizmet sınıfında Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="7223e-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="7223e-125">Adres veya bağlama bilgisi hizmet uygulaması içinde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7223e-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="7223e-126">Ayrıca, bu bilgileri yapılandırma dosyasından almak için yazılacak kodu yok.</span><span class="sxs-lookup"><span data-stu-id="7223e-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  <span data-ttu-id="7223e-127">Tanımlamak için bir Web.config dosyası oluşturmak <xref:System.ServiceModel.NetTcpBinding> tarafından kullanılmak üzere bağlama `CalculatorService` uç noktaları.</span><span class="sxs-lookup"><span data-stu-id="7223e-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4.  <span data-ttu-id="7223e-128">Aşağıdaki kodu içeren bir Service.svc dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7223e-128">Create a Service.svc file that contains the following code.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  <span data-ttu-id="7223e-129">Service.svc dosyasını, IIS sanal dizininde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7223e-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="7223e-130">Hizmeti kullanmak için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7223e-130">To create a client to use the service</span></span>  
  
1.  <span data-ttu-id="7223e-131">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.</span><span class="sxs-lookup"><span data-stu-id="7223e-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="7223e-132">Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7223e-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  <span data-ttu-id="7223e-133">Oluşturulan istemci uygulaması da uyarlamasını içeren `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="7223e-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="7223e-134">Adres ve bağlama bilgilerini hizmet uygulaması içinde herhangi bir yerde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7223e-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="7223e-135">Ayrıca, bu bilgileri yapılandırma dosyasından almak için yazılacak kodu yok.</span><span class="sxs-lookup"><span data-stu-id="7223e-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  <span data-ttu-id="7223e-136">Kullanan istemci yapılandırması <xref:System.ServiceModel.NetTcpBinding> Svcutil.exe tarafından da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7223e-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="7223e-137">Bu dosya App.config dosyasında Visual Studio kullanırken adlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7223e-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  <span data-ttu-id="7223e-138">Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="7223e-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  <span data-ttu-id="7223e-139">Derleme ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7223e-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7223e-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7223e-140">See Also</span></span>  
 [<span data-ttu-id="7223e-141">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7223e-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="7223e-142">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="7223e-142">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
