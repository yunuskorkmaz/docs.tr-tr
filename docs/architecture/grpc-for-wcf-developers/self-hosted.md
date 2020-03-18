---
title: Kendi kendine barındırılan gRPC uygulamaları - WCF geliştiricileri için gRPC
description: Core gRPC uygulamalarını kendi kendine barındırılan hizmetler olarak ASP.NET dağıtma.
ms.date: 09/02/2019
ms.openlocfilehash: 00fb1453e19a02469f80af79672e0c1f72c7280f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147808"
---
# <a name="self-hosted-grpc-applications"></a>Kendi kendine barındırılan gRPC uygulamaları

ASP.NET Core 3.0 uygulamaları Windows Server'da IIS'de barındırılabilse de, şu anda HTTP/2 işlevlerinin bazıları desteklenmediği için IIS'de bir gRPC uygulamasını barındırmak mümkün değildir. Bu işlev, Windows Server için gelecekteki bir güncelleştirme için bir hedeftir.

Uygulamanızı bir Windows hizmeti olarak çalıştırabilirsiniz. Ya da .NET Core 3.0 barındırma uzantılarındaki yeni özellikler nedeniyle [sistemli](https://en.wikipedia.org/wiki/Systemd)tarafından kontrol edilen bir Linux hizmeti olarak çalıştırabilirsiniz.

## <a name="run-your-app-as-a-windows-service"></a>Uygulamanızı Windows hizmeti olarak çalıştırın

ASP.NET Core uygulamanızı Windows hizmeti olarak çalışacak şekilde yapılandırmak için NuGet'den [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) paketini yükleyin. Sonra `UseWindowsService` `CreateHostBuilder` yönteme bir çağrı `Program.cs`ekleyin.

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
> Uygulama Windows hizmeti olarak çalışmıyorsa, `UseWindowsService` yöntem hiçbir şey yapmaz.

Şimdi bu yöntemlerden birini kullanarak uygulamanızı yayımlayın:

* Visual Studio'dan projeyi sağ tıklayarak **Publish** ve kısayol menüsünde Yayınla'yı seçerek.
* .NET Çekirdek CLI'den.

Bir .NET Core uygulaması yayımladığınızda, *çerçeveye bağımlı* bir dağıtım veya *bağımsız* bir dağıtım oluşturmayı seçebilirsiniz. Çerçeveye bağımlı dağıtımlar, .NET Core Paylaşılan Çalışma Zamanı'nın çalıştırıldıkları ana bilgisayara yüklenmesini gerektirir. Bağımsız dağıtımlar .NET Core çalışma zamanı nın ve çerçevesinin tam bir kopyasıyla yayımlanır ve herhangi bir ana bilgisayarda çalıştırılabilir. Her yaklaşımın avantajları ve dezavantajları da dahil olmak üzere daha fazla bilgi için [.NET Core uygulama dağıtım](../../core/deploying/index.md) belgelerine bakın.

.NET Core 3.0 çalışma zamanının ana bilgisayara yüklenmesini gerektirmeyen uygulamanın bağımsız bir yapısını yayımlamak için, uygulamaya eklenecek çalışma saatini belirtin. `-r` (veya) `--runtime`bayrağı kullanın.

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Çerçeveye bağımlı bir yapı yayımlamak `-r` için bayrağı atlayın.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Dizinin tüm içeriğini `publish` yükleme klasörüne kopyalayın. Ardından, yürütülebilir dosya için bir Windows hizmeti oluşturmak için [sc aracını](/windows/desktop/services/controlling-a-service-using-sc) kullanın.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Windows etkinlik günlüğüne oturum açma

Yöntem, `UseWindowsService` Windows olay günlüğüne günlük iletileri yazan bir [günlük](/aspnet/core/fundamentals/logging/) sağlayıcısını otomatik olarak ekler. Bu sağlayıcı nın `EventLog` `Logging` bölümüne `appsettings.json` veya başka bir yapılandırma kaynağına bir giriş ekleyerek günlük işlemlerini yapılandırabilirsiniz.

Bu ayarlarda bir `SourceName` özellik ayarlayarak olay günlüğünde kullanılan kaynak adı geçersiz kılabilirsiniz. Bir ad belirtmezseniz, varsayılan uygulama adı (normalde çalıştırılabilir derleme adı) kullanılır.

Günlük hakkında daha fazla bilgi bu bölümün sonunda dır.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Uygulamanızı systemd ile linux hizmeti olarak çalıştırın

ASP.NET Core uygulamanızı Linux hizmeti (veya Linux dilinde *daemon)* olarak çalışacak şekilde yapılandırmak için, [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) paketini NuGet'den yükleyin. Sonra `UseSystemd` `CreateHostBuilder` yönteme bir çağrı `Program.cs`ekleyin.

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
> Uygulama bir Linux hizmeti olarak çalışmıyorsa, `UseSystemd` yöntem hiçbir şey yapmaz.

Şimdi başvurunuzu yayınlayın. Uygulama, ilgili Linux çalışma süresi için çerçeveye bağımlı veya bağımsız `linux-x64`olabilir (örneğin, ). Şu yöntemlerden birini kullanarak yayımlayabilirsiniz:

* Visual Studio'dan projeyi sağ tıklayarak **Publish** ve kısayol menüsünde Yayınla'yı seçerek.
* .NET Core CLI'den aşağıdaki komutu kullanarak:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
`publish` Dizinin tüm içeriğini Linux ana bilgisayarındaki bir yükleme klasörüne kopyalayın. Hizmetin kaydedilmesi, `/etc/systemd/system` dizine eklenecek birim dosyası adı verilen özel bir *dosya*gerektirir. Bu klasörde bir dosya oluşturmak için kök iznine ihtiyacınız olur. Kullanmak istediğiniz `systemd` tanımlayıcıve uzantı ile dosyayı `.service` adlandırın. Örneğin, kullanın. `/etc/systemd/system/myapp.service`

Hizmet dosyası, bu örnekte gösterildiği gibi INI biçimini kullanır:

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

Özellik, `Type=notify` `systemd` uygulamanın başlangıç ve kapatma konusunda bunu bildireceğini söyler. Ayar, `WantedBy=multi-user.target` Linux sistemi "runlevel 2"ye ulaştığında hizmetin başlamasına neden olur, bu da grafiksel olmayan çok kullanıcılı bir kabuğun etkin olduğu anlamına gelir.

Hizmeti `systemd` tanımadan önce yapılandırmasını yeniden yüklemesi gerekir. Komutu `systemd` kullanarak `systemctl` kontrol edin. Yeniden yüklendikten sonra, uygulamanın `status` başarıyla kaydolduğunu doğrulamak için alt komutu kullanın.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Hizmeti doğru şekilde yapılandırmışsanız, aşağıdaki çıktıyı alırsınız:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Hizmeti `start` başlatmak için komutu kullanın.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> Uzantısı `.service` kullanırken `systemctl start`isteğe bağlıdır.

Hizmeti `systemd` sistem başlatmada otomatik olarak başlatmayı `enable` söylemek için komutu kullanın.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Günlük olarak günlük olarak oturum aç

Windows olay günlüğülinux eşdeğer `journald`, bir parçası olan yapılandırılmış bir `systemd`günlük sistemi hizmetidir. Bir Linux daemon tarafından standart çıktıya yazılan günlük `journald`iletileri otomatik olarak . Günlüğe kaydetme düzeylerini yapılandırmak için günlüğe kaydetme yapılandırmabölümünü kullanın. `Console` Ana `UseSystemd` bilgisayar oluşturucu yöntemi, konsol çıktı biçimini günlük le eşecek şekilde otomatik olarak yapılandırır.

Linux `journald` günlükleri için standart olduğundan, çeşitli araçlar onunla entegre. Günlükleri `journald` harici bir günlük sistemine kolayca yönlendirebilirsiniz. Ana bilgisayar üzerinde yerel olarak çalışırken, komut satırından günlükleri görüntülemek için `journalctl` komutu kullanabilirsiniz.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Ev sahibinizde bir GUI ortamı varsa, Linux için *QJournalctl* ve *gnome günlükleri*gibi birkaç grafik günlük görüntüleyen kullanılabilir.

`systemd` Kullanarak komut satırından günlüğü sorgulama hakkında daha `journalctl`fazla bilgi edinmek için, [adam sayfalarına](https://manpages.debian.org/buster/systemd/journalctl.1)bakın.

## <a name="https-certificates-for-self-hosted-applications"></a>Kendi barındırılan uygulamalar için HTTPS sertifikaları

Üretimde bir gRPC uygulaması çalıştırıyorsanız, güvenilir bir sertifika yetkilisinden (CA) bir TLS sertifikası kullanmanız gerekir. Bu CA herkese açık bir CA veya kuruluşunuz için dahili bir CA olabilir.

Windows ana bilgisayarlarında, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıfı kullanarak sertifikayı güvenli bir sertifika [deposundan](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) yükleyebilirsiniz. Sınıfı, bazı `X509Store` Linux ana bilgisayarlarında OpenSSL anahtar deposu ile de kullanabilirsiniz.

[X509Certificate2 oluşturucularından](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)birini kullanarak da sertifika lar oluşturabilirsiniz:

* Güçlü bir parolayla `.pfx` korunan dosya gibi bir dosya
* [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) gibi güvenli bir depolama hizmetinden alınan ikili veriler

Kestrel'i bir sertifikayı yapılandırmadan veya kodda olmak üzere iki şekilde kullanacak şekilde yapılandırabilirsiniz.

### <a name="set-https-certificates-by-using-configuration"></a>Yapılandırmayı kullanarak HTTPS sertifikalarını ayarlama

Yapılandırma yaklaşımı, Kestrel yapılandırma `.pfx` bölümünde sertifika dosyasına ve parolaya giden yolu ayarlamayı gerektirir. In `appsettings.json`, bu gibi görünür:

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

Parolayı Azure Key Vault veya Hashicorp Vault gibi güvenli bir yapılandırma kaynağı kullanarak sağlayın.

> [!IMPORTANT]
> Şifrelenmemiş parolaları yapılandırma dosyalarında saklamayın.

### <a name="set-https-certificates-in-code"></a>HTTPS sertifikalarını kodda ayarlama

Https'yi Kerkenez'de kodolarak `ConfigureKestrel` yapılandırmak `IWebHostBuilder` `Program` için, sınıftaki yöntemi kullanın.

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

Yine, dosyanın parolasını `.pfx` sakladığınızdan ve güvenli bir yapılandırma kaynağından aldığından emin olun.

>[!div class="step-by-step"]
>[Önceki](grpc-in-production.md)
>[Sonraki](docker.md)
