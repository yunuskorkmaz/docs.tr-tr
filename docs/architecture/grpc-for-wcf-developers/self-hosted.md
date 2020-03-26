---
title: Kendi kendine barındırılan gRPC uygulamaları - WCF geliştiricileri için gRPC
description: Core gRPC uygulamalarını kendi kendine barındırılan hizmetler olarak ASP.NET dağıtma.
ms.date: 09/02/2019
ms.openlocfilehash: 69f70e4077247fd07eba7abeee82f257dd1f4f90
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110912"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="5d45d-103">Kendi kendine barındırılan gRPC uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5d45d-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="5d45d-104">ASP.NET Core 3.0 uygulamaları Windows Server'da IIS'de barındırılabilse de, şu anda HTTP/2 işlevlerinin bazıları desteklenmediği için IIS'de bir gRPC uygulamasını barındırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="5d45d-105">Bu işlev, Windows Server için gelecekteki bir güncelleştirme için bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="5d45d-106">Uygulamanızı bir Windows hizmeti olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="5d45d-107">Ya da .NET Core 3.0 barındırma uzantılarındaki yeni özellikler nedeniyle [sistemli](https://en.wikipedia.org/wiki/Systemd)tarafından kontrol edilen bir Linux hizmeti olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="5d45d-108">Uygulamanızı Windows hizmeti olarak çalıştırın</span><span class="sxs-lookup"><span data-stu-id="5d45d-108">Run your app as a Windows service</span></span>

<span data-ttu-id="5d45d-109">ASP.NET Core uygulamanızı Windows hizmeti olarak çalışacak şekilde yapılandırmak için NuGet'den [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5d45d-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="5d45d-110">Sonra `UseWindowsService` `CreateHostBuilder` yönteme bir çağrı `Program.cs`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5d45d-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="5d45d-111">Uygulama Windows hizmeti olarak çalışmıyorsa, `UseWindowsService` yöntem hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="5d45d-112">Şimdi bu yöntemlerden birini kullanarak uygulamanızı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="5d45d-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="5d45d-113">Visual Studio'dan projeyi sağ tıklayarak **Publish** ve kısayol menüsünde Yayınla'yı seçerek.</span><span class="sxs-lookup"><span data-stu-id="5d45d-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="5d45d-114">.NET Çekirdek CLI'den.</span><span class="sxs-lookup"><span data-stu-id="5d45d-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="5d45d-115">Bir .NET Core uygulaması yayımladığınızda, *çerçeveye bağımlı* bir dağıtım veya *bağımsız* bir dağıtım oluşturmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="5d45d-116">Çerçeveye bağımlı dağıtımlar, .NET Core Paylaşılan Çalışma Zamanı'nın çalıştırıldıkları ana bilgisayara yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="5d45d-117">Bağımsız dağıtımlar .NET Core çalışma zamanı nın ve çerçevesinin tam bir kopyasıyla yayımlanır ve herhangi bir ana bilgisayarda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="5d45d-118">Her yaklaşımın avantajları ve dezavantajları da dahil olmak üzere daha fazla bilgi için [.NET Core uygulama dağıtım](../../core/deploying/index.md) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="5d45d-119">.NET Core 3.0 çalışma zamanının ana bilgisayara yüklenmesini gerektirmeyen uygulamanın bağımsız bir yapısını yayımlamak için, uygulamaya eklenecek çalışma saatini belirtin.</span><span class="sxs-lookup"><span data-stu-id="5d45d-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="5d45d-120">`-r` (veya) `--runtime`bayrağı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="5d45d-121">Çerçeveye bağımlı bir yapı yayımlamak `-r` için bayrağı atlayın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="5d45d-122">Dizinin tüm içeriğini `publish` yükleme klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="5d45d-123">Ardından, yürütülebilir dosya için bir Windows hizmeti oluşturmak için [sc aracını](/windows/desktop/services/controlling-a-service-using-sc) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="5d45d-124">Windows etkinlik günlüğüne oturum açma</span><span class="sxs-lookup"><span data-stu-id="5d45d-124">Log to the Windows event log</span></span>

