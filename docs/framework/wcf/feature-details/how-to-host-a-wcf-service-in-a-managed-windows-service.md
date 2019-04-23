---
title: 'Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: c63b249cf16100f0b18d622fdecd7cd375df83d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297765"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="cdc9a-102">Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="cdc9a-102">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="cdc9a-103">Bu konuda, bir Windows hizmeti tarafından barındırılan bir Windows Communication Foundation (WCF) hizmet oluşturma için gerekli temel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="cdc9a-104">Senaryo, uzun süre çalışan, Internet Information Services (IIS) dışında iletisi etkin olmayan güvenli bir ortamda barındırılan bir WCF Hizmeti seçeneğini barındıran yönetilen Windows hizmeti olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="cdc9a-105">Hizmet ömrü, bunun yerine işletim sistemi tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="cdc9a-106">Barındırma bu seçenek, tüm Windows sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-106">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="cdc9a-107">Windows Hizmetleri Microsoft.ManagementConsole.SnapIn Microsoft Yönetim Konsolu (MMC) ile yönetilen ve sistem önyüklendiğinde otomatik olarak başlatılmasını yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="cdc9a-108">Bu barındırma seçeneği, yönetilen bir Windows hizmeti olarak bir WCF hizmetini barındıran ve böylece işlem ömrü hizmetin Windows Hizmetleri için Hizmet Denetimi Yöneticisi (SCM) tarafından denetlenen uygulama etki alanı (AppDomain) kaydetme oluşur.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="cdc9a-109">Hizmet kodunu bir hizmet uygulaması hizmet sözleşmesi ve bir Windows hizmet sınıfı bir yükleyici sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="cdc9a-110">Hizmet uygulaması sınıfı `CalculatorService`, bir WCF hizmeti.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="cdc9a-111">`CalculatorWindowsService` Bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="cdc9a-112">Bir Windows hizmeti olarak nitelemek için sınıf devraldığı `ServiceBase` ve uygulayan `OnStart` ve `OnStop` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="cdc9a-113">İçinde `OnStart`, <xref:System.ServiceModel.ServiceHost> için oluşturulan `CalculatorService` yazın ve açılır.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="cdc9a-114">İçinde `OnStop`, hizmeti durdurulur ve atıldı.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="cdc9a-115">Konak, uygulama ayarlarında yapılandırılan hizmet ana bilgisayarı için temel adres sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="cdc9a-116">Devralınan Yükleyici sınıfı <xref:System.Configuration.Install.Installer>, program tarafından Installutil.exe aracı bir Windows hizmeti olarak yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="cdc9a-117">Hizmet oluşturmak ve barındırma kodu sağlayın</span><span class="sxs-lookup"><span data-stu-id="cdc9a-117">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="cdc9a-118">Yeni bir Visual Studio oluşturma **konsol uygulaması** adlı proje **hizmet**.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-118">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="cdc9a-119">Program.cs adını da için yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-119">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="cdc9a-120">Ad alanına değiştirme `Microsoft.ServiceModel.Samples`.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-120">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="cdc9a-121">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cdc9a-121">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="cdc9a-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="cdc9a-122">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="cdc9a-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="cdc9a-123">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="cdc9a-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="cdc9a-124">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="cdc9a-125">Aşağıdaki using deyimlerini adını da.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-125">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="cdc9a-126">Tanımlama `ICalculator` aşağıdaki kodda gösterildiği gibi hizmet sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-126">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="cdc9a-127">Adlı bir sınıf içinde hizmet sözleşmesini uygulama `CalculatorService` aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="cdc9a-128">Adlı yeni bir sınıf oluşturma `CalculatorWindowsService` öğesinden devralan <xref:System.ServiceProcess.ServiceBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="cdc9a-129">Adlı bir yerel değişken ekleme `serviceHost` başvurusuna <xref:System.ServiceModel.ServiceHost> örneği.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="cdc9a-130">Tanımlama `Main` çağıran yöntemi `ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="cdc9a-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="cdc9a-131">Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> oluşturarak ve yeni açma yöntemi <xref:System.ServiceModel.ServiceHost> örneği aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="cdc9a-132">Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemi kapanış <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="cdc9a-133">Adlı yeni bir sınıf oluşturma `ProjectInstaller` öğesinden devralan <xref:System.Configuration.Install.Installer> ve ile işaretlenen <xref:System.ComponentModel.RunInstallerAttribute> kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="cdc9a-134">Bu, Installutil.exe aracı tarafından yüklenecek Windows hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="cdc9a-135">Kaldırma `Service` projeyi oluşturduğunuzda oluşturulan sınıf.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-135">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="cdc9a-136">Uygulama yapılandırma dosyası projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="cdc9a-137">Dosyanın içeriğini aşağıdaki yapılandırma XML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-137">Replace the contents of the file with the following configuration XML.</span></span>

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

     <span data-ttu-id="cdc9a-138">Sağ tıklayın App.config dosyasında **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="cdc9a-139">Altında **çıkış dizinine Kopyala** seçin **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="cdc9a-140">Bu örnek, uç noktaları yapılandırma dosyasında açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="cdc9a-141">Hizmet için uç nokta eklemezseniz, çalışma zamanı varsayılan uç noktalar ekler.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="cdc9a-142">Bu örnekte, hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kümesine `true`, hizmetinizin etkin meta veri yayımlama de vardır.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="cdc9a-143">Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cdc9a-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="cdc9a-144">Yükleme ve hizmet çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cdc9a-144">Install and run the service</span></span>

