---
title: "Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4b2c8daa176ef1f9aef24cac3125d59fcc02fa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="380a2-102">Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="380a2-102">How to: Host a WCF Service in a Managed Windows Service</span></span>
<span data-ttu-id="380a2-103">Bu konu oluşturmak için gereken temel adımlarda özetler bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir Windows hizmeti tarafından barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="380a2-103">This topic outlines the basic steps required to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service that is hosted by a Windows Service.</span></span> <span data-ttu-id="380a2-104">Senaryo barındırma uzun süreli olduğundan seçeneği yönetilen Windows hizmeti tarafından etkin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] etkinleştirildi, değil ileti güvenli bir ortamda Internet Information Services (IIS) dışında barındırılan hizmeti.</span><span class="sxs-lookup"><span data-stu-id="380a2-104">The scenario is enabled by the managed Windows service hosting option that is a long-running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="380a2-105">Hizmet ömrü, bunun yerine işletim sistemi tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="380a2-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="380a2-106">Barındırma bu seçenek, tüm Windows sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="380a2-106">This hosting option is available in all versions of Windows.</span></span>  
  
 <span data-ttu-id="380a2-107">Windows Hizmetleri Microsoft.ManagementConsole.SnapIn Microsoft Yönetim Konsolu (MMC) ile yönetilebilir ve sistem önyüklendiğinde otomatik olarak başlatılmasını yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="380a2-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="380a2-108">Bu barındırma seçeneği barındıran uygulama etki alanı (AppDomain) kaydetme oluşan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet yönetilen bir Windows hizmet böylece hizmeti işlem ömrü Windows Hizmetleri için Hizmet Denetim Yöneticisi (SCM) tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="380a2-108">This hosting option consists of registering the application domain (AppDomain) that hosts a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>  
  
 <span data-ttu-id="380a2-109">Hizmet koduna bir hizmet uygulaması hizmet sözleşmesi, bir Windows hizmet sınıfı ve bir yükleyici sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="380a2-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="380a2-110">Hizmet uygulaması sınıfı `CalculatorService`, olan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="380a2-110">The service implementation class, `CalculatorService`, is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="380a2-111">`CalculatorWindowsService` Bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="380a2-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="380a2-112">Bir Windows hizmeti olarak nitelemek için sınıfının devraldığı `ServiceBase` ve uygulayan `OnStart` ve `OnStop` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="380a2-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="380a2-113">İçinde `OnStart`, <xref:System.ServiceModel.ServiceHost> için oluşturulan `CalculatorService` yazın ve açılır.</span><span class="sxs-lookup"><span data-stu-id="380a2-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="380a2-114">İçinde `OnStop`, hizmeti durdurulur ve atıldı.</span><span class="sxs-lookup"><span data-stu-id="380a2-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="380a2-115">Konak, uygulama ayarları'nda yapılandırılmış hizmet ana bilgisayarı için bir taban adresi sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="380a2-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="380a2-116">Öğesinden devralınan Yükleyici sınıfı <xref:System.Configuration.Install.Installer>, programın bir Windows hizmeti olarak Installutil.exe aracı tarafından yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="380a2-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>  
  
### <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="380a2-117">Hizmet oluşturmak ve barındırma kodu sağlayın</span><span class="sxs-lookup"><span data-stu-id="380a2-117">Construct the service and provide the hosting code</span></span>  
  
1.  <span data-ttu-id="380a2-118">"Hizmet" adlı yeni bir Visual Studio konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="380a2-118">Create a new Visual Studio Console Application project called "Service".</span></span>  
  
2.  <span data-ttu-id="380a2-119">Program.cs için adını da yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="380a2-119">Rename Program.cs to Service.cs.</span></span>  
  
3.  <span data-ttu-id="380a2-120">Ad alanı için Microsoft.ServiceModel.Samples değiştirin.</span><span class="sxs-lookup"><span data-stu-id="380a2-120">Change the namespace to Microsoft.ServiceModel.Samples.</span></span>  
  
4.  <span data-ttu-id="380a2-121">Aşağıdaki derlemeler başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380a2-121">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="380a2-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="380a2-122">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="380a2-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="380a2-123">System.ServiceProcess.dll</span></span>  
  
    -   <span data-ttu-id="380a2-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="380a2-124">System.Configuration.Install.dll</span></span>  
  
