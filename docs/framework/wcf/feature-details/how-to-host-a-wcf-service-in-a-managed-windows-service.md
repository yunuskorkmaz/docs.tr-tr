---
title: 'Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma'
description: Bir Windows hizmeti tarafından barındırılan bir WCF hizmeti oluşturmayı öğrenin. Bu barındırma seçeneği Windows 'un tüm sürümlerinde kullanılabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 4e07aa7aac82fae5cfd1bfc759ef724cf87a873a
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246942"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="938b0-104">Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="938b0-104">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="938b0-105">Bu konuda, bir Windows hizmeti tarafından barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="938b0-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="938b0-106">Bu senaryo, ileti etkinleştirilmemiş güvenli bir ortamda Internet Information Services (IIS) dışında barındırılan, uzun süre çalışan bir WCF hizmeti olan yönetilen Windows hizmeti barındırma seçeneği tarafından etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="938b0-106">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="938b0-107">Hizmetin kullanım ömrü, işletim sistemi tarafından bunun yerine denetlenir.</span><span class="sxs-lookup"><span data-stu-id="938b0-107">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="938b0-108">Bu barındırma seçeneği Windows 'un tüm sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="938b0-108">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="938b0-109">Windows Hizmetleri, Microsoft Yönetim Konsolu 'nda (MMC) Microsoft. ManagementConsole. Snapın ile yönetilebilir ve sistem önyüklendiğinde otomatik olarak başlayacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="938b0-109">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="938b0-110">Bu barındırma seçeneği, hizmet işlem ömrünün Windows Hizmetleri için hizmet denetimi Yöneticisi (SCM) tarafından denetlenmesi için bir WCF hizmetini yönetilen bir Windows hizmeti olarak barındıran uygulama etki alanını (AppDomain) kaydetmeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="938b0-110">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="938b0-111">Hizmet kodu, hizmet sözleşmesinin bir hizmet uygulamasını, bir Windows hizmeti sınıfını ve bir yükleyici sınıfını içerir.</span><span class="sxs-lookup"><span data-stu-id="938b0-111">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="938b0-112">Hizmet uygulama sınıfı, `CalculatorService` BIR WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="938b0-112">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="938b0-113">, `CalculatorWindowsService` Bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="938b0-113">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="938b0-114">Bir Windows hizmeti olarak nitelendirmek için, sınıfı öğesinden devralır `ServiceBase` ve `OnStart` ve yöntemlerini uygular `OnStop` .</span><span class="sxs-lookup"><span data-stu-id="938b0-114">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="938b0-115">İçinde `OnStart` , <xref:System.ServiceModel.ServiceHost> türü için oluşturulur `CalculatorService` ve açılır.</span><span class="sxs-lookup"><span data-stu-id="938b0-115">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="938b0-116">`OnStop`' De, hizmet durdurulur ve bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="938b0-116">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="938b0-117">Ana bilgisayar Ayrıca, uygulama ayarlarında yapılandırılan hizmet ana bilgisayarı için bir temel adres sağlamaktan da sorumludur.</span><span class="sxs-lookup"><span data-stu-id="938b0-117">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="938b0-118">' Den devralan Yükleyici sınıfı <xref:System.Configuration.Install.Installer> , programın Installutil.exe aracı tarafından bir Windows hizmeti olarak yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="938b0-118">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="938b0-119">Hizmeti oluşturun ve barındırma kodunu sağlayın</span><span class="sxs-lookup"><span data-stu-id="938b0-119">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="938b0-120">**Hizmeti**adlı yeni bir Visual Studio **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="938b0-120">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="938b0-121">Program.cs olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="938b0-121">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="938b0-122">Ad alanını olarak değiştirin `Microsoft.ServiceModel.Samples` .</span><span class="sxs-lookup"><span data-stu-id="938b0-122">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="938b0-123">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="938b0-123">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="938b0-124">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="938b0-124">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="938b0-125">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="938b0-125">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="938b0-126">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="938b0-126">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="938b0-127">Aşağıdaki using deyimlerini Service.cs öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="938b0-127">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="938b0-128">`ICalculator`Hizmet sözleşmesini aşağıdaki kodda gösterildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="938b0-128">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="938b0-129">Hizmet sözleşmesini `CalculatorService` aşağıdaki kodda gösterildiği gibi adlı bir sınıfta uygulayın.</span><span class="sxs-lookup"><span data-stu-id="938b0-129">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="938b0-130">Sınıfından devralan adlı yeni bir sınıf oluşturun `CalculatorWindowsService` <xref:System.ServiceProcess.ServiceBase> .</span><span class="sxs-lookup"><span data-stu-id="938b0-130">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="938b0-131">Örneğe başvurmak için adlı bir yerel değişken ekleyin `serviceHost` <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="938b0-131">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="938b0-132">`Main`Çağıran yöntemi tanımlayın`ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="938b0-132">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="938b0-133"><xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>Aşağıdaki kodda gösterildiği gibi yeni bir örnek oluşturup açarak yöntemi geçersiz kılın <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="938b0-133">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="938b0-134"><xref:System.ServiceProcess.ServiceBase.OnStop%2A>Aşağıdaki kodda gösterildiği gibi, öğesini kapatan yöntemini geçersiz kılın <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="938b0-134">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="938b0-135">`ProjectInstaller`' Den devralan ve ' den ' a işaretlenmiş olarak işaretlenen yeni bir sınıf oluşturun <xref:System.Configuration.Install.Installer> <xref:System.ComponentModel.RunInstallerAttribute> `true` .</span><span class="sxs-lookup"><span data-stu-id="938b0-135">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="938b0-136">Bu, Windows hizmetinin Installutil.exe aracı tarafından yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="938b0-136">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="938b0-137">`Service`Projeyi oluştururken oluşturulan sınıfı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="938b0-137">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="938b0-138">Projeye bir uygulama yapılandırma dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="938b0-138">Add an application configuration file to the project.</span></span> <span data-ttu-id="938b0-139">Dosyanın içeriğini aşağıdaki yapılandırma XML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="938b0-139">Replace the contents of the file with the following configuration XML.</span></span>

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

     <span data-ttu-id="938b0-140">**Çözüm Gezgini** App.config dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="938b0-140">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="938b0-141">**Çıkış Dizinine Kopyala** ' nın altında **, daha yeniyse kopyala**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="938b0-141">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="938b0-142">Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="938b0-142">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="938b0-143">Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="938b0-143">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="938b0-144">Bu örnekte, hizmetin <xref:System.ServiceModel.Description.ServiceMetadataBehavior> olarak ayarlanmış olması nedeniyle `true` hizmetinize yayımlama meta verileri de etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="938b0-144">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="938b0-145">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="938b0-145">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="938b0-146">Hizmeti yükleyip çalıştırın</span><span class="sxs-lookup"><span data-stu-id="938b0-146">Install and run the service</span></span>

1. <span data-ttu-id="938b0-147">Yürütülebilir dosyayı oluşturmak için çözümü oluşturun `Service.exe` .</span><span class="sxs-lookup"><span data-stu-id="938b0-147">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="938b0-148">Visual Studio için Geliştirici Komut İstemi açın ve proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="938b0-148">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="938b0-149">`installutil bin\service.exe`Windows hizmetini yüklemek için komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="938b0-149">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="938b0-150">`services.msc`Service Control Manager 'a (SCM) erişmek için komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="938b0-150">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="938b0-151">Windows hizmeti hizmetlerde "WCFWindowsServiceSample" olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="938b0-151">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="938b0-152">WCF hizmeti yalnızca Windows hizmeti çalışıyorsa istemcilere yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="938b0-152">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="938b0-153">Hizmeti başlatmak için SCM 'de sağ tıklayın ve "Başlat" ı seçin veya komut istemine **net start WCFWindowsServiceSample** yazın.</span><span class="sxs-lookup"><span data-stu-id="938b0-153">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="938b0-154">Hizmette değişiklik yaparsanız, önce onu durdurup kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="938b0-154">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="938b0-155">Hizmeti durdurmak için SCM 'de hizmete sağ tıklayın ve "Durdur" seçeneğini belirleyin veya komut istemine **net stop WCFWindowsServiceSample yazın** .</span><span class="sxs-lookup"><span data-stu-id="938b0-155">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="938b0-156">Windows hizmetini durdurup bir istemciyi çalıştırırsanız, <xref:System.ServiceModel.EndpointNotFoundException> istemci hizmete erişmeye çalıştığında bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="938b0-156">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="938b0-157">Windows hizmet türü **InstallUtil/u bin\service.exe** kaldırmak için komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="938b0-157">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="938b0-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="938b0-158">Example</span></span>

<span data-ttu-id="938b0-159">Aşağıda, bu konunun kullandığı kodun tamamen bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="938b0-159">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="938b0-160">"Kendi kendine barındırma" seçeneğinde olduğu gibi, Windows hizmeti barındırma ortamı, bazı barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="938b0-160">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="938b0-161">Hizmet bir konsol uygulaması olarak uygulanır ve kendi barındırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="938b0-161">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="938b0-162">Internet Information Services (IIS) içinde barındırılan Windows Işlem etkinleştirme hizmeti (WAS) gibi diğer barındırma ortamlarında, geliştiricilerin barındırma kodunu yazması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="938b0-162">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="938b0-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="938b0-163">See also</span></span>

- [<span data-ttu-id="938b0-164">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="938b0-164">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="938b0-165">Yönetilen Bir Uygulamada Barındırma</span><span class="sxs-lookup"><span data-stu-id="938b0-165">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)
- [<span data-ttu-id="938b0-166">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="938b0-166">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="938b0-167">[Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="938b0-167">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
