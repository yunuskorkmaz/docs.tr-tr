---
title: 'Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 698a5134683341fedf2a37f7d6383770e14c232c
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964798"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="5f2ac-102">Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="5f2ac-102">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="5f2ac-103">Bu konuda, bir Windows hizmeti tarafından barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="5f2ac-104">Bu senaryo, ileti etkinleştirilmemiş güvenli bir ortamda Internet Information Services (IIS) dışında barındırılan, uzun süre çalışan bir WCF hizmeti olan yönetilen Windows hizmeti barındırma seçeneği tarafından etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="5f2ac-105">Hizmetin kullanım ömrü, işletim sistemi tarafından bunun yerine denetlenir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="5f2ac-106">Bu barındırma seçeneği Windows 'un tüm sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-106">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="5f2ac-107">Windows Hizmetleri, Microsoft Yönetim Konsolu 'nda (MMC) Microsoft. ManagementConsole. Snapın ile yönetilebilir ve sistem önyüklendiğinde otomatik olarak başlayacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="5f2ac-108">Bu barındırma seçeneği, hizmet işlem ömrünün Windows Hizmetleri için hizmet denetimi Yöneticisi (SCM) tarafından denetlenmesi için bir WCF hizmetini yönetilen bir Windows hizmeti olarak barındıran uygulama etki alanını (AppDomain) kaydetmeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="5f2ac-109">Hizmet kodu, hizmet sözleşmesinin bir hizmet uygulamasını, bir Windows hizmeti sınıfını ve bir yükleyici sınıfını içerir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="5f2ac-110">Hizmet uygulama sınıfı `CalculatorService`, bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="5f2ac-111">`CalculatorWindowsService` bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="5f2ac-112">Bir Windows hizmeti olarak nitelendirmek için, sınıf `ServiceBase` devralır ve `OnStart` ve `OnStop` yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="5f2ac-113">`OnStart`, `CalculatorService` türü için <xref:System.ServiceModel.ServiceHost> oluşturulur ve açılır.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="5f2ac-114">`OnStop`, hizmet durdurulur ve bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="5f2ac-115">Ana bilgisayar Ayrıca, uygulama ayarlarında yapılandırılan hizmet ana bilgisayarı için bir temel adres sağlamaktan da sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="5f2ac-116"><xref:System.Configuration.Install.Installer>devralan Yükleyici sınıfı, programın InstallUtil. exe aracı tarafından bir Windows hizmeti olarak yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="5f2ac-117">Hizmeti oluşturun ve barındırma kodunu sağlayın</span><span class="sxs-lookup"><span data-stu-id="5f2ac-117">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="5f2ac-118">**Hizmeti**adlı yeni bir Visual Studio **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-118">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="5f2ac-119">Program.cs olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-119">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="5f2ac-120">Ad alanını `Microsoft.ServiceModel.Samples`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-120">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="5f2ac-121">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f2ac-121">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="5f2ac-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="5f2ac-122">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="5f2ac-123">System. ServiceProcess. dll</span><span class="sxs-lookup"><span data-stu-id="5f2ac-123">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="5f2ac-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="5f2ac-124">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="5f2ac-125">Aşağıdaki using deyimlerini Service.cs öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-125">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="5f2ac-126">Aşağıdaki kodda gösterildiği gibi `ICalculator` hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-126">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="5f2ac-127">Hizmet sözleşmesini, aşağıdaki kodda gösterildiği gibi `CalculatorService` adlı bir sınıfta uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="5f2ac-128"><xref:System.ServiceProcess.ServiceBase> sınıfından devralan `CalculatorWindowsService` adlı yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="5f2ac-129"><xref:System.ServiceModel.ServiceHost> örneğine başvurmak için `serviceHost` adlı bir yerel değişken ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="5f2ac-130">`ServiceBase.Run(new CalculatorWindowsService)` çağıran `Main` yöntemi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="5f2ac-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="5f2ac-131">Aşağıdaki kodda gösterildiği gibi yeni bir <xref:System.ServiceModel.ServiceHost> örneği oluşturup açarak <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="5f2ac-132">Aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ServiceHost> kapatan <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="5f2ac-133"><xref:System.Configuration.Install.Installer> devralan ve `true`<xref:System.ComponentModel.RunInstallerAttribute> ayarlanmış olarak işaretlenen `ProjectInstaller` adlı yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="5f2ac-134">Bu, Windows hizmetinin InstallUtil. exe aracı tarafından yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="5f2ac-135">Projeyi oluştururken oluşturulan `Service` sınıfını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-135">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="5f2ac-136">Projeye bir uygulama yapılandırma dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="5f2ac-137">Dosyanın içeriğini aşağıdaki yapılandırma XML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-137">Replace the contents of the file with the following configuration XML.</span></span>

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

     <span data-ttu-id="5f2ac-138">**Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="5f2ac-139">**Çıkış Dizinine Kopyala** ' nın altında **, daha yeniyse kopyala**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="5f2ac-140">Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="5f2ac-141">Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="5f2ac-142">Bu örnekte, hizmet `true`olarak ayarlanmış <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sahip olduğundan, hizmetiniz yayımlama meta verilerini de etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="5f2ac-143">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="5f2ac-144">Hizmeti yükleyip çalıştırın</span><span class="sxs-lookup"><span data-stu-id="5f2ac-144">Install and run the service</span></span>

1. <span data-ttu-id="5f2ac-145">`Service.exe` çalıştırılabiliri oluşturmak için çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-145">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="5f2ac-146">Visual Studio için Geliştirici Komut İstemi açın ve proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-146">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="5f2ac-147">Windows hizmetini yüklemek için komut istemine `installutil bin\service.exe` yazın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="5f2ac-148">Service Control Manager 'a (SCM) erişmek için komut istemine `services.msc` yazın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-148">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="5f2ac-149">Windows hizmeti hizmetlerde "WCFWindowsServiceSample" olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-149">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="5f2ac-150">WCF hizmeti yalnızca Windows hizmeti çalışıyorsa istemcilere yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-150">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="5f2ac-151">Hizmeti başlatmak için SCM 'de sağ tıklayın ve "Başlat" ı seçin veya komut istemine **net start WCFWindowsServiceSample** yazın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-151">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="5f2ac-152">Hizmette değişiklik yaparsanız, önce onu durdurup kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-152">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="5f2ac-153">Hizmeti durdurmak için SCM 'de hizmete sağ tıklayın ve "Durdur" seçeneğini belirleyin veya komut istemine **net stop WCFWindowsServiceSample yazın** .</span><span class="sxs-lookup"><span data-stu-id="5f2ac-153">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="5f2ac-154">Windows hizmetini durdurup bir istemciyi çalıştırırsanız, istemci hizmete erişmeyi denediğinde bir <xref:System.ServiceModel.EndpointNotFoundException> özel durum oluştuğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-154">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="5f2ac-155">Windows hizmet türü **InstallUtil/u bin\service.exe** komutunu komut istemine kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-155">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="5f2ac-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f2ac-156">Example</span></span>

<span data-ttu-id="5f2ac-157">Aşağıda, bu konunun kullandığı kodun tamamen bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5f2ac-157">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="5f2ac-158">"Kendi kendine barındırma" seçeneğinde olduğu gibi, Windows hizmeti barındırma ortamı, bazı barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-158">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="5f2ac-159">Hizmet bir konsol uygulaması olarak uygulanır ve kendi barındırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-159">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="5f2ac-160">Internet Information Services (IIS) içinde barındırılan Windows Işlem etkinleştirme hizmeti (WAS) gibi diğer barındırma ortamlarında, geliştiricilerin barındırma kodunu yazması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-160">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f2ac-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f2ac-161">See also</span></span>

- [<span data-ttu-id="5f2ac-162">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5f2ac-162">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="5f2ac-163">Yönetilen Bir Uygulamada Barındırma</span><span class="sxs-lookup"><span data-stu-id="5f2ac-163">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [<span data-ttu-id="5f2ac-164">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5f2ac-164">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- <span data-ttu-id="5f2ac-165">[Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5f2ac-165">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