<span data-ttu-id="5d45d-125">Yöntem, `UseWindowsService` Windows olay günlüğüne günlük iletileri yazan bir [günlük](/aspnet/core/fundamentals/logging/) sağlayıcısını otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="5d45d-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="5d45d-126">Bu sağlayıcı nın `EventLog` `Logging` bölümüne `appsettings.json` veya başka bir yapılandırma kaynağına bir giriş ekleyerek günlük işlemlerini yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="5d45d-127">Bu ayarlarda bir `SourceName` özellik ayarlayarak olay günlüğünde kullanılan kaynak adı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="5d45d-128">Bir ad belirtmezseniz, varsayılan uygulama adı (normalde çalıştırılabilir derleme adı) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d45d-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="5d45d-129">Günlük hakkında daha fazla bilgi bu bölümün sonunda dır.</span><span class="sxs-lookup"><span data-stu-id="5d45d-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="5d45d-130">Uygulamanızı systemd ile linux hizmeti olarak çalıştırın</span><span class="sxs-lookup"><span data-stu-id="5d45d-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="5d45d-131">ASP.NET Core uygulamanızı Linux hizmeti (veya Linux dilinde *daemon)* olarak çalışacak şekilde yapılandırmak için, [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) paketini NuGet'den yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5d45d-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="5d45d-132">Sonra `UseSystemd` `CreateHostBuilder` yönteme bir çağrı `Program.cs`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5d45d-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="5d45d-133">Uygulama bir Linux hizmeti olarak çalışmıyorsa, `UseSystemd` yöntem hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="5d45d-134">Şimdi başvurunuzu yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-134">Now publish your application.</span></span> <span data-ttu-id="5d45d-135">Uygulama, ilgili Linux çalışma süresi için çerçeveye bağımlı veya bağımsız `linux-x64`olabilir (örneğin, ).</span><span class="sxs-lookup"><span data-stu-id="5d45d-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="5d45d-136">Şu yöntemlerden birini kullanarak yayımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5d45d-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="5d45d-137">Visual Studio'dan projeyi sağ tıklayarak **Publish** ve kısayol menüsünde Yayınla'yı seçerek.</span><span class="sxs-lookup"><span data-stu-id="5d45d-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="5d45d-138">.NET Core CLI'den aşağıdaki komutu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="5d45d-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="5d45d-139">`publish` Dizinin tüm içeriğini Linux ana bilgisayarındaki bir yükleme klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="5d45d-140">Hizmetin kaydedilmesi, `/etc/systemd/system` dizine eklenecek birim dosyası adı verilen özel bir *dosya*gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="5d45d-141">Bu klasörde bir dosya oluşturmak için kök iznine ihtiyacınız olur.</span><span class="sxs-lookup"><span data-stu-id="5d45d-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="5d45d-142">Kullanmak istediğiniz `systemd` tanımlayıcıve uzantı ile dosyayı `.service` adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="5d45d-143">Örneğin, kullanın. `/etc/systemd/system/myapp.service`</span><span class="sxs-lookup"><span data-stu-id="5d45d-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="5d45d-144">Hizmet dosyası, bu örnekte gösterildiği gibi INI biçimini kullanır:</span><span class="sxs-lookup"><span data-stu-id="5d45d-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="5d45d-145">Özellik, `Type=notify` `systemd` uygulamanın başlangıç ve kapatma konusunda bunu bildireceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="5d45d-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="5d45d-146">Ayar, `WantedBy=multi-user.target` Linux sistemi "runlevel 2"ye ulaştığında hizmetin başlamasına neden olur, bu da grafiksel olmayan, çok kullanıcılı bir kabuğun etkin olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="5d45d-147">Hizmeti `systemd` tanımadan önce yapılandırmasını yeniden yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="5d45d-148">Komutu `systemd` kullanarak `systemctl` kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="5d45d-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="5d45d-149">Yeniden yüklendikten sonra, uygulamanın `status` başarıyla kaydolduğunu doğrulamak için alt komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="5d45d-150">Hizmeti doğru şekilde yapılandırmışsanız, aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="5d45d-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="5d45d-151">Hizmeti `start` başlatmak için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="5d45d-152">Uzantısı `.service` kullanırken `systemctl start`isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5d45d-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="5d45d-153">Hizmeti `systemd` sistem başlatmada otomatik olarak başlatmayı `enable` söylemek için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="5d45d-154">Günlük olarak günlük olarak oturum aç</span><span class="sxs-lookup"><span data-stu-id="5d45d-154">Log to journald</span></span>

<span data-ttu-id="5d45d-155">Windows olay günlüğülinux eşdeğer `journald`, bir parçası olan yapılandırılmış bir `systemd`günlük sistemi hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="5d45d-156">Bir Linux daemon tarafından standart çıktıya yazılan günlük `journald`iletileri otomatik olarak .</span><span class="sxs-lookup"><span data-stu-id="5d45d-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="5d45d-157">Günlüğe kaydetme düzeylerini yapılandırmak için günlüğe kaydetme yapılandırmabölümünü kullanın. `Console`</span><span class="sxs-lookup"><span data-stu-id="5d45d-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="5d45d-158">Ana `UseSystemd` bilgisayar oluşturucu yöntemi, konsol çıktı biçimini günlük le eşecek şekilde otomatik olarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5d45d-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="5d45d-159">Linux `journald` günlükleri için standart olduğundan, çeşitli araçlar onunla entegre.</span><span class="sxs-lookup"><span data-stu-id="5d45d-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="5d45d-160">Günlükleri `journald` harici bir günlük sistemine kolayca yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="5d45d-161">Ana bilgisayar üzerinde yerel olarak çalışırken, komut satırından günlükleri görüntülemek için `journalctl` komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="5d45d-162">Ev sahibinizde bir GUI ortamı varsa, Linux için *QJournalctl* ve *gnome günlükleri*gibi birkaç grafik günlük görüntüleyen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="5d45d-163">`systemd` Kullanarak komut satırından günlüğü sorgulama hakkında daha `journalctl`fazla bilgi edinmek için, [bkz.](https://manpages.debian.org/buster/systemd/journalctl.1)</span><span class="sxs-lookup"><span data-stu-id="5d45d-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="5d45d-164">Kendi barındırılan uygulamalar için HTTPS sertifikaları</span><span class="sxs-lookup"><span data-stu-id="5d45d-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="5d45d-165">Üretimde bir gRPC uygulaması çalıştırıyorsanız, güvenilir bir sertifika yetkilisinden (CA) bir TLS sertifikası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="5d45d-166">Bu CA herkese açık bir CA veya kuruluşunuz için dahili bir CA olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="5d45d-167">Windows ana bilgisayarlarında, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıfı kullanarak sertifikayı güvenli bir sertifika [deposundan](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="5d45d-168">Sınıfı, bazı `X509Store` Linux ana bilgisayarlarında OpenSSL anahtar deposu ile de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="5d45d-169">[X509Certificate2 oluşturucularından](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)birini kullanarak da sertifika lar oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5d45d-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="5d45d-170">Güçlü bir parolayla `.pfx` korunan dosya gibi bir dosya</span><span class="sxs-lookup"><span data-stu-id="5d45d-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="5d45d-171">[Azure Key Vault](https://azure.microsoft.com/services/key-vault/) gibi güvenli bir depolama hizmetinden alınan ikili veriler</span><span class="sxs-lookup"><span data-stu-id="5d45d-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="5d45d-172">Kestrel'i bir sertifikayı yapılandırmadan veya kodda olmak üzere iki şekilde kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d45d-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="5d45d-173">Yapılandırmayı kullanarak HTTPS sertifikalarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="5d45d-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="5d45d-174">Yapılandırma yaklaşımı, Kestrel yapılandırma `.pfx` bölümünde sertifika dosyasına ve parolaya giden yolu ayarlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5d45d-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="5d45d-175">In `appsettings.json`, bu gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="5d45d-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="5d45d-176">Parolayı Azure Key Vault veya Hashicorp Vault gibi güvenli bir yapılandırma kaynağı kullanarak sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d45d-177">Şifrelenmemiş parolaları yapılandırma dosyalarında saklamayın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="5d45d-178">HTTPS sertifikalarını kodda ayarlama</span><span class="sxs-lookup"><span data-stu-id="5d45d-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="5d45d-179">Https'yi Kerkenez'de kodolarak `ConfigureKestrel` yapılandırmak `IWebHostBuilder` `Program` için, sınıftaki yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d45d-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="5d45d-180">Yine, dosyanın parolasını `.pfx` sakladığınızdan ve güvenli bir yapılandırma kaynağından aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="5d45d-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d45d-181">[Önceki](grpc-in-production.md)
>[Sonraki](docker.md)</span><span class="sxs-lookup"><span data-stu-id="5d45d-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