1. <span data-ttu-id="cdc9a-145">Çözümü oluşturmak için yapı `Service.exe` yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-145">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="cdc9a-146">Visual Studio için geliştirici komut istemi açın ve proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-146">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="cdc9a-147">Tür `installutil bin\service.exe` Windows hizmetini yüklemek için komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="cdc9a-148">Tür `services.msc` Hizmet Denetim Yöneticisi (SCM) erişmek için komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-148">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="cdc9a-149">Windows hizmeti Hizmetleri'nde "WCFWindowsServiceSample" görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-149">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="cdc9a-150">Windows Hizmeti çalışıyorsa WCF hizmeti yalnızca istemcilere yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-150">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="cdc9a-151">Hizmeti başlatmak için SCM ve Seç "Başlat" veya türü sağ **net Başlat WCFWindowsServiceSample** komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-151">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="cdc9a-152">Hizmete değişiklik yaparsanız, öncelikle durdurmak ve bunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-152">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="cdc9a-153">Hizmeti durdurun, SCM hizmete sağ tıklayın ve "Durdur" seçin veya **türü net stop WCFWindowsServiceSample** komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-153">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="cdc9a-154">Windows hizmetini durdurun ve ardından bir istemci çalıştırın gerçekleştiriyorsanız bir <xref:System.ServiceModel.EndpointNotFoundException> istemci hizmeti erişmeye çalışırken özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-154">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="cdc9a-155">Windows hizmet türünü kaldırma **InstallUtil /u bin\service.exe** komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-155">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="cdc9a-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="cdc9a-156">Example</span></span>

<span data-ttu-id="cdc9a-157">Bu konuda kullanılan kod tam listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cdc9a-157">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="cdc9a-158">Gibi bir "Kendi kendine barındırma" seçeneği, Windows hizmet barındırma ortamını bazı barındırma kodu uygulamanın bir parçası yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-158">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="cdc9a-159">Hizmet, bir konsol uygulaması olarak uygulanır ve kendi barındırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-159">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="cdc9a-160">Windows İşlem Etkinleştirme Hizmeti (WAS) barındıran Internet Information Services (IIS) gibi diğer barındırma ortamlarında yazmak, geliştiriciler için ise gerekli değildir kod barındırma.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-160">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdc9a-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-161">See also</span></span>

- [<span data-ttu-id="cdc9a-162">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cdc9a-162">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="cdc9a-163">Yönetilen Bir Uygulamada Barındırma</span><span class="sxs-lookup"><span data-stu-id="cdc9a-163">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [<span data-ttu-id="cdc9a-164">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="cdc9a-164">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="cdc9a-165">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="cdc9a-165">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)