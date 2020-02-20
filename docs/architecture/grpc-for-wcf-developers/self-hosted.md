---
title: Self-hosted gRPC uygulamaları-WCF geliştiricileri için gRPC
description: ASP.NET Core gRPC uygulamalarını self-hosted Hizmetleri olarak dağıtma.
ms.date: 09/02/2019
ms.openlocfilehash: 2244f161ad4b5d60138ae0f7b4d6a9c8c8829aa8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503407"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="d38a2-103">Şirket içinde barındırılan gRPC uygulamaları</span><span class="sxs-lookup"><span data-stu-id="d38a2-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="d38a2-104">ASP.NET Core 3,0 uygulamaları Windows Server 'da IIS 'de barındırılamasa da, HTTP/2 işlevselliğinin bazıları desteklenmediğinden, şu anda IIS 'de bir gRPC uygulaması barındırılamaz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="d38a2-105">Bu işlevsellik, gelecekteki bir Windows Server güncelleştirmesi için bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="d38a2-106">Uygulamanızı bir Windows hizmeti olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="d38a2-107">Veya .NET Core 3,0 barındırma uzantılarında yeni özellikler nedeniyle bu hizmeti [systemd](https://en.wikipedia.org/wiki/Systemd)tarafından denetlenen bir Linux hizmeti olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="d38a2-108">Uygulamanızı bir Windows hizmeti olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d38a2-108">Run your app as a Windows service</span></span>

<span data-ttu-id="d38a2-109">ASP.NET Core uygulamanızı bir Windows hizmeti olarak çalışacak şekilde yapılandırmak için, NuGet 'den [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="d38a2-110">Ardından, `Program.cs``CreateHostBuilder` yöntemine `UseWindowsService` bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d38a2-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="d38a2-111">Uygulama bir Windows hizmeti olarak çalışmıyorsa `UseWindowsService` yöntemi hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="d38a2-112">Şimdi aşağıdaki yöntemlerden birini kullanarak uygulamanızı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="d38a2-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="d38a2-113">Visual Studio 'dan projeye sağ tıklayıp kısayol menüsünde **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="d38a2-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="d38a2-114">.NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="d38a2-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="d38a2-115">Bir .NET Core uygulaması yayımladığınızda, *çerçeveye bağımlı* bir dağıtım veya *kendi kendine dahil* edilen bir dağıtım oluşturmayı tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="d38a2-116">Çerçeveye bağımlı dağıtımlar, çalıştırıldıkları konakta .NET Core paylaşılan çalışma zamanının yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="d38a2-117">Kendi içindeki dağıtımlar, .NET Core çalışma zamanının ve çerçevesinin tam kopyasıyla yayımlanır ve herhangi bir konakta çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="d38a2-118">Her yaklaşımın avantajları ve dezavantajları dahil daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../../core/deploying/index.md) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d38a2-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="d38a2-119">.NET Core 3,0 çalışma zamanının konakta yüklü olmasını gerektirmeyen uygulamanın kendi içindeki bir derlemesini yayımlamak için, uygulamaya dahil edilecek çalışma zamanını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d38a2-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="d38a2-120">`-r` (veya `--runtime`) bayrağını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="d38a2-121">Çerçeveye bağımlı bir yapı yayımlamak için `-r` bayrağını atlayın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="d38a2-122">`publish` dizininin tüm içeriğini bir yükleme klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="d38a2-123">Ardından, bir yürütülebilir dosya için bir Windows hizmeti oluşturmak üzere [SC aracını](/windows/desktop/services/controlling-a-service-using-sc) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="d38a2-124">Windows olay günlüğü 'ne Kaydet</span><span class="sxs-lookup"><span data-stu-id="d38a2-124">Log to the Windows event log</span></span>

<span data-ttu-id="d38a2-125">`UseWindowsService` yöntemi, Windows olay günlüğüne günlük iletilerini yazan bir [günlüğe kaydetme](/aspnet/core/fundamentals/logging/) sağlayıcısını otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="d38a2-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="d38a2-126">`appsettings.json` ya da başka bir yapılandırma kaynağının `Logging` bölümüne bir `EventLog` girişi ekleyerek bu sağlayıcının günlüğünü yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span> 