5.  <span data-ttu-id="380a2-125">Aşağıdaki using deyimlerini adını da ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380a2-125">Add the following using statements to Service.cs.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  <span data-ttu-id="380a2-126">Tanımlamak `ICalculator` aşağıdaki kodda gösterildiği gibi hizmet sözleşme.</span><span class="sxs-lookup"><span data-stu-id="380a2-126">Define the `ICalculator` service contract as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  <span data-ttu-id="380a2-127">Adlı bir sınıf hizmet sözleşmesini uygulama `CalculatorService` aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="380a2-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  <span data-ttu-id="380a2-128">Adlı yeni bir sınıf oluşturmak `CalculatorWindowsService` devraldığı <xref:System.ServiceProcess.ServiceBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="380a2-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="380a2-129">Adlı bir yerel değişken Ekle `serviceHost` başvuru <xref:System.ServiceModel.ServiceHost> örneği.</span><span class="sxs-lookup"><span data-stu-id="380a2-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="380a2-130">Tanımlamak `Main` çağıran yöntemi`ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="380a2-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. <span data-ttu-id="380a2-131">Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> oluşturarak ve yeni açma yöntemini <xref:System.ServiceModel.ServiceHost> örneği aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="380a2-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. <span data-ttu-id="380a2-132">Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemi kapanış <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="380a2-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. <span data-ttu-id="380a2-133">Adlı yeni bir sınıf oluşturmak `ProjectInstaller` devraldığı <xref:System.Configuration.Install.Installer> ve ile işaretlenmiş <xref:System.ComponentModel.RunInstallerAttribute> kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="380a2-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="380a2-134">Bu, Windows hizmeti tarafından Installutil.exe aracı yüklü olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="380a2-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. <span data-ttu-id="380a2-135">Kaldırma `Service` proje oluşturduğunuzda, oluşturulan sınıf.</span><span class="sxs-lookup"><span data-stu-id="380a2-135">Remove the `Service` class that was generated when you created the project.</span></span>  
  
13. <span data-ttu-id="380a2-136">Uygulama yapılandırma dosyası projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380a2-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="380a2-137">Aşağıdaki yapılandırma XML dosyasının içeriğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="380a2-137">Replace the contents of the file with the following configuration XML.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>    <services>  
          <!-- This section is optional with the new configuration model  
               introduced in .NET Framework 4. -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                   behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceMetadata httpGetEnabled="true"/>  
              <serviceDebug includeExceptionDetailInFaults="False"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="380a2-138">App.config dosyasını sağ tıklatın **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="380a2-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="380a2-139">Altında **çıktı dizinine Kopyala** seçin **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="380a2-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>  
  
     <span data-ttu-id="380a2-140">Bu örnek, yapılandırma dosyasında uç noktalar açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="380a2-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="380a2-141">Hizmeti için uç nokta eklemezseniz çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="380a2-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="380a2-142">Bu örnekte, hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kümesine `true`, hizmetiniz etkin meta veri yayımlama de vardır.</span><span class="sxs-lookup"><span data-stu-id="380a2-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="380a2-143">Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="380a2-143"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
### <a name="install-and-run-the-service"></a><span data-ttu-id="380a2-144">Yükleyin ve hizmet çalıştırın</span><span class="sxs-lookup"><span data-stu-id="380a2-144">Install and run the service</span></span>  
  
1.  <span data-ttu-id="380a2-145">Çözüm oluşturmak için yapı `Service.exe` yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="380a2-145">Build the solution to create the `Service.exe` executable.</span></span>  
  
2.  <span data-ttu-id="380a2-146">Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi açın ve proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="380a2-146">Open the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the project directory.</span></span> <span data-ttu-id="380a2-147">Tür `installutil bin\service.exe` Windows hizmetini yüklemek için komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="380a2-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="380a2-148">Kullanmıyorsanız, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut isteminde, olduğundan emin olun `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` sistem yolunda dizindir.</span><span class="sxs-lookup"><span data-stu-id="380a2-148">If you do not use the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt, make sure that the `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` directory is in the system path.</span></span>  
  
     <span data-ttu-id="380a2-149">Tür `services.msc` Hizmet Denetim Yöneticisi (SCM) erişmek için komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="380a2-149">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="380a2-150">Windows hizmeti Hizmetleri'nde "WCFWindowsServiceSample" görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="380a2-150">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="380a2-151">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmeti yalnızca yanıt verebilmesini istemcilere Windows Hizmeti çalışıyorsa.</span><span class="sxs-lookup"><span data-stu-id="380a2-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="380a2-152">Hizmeti başlatmak için SCM ve "Başlat" veya türü sağ **net Başlat WCFWindowsServiceSample** komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="380a2-152">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>  
  
3.  <span data-ttu-id="380a2-153">Hizmete değişiklik yaparsanız, öncelikle durdurmak ve bunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="380a2-153">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="380a2-154">Hizmeti durdurmak, SCM hizmetinde sağ tıklatın ve "Durdur" seçin veya **türü net stop WCFWindowsServiceSample** komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="380a2-154">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="380a2-155">Windows hizmetini durdurun ve sonra bir istemci çalıştırırsanız unutmayın bir <xref:System.ServiceModel.EndpointNotFoundException> istemci hizmete erişmeye çalıştığında özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="380a2-155">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="380a2-156">Windows hizmet türünü kaldırmak için **InstallUtil /u bin\service.exe** komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="380a2-156">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="380a2-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="380a2-157">Example</span></span>  
 <span data-ttu-id="380a2-158">Bu konuda kullanılan kod tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="380a2-158">The following is a complete listing of the code used by this topic.</span></span>  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 <span data-ttu-id="380a2-159">"Kendi kendine barındırma" seçeneği gibi bazı barındırma kod uygulamanın bir parçası yazılması barındırma ortamı Windows hizmetini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="380a2-159">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="380a2-160">Hizmeti bir konsol uygulaması olarak uygulanır ve kendi barındırma kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="380a2-160">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="380a2-161">Windows İşlem Etkinleştirme Hizmeti (WAS) barındıran Internet Information Services (IIS) gibi diğer ortamlarda barındırma, geliştiricilerin yazmak için ise gerekli değildir kod barındırma.</span><span class="sxs-lookup"><span data-stu-id="380a2-161">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380a2-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="380a2-162">See Also</span></span>  
 [<span data-ttu-id="380a2-163">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="380a2-163">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="380a2-164">Yönetilen Bir Uygulamada Barındırma</span><span class="sxs-lookup"><span data-stu-id="380a2-164">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 [<span data-ttu-id="380a2-165">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="380a2-165">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="380a2-166">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="380a2-166">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