<span data-ttu-id="d38a2-127">Bu ayarlarda bir `SourceName` özelliğini ayarlayarak olay günlüğünde kullanılan kaynak adını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="d38a2-128">Bir ad belirtmezseniz, varsayılan uygulama adı (normalde yürütülebilir derleme adı) kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="d38a2-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="d38a2-129">Günlüğe kaydetme hakkında daha fazla bilgi bu bölümün sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d38a2-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="d38a2-130">Uygulamanızı systemd ile Linux hizmeti olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d38a2-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="d38a2-131">ASP.NET Core uygulamanızı bir Linux hizmeti olarak çalışacak şekilde yapılandırmak için (veya Linux paranın *arka plan programı* ), NuGet 'den [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="d38a2-132">Ardından, `Program.cs``CreateHostBuilder` yöntemine `UseSystemd` bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d38a2-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="d38a2-133">Uygulama bir Linux hizmeti olarak çalışmıyorsa `UseSystemd` yöntemi hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="d38a2-134">Şimdi uygulamanızı yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-134">Now publish your application.</span></span> <span data-ttu-id="d38a2-135">Uygulama, ilgili Linux çalışma zamanı (örneğin, `linux-x64`) için çerçeve bağımlı veya kendi kendine dahil olabilir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="d38a2-136">Aşağıdaki yöntemlerden birini kullanarak yayımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d38a2-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="d38a2-137">Visual Studio 'dan projeye sağ tıklayıp kısayol menüsünde **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="d38a2-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span> 
* <span data-ttu-id="d38a2-138">.NET Core CLI, aşağıdaki komutu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d38a2-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
<span data-ttu-id="d38a2-139">`publish` dizininin tüm içeriğini Linux ana bilgisayarındaki bir yükleme klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="d38a2-140">Hizmeti kaydettirmek, `/etc/systemd/system` dizinine eklenmek üzere *birim dosyası*olarak adlandırılan özel bir dosya gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="d38a2-141">Bu klasörde bir dosya oluşturmak için kök izninizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="d38a2-142">`systemd` kullanmak istediğiniz tanımlayıcıyı ve `.service` uzantısını adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="d38a2-143">Örneğin, `/etc/systemd/system/myapp.service`kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="d38a2-144">Hizmet dosyası, aşağıdaki örnekte gösterildiği gibi ıNı biçimini kullanır:</span><span class="sxs-lookup"><span data-stu-id="d38a2-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="d38a2-145">`Type=notify` özelliği, uygulamanın başlatma ve kapatmayla haberdar olacağını `systemd` söyler.</span><span class="sxs-lookup"><span data-stu-id="d38a2-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="d38a2-146">`WantedBy=multi-user.target` ayarı, Linux sistemi "Runlevel 2" değerine ulaştığında hizmetin başlatılmasına neden olur. Bu, grafik olmayan bir çok kullanıcılı kabuğun etkin olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="d38a2-147">`systemd`, hizmeti tanıyamadan önce, yapılandırmasını yeniden yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="d38a2-148">`systemctl` komutunu kullanarak `systemd` denetlersiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="d38a2-149">Yeniden yüklendikten sonra, uygulamanın başarıyla kaydedildiğini doğrulamak için `status` alt komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="d38a2-150">Hizmeti doğru şekilde yapılandırdıysanız aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="d38a2-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="d38a2-151">Hizmeti başlatmak için `start` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="d38a2-152">`systemctl start`kullandığınızda `.service` uzantısı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d38a2-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="d38a2-153">`systemd` sistem başlangıcında hizmeti otomatik olarak başlatmasını söylemek için `enable` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="d38a2-154">Journald 'de günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="d38a2-154">Log to journald</span></span>

<span data-ttu-id="d38a2-155">Windows olay günlüğü 'nün Linux eşdeğeri, `systemd`bir parçası olan yapılandırılmış bir günlük sistem hizmetidir `journald`.</span><span class="sxs-lookup"><span data-stu-id="d38a2-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="d38a2-156">Bir Linux Daemon tarafından standart çıktıya yazılan günlük iletileri `journald`otomatik olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="d38a2-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="d38a2-157">Günlüğe kaydetme düzeylerini yapılandırmak için, günlük yapılandırmasının `Console` bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="d38a2-158">`UseSystemd` ana bilgisayar Oluşturucu yöntemi, konsol çıkış biçimini otomatik olarak günlüğe uyacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d38a2-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="d38a2-159">`journald`, Linux günlükleri için standart olduğundan, çeşitli araçlar onunla tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="d38a2-160">Günlükleri `journald` bir dış günlük sistemine kolayca yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="d38a2-161">Konakta yerel olarak çalışarak, komut satırından günlükleri görüntülemek için `journalctl` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="d38a2-162">Ana bilgisayarınızda kullanılabilir bir GUI ortamınız varsa, Linux için *Qjournalctl* ve *GNOME günlükleri*gibi birkaç grafik günlük görüntüleyicileri vardır.</span><span class="sxs-lookup"><span data-stu-id="d38a2-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="d38a2-163">`journalctl`kullanarak komut satırından `systemd` günlüğünü sorgulama hakkında daha fazla bilgi edinmek için, [adam sayfalarına](https://manpages.debian.org/buster/systemd/journalctl.1)bakın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="d38a2-164">Şirket içinde barındırılan uygulamalar için HTTPS sertifikaları</span><span class="sxs-lookup"><span data-stu-id="d38a2-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="d38a2-165">Üretimde bir gRPC uygulaması çalıştırırken, güvenilir bir sertifika yetkilisinden (CA) bir TLS sertifikası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="d38a2-166">Bu CA, bir genel CA veya kuruluşunuz için bir dahili olabilir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="d38a2-167">Windows konakları üzerinde, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıfını kullanarak güvenli bir [sertifika deposundan](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sertifikayı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="d38a2-168">`X509Store` sınıfını, bazı Linux konaklarındaki OpenSSL anahtar deposu ile de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38a2-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="d38a2-169">Ayrıca, [X509Certificate2 oluşturucularından](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)birini kullanarak da sertifikalar oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d38a2-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="d38a2-170">Güçlü bir parolayla korunan `.pfx` dosyası gibi bir dosya</span><span class="sxs-lookup"><span data-stu-id="d38a2-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="d38a2-171">[Azure Key Vault](https://azure.microsoft.com/services/key-vault/) gibi güvenli bir depolama hizmetinden alınan ikili veriler</span><span class="sxs-lookup"><span data-stu-id="d38a2-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="d38a2-172">Kestrel 'yi bir sertifikayı kullanmak için iki şekilde yapılandırabilirsiniz: yapılandırmadan veya koddan.</span><span class="sxs-lookup"><span data-stu-id="d38a2-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="d38a2-173">HTTPS sertifikalarını yapılandırma kullanarak ayarlama</span><span class="sxs-lookup"><span data-stu-id="d38a2-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="d38a2-174">Yapılandırma yaklaşımı, sertifika `.pfx` dosyası yolunu ve Kestrel yapılandırma bölümünde parolayı ayarlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d38a2-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="d38a2-175">`appsettings.json`, bu şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="d38a2-175">In `appsettings.json`, that would look like this:</span></span>

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

<span data-ttu-id="d38a2-176">Azure Key Vault veya HashiCorp kasası gibi güvenli bir yapılandırma kaynağı kullanarak parolayı girin.</span><span class="sxs-lookup"><span data-stu-id="d38a2-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d38a2-177">Şifrelenmemiş parolaları yapılandırma dosyalarında depolamamayın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="d38a2-178">Kodda HTTPS sertifikaları ayarlama</span><span class="sxs-lookup"><span data-stu-id="d38a2-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="d38a2-179">Kodda HTTPS 'yi yapılandırmak için, `Program` sınıfında `IWebHostBuilder` `ConfigureKestrel` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38a2-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

<span data-ttu-id="d38a2-180">Ayrıca, `.pfx` dosyanın parolasını içinde depoladığınızdan ve güvenli bir yapılandırma kaynağından geri aldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d38a2-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d38a2-181">[Önceki](grpc-in-production.md)
>[İleri](docker.md)</span><span class="sxs-lookup"><span data-stu-id="d38a2-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
