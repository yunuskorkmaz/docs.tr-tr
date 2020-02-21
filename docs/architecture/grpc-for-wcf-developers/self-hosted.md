---
title: Self-hosted gRPC uygulamaları-WCF geliştiricileri için gRPC
description: ASP.NET Core gRPC uygulamalarını self-hosted Hizmetleri olarak dağıtma.
ms.date: 09/02/2019
ms.openlocfilehash: ee370ba1893b060505b38ddf84235bd84433ad32
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542995"
---
# <a name="self-hosted-grpc-applications"></a>Şirket içinde barındırılan gRPC uygulamaları

ASP.NET Core 3,0 uygulamaları Windows Server 'da IIS 'de barındırılamasa da, HTTP/2 işlevselliğinin bazıları desteklenmediğinden, şu anda IIS 'de bir gRPC uygulaması barındırılamaz. Bu işlevsellik, gelecekteki bir Windows Server güncelleştirmesi için bir hedeftir.

Uygulamanızı bir Windows hizmeti olarak çalıştırabilirsiniz. Veya .NET Core 3,0 barındırma uzantılarında yeni özellikler nedeniyle bu hizmeti [systemd](https://en.wikipedia.org/wiki/Systemd)tarafından denetlenen bir Linux hizmeti olarak çalıştırabilirsiniz.

## <a name="run-your-app-as-a-windows-service"></a>Uygulamanızı bir Windows hizmeti olarak çalıştırma

ASP.NET Core uygulamanızı bir Windows hizmeti olarak çalışacak şekilde yapılandırmak için, NuGet 'den [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) paketini yüklersiniz. Ardından, `Program.cs``CreateHostBuilder` yöntemine `UseWindowsService` bir çağrı ekleyin.

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
> Uygulama bir Windows hizmeti olarak çalışmıyorsa `UseWindowsService` yöntemi hiçbir şey yapmaz.

Şimdi aşağıdaki yöntemlerden birini kullanarak uygulamanızı yayımlayın:

* Visual Studio 'dan projeye sağ tıklayıp kısayol menüsünde **Yayımla** ' yı seçin.
* .NET Core CLI.

Bir .NET Core uygulaması yayımladığınızda, *çerçeveye bağımlı* bir dağıtım veya *kendi kendine dahil* edilen bir dağıtım oluşturmayı tercih edebilirsiniz. Çerçeveye bağımlı dağıtımlar, çalıştırıldıkları konakta .NET Core paylaşılan çalışma zamanının yüklenmesini gerektirir. Kendi içindeki dağıtımlar, .NET Core çalışma zamanının ve çerçevesinin tam kopyasıyla yayımlanır ve herhangi bir konakta çalıştırılabilir. Her yaklaşımın avantajları ve dezavantajları dahil daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../../core/deploying/index.md) belgeleri.

.NET Core 3,0 çalışma zamanının konakta yüklü olmasını gerektirmeyen uygulamanın kendi içindeki bir derlemesini yayımlamak için, uygulamaya dahil edilecek çalışma zamanını belirtin. `-r` (veya `--runtime`) bayrağını kullanın.

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Çerçeveye bağımlı bir yapı yayımlamak için `-r` bayrağını atlayın.

```dotnetcli
dotnet publish -c Release -o ./publish
```

`publish` dizininin tüm içeriğini bir yükleme klasörüne kopyalayın. Ardından, bir yürütülebilir dosya için bir Windows hizmeti oluşturmak üzere [SC aracını](/windows/desktop/services/controlling-a-service-using-sc) kullanın.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Windows olay günlüğü 'ne Kaydet

`UseWindowsService` yöntemi, Windows olay günlüğüne günlük iletilerini yazan bir [günlüğe kaydetme](/aspnet/core/fundamentals/logging/) sağlayıcısını otomatik olarak ekler. `appsettings.json` ya da başka bir yapılandırma kaynağının `Logging` bölümüne bir `EventLog` girişi ekleyerek bu sağlayıcının günlüğünü yapılandırabilirsiniz. 

Bu ayarlarda bir `SourceName` özelliğini ayarlayarak olay günlüğünde kullanılan kaynak adını geçersiz kılabilirsiniz. Bir ad belirtmezseniz, varsayılan uygulama adı (normalde yürütülebilir derleme adı) kullanılacaktır.

Günlüğe kaydetme hakkında daha fazla bilgi bu bölümün sonunda yer alır.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Uygulamanızı systemd ile Linux hizmeti olarak çalıştırma

ASP.NET Core uygulamanızı bir Linux hizmeti olarak çalışacak şekilde yapılandırmak için (veya Linux paranın *arka plan programı* ), NuGet 'den [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) paketini yüklersiniz. Ardından, `Program.cs``CreateHostBuilder` yöntemine `UseSystemd` bir çağrı ekleyin.

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
> Uygulama bir Linux hizmeti olarak çalışmıyorsa `UseSystemd` yöntemi hiçbir şey yapmaz.

Şimdi uygulamanızı yayımlayın. Uygulama, ilgili Linux çalışma zamanı (örneğin, `linux-x64`) için çerçeve bağımlı veya kendi kendine dahil olabilir. Aşağıdaki yöntemlerden birini kullanarak yayımlayabilirsiniz:

* Visual Studio 'dan projeye sağ tıklayıp kısayol menüsünde **Yayımla** ' yı seçin. 
* .NET Core CLI, aşağıdaki komutu kullanarak:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
`publish` dizininin tüm içeriğini Linux ana bilgisayarındaki bir yükleme klasörüne kopyalayın. Hizmeti kaydettirmek, `/etc/systemd/system` dizinine eklenmek üzere *birim dosyası*olarak adlandırılan özel bir dosya gerektirir. Bu klasörde bir dosya oluşturmak için kök izninizin olması gerekir. `systemd` kullanmak istediğiniz tanımlayıcıyı ve `.service` uzantısını adlandırın. Örneğin, `/etc/systemd/system/myapp.service`kullanın.

Hizmet dosyası, aşağıdaki örnekte gösterildiği gibi ıNı biçimini kullanır:

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

`Type=notify` özelliği, uygulamanın başlatma ve kapatmayla haberdar olacağını `systemd` söyler. `WantedBy=multi-user.target` ayarı, Linux sistemi "Runlevel 2" değerine ulaştığında hizmetin başlatılmasına neden olur. Bu, grafik olmayan bir çok kullanıcılı kabuğun etkin olduğu anlamına gelir.

`systemd`, hizmeti tanıyamadan önce, yapılandırmasını yeniden yüklemesi gerekir. `systemctl` komutunu kullanarak `systemd` denetlersiniz. Yeniden yüklendikten sonra, uygulamanın başarıyla kaydedildiğini doğrulamak için `status` alt komutunu kullanın.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Hizmeti doğru şekilde yapılandırdıysanız aşağıdaki çıktıyı alırsınız:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Hizmeti başlatmak için `start` komutunu kullanın.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> `systemctl start`kullandığınızda `.service` uzantısı isteğe bağlıdır.

`systemd` sistem başlangıcında hizmeti otomatik olarak başlatmasını söylemek için `enable` komutunu kullanın.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Journald 'de günlüğe kaydet

Windows olay günlüğü 'nün Linux eşdeğeri, `systemd`bir parçası olan yapılandırılmış bir günlük sistem hizmetidir `journald`. Bir Linux Daemon tarafından standart çıktıya yazılan günlük iletileri `journald`otomatik olarak yazılır. Günlüğe kaydetme düzeylerini yapılandırmak için, günlük yapılandırmasının `Console` bölümünü kullanın. `UseSystemd` ana bilgisayar Oluşturucu yöntemi, konsol çıkış biçimini otomatik olarak günlüğe uyacak şekilde yapılandırır.

`journald`, Linux günlükleri için standart olduğundan, çeşitli araçlar onunla tümleştirilir. Günlükleri `journald` bir dış günlük sistemine kolayca yönlendirebilirsiniz. Konakta yerel olarak çalışarak, komut satırından günlükleri görüntülemek için `journalctl` komutunu kullanabilirsiniz.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Ana bilgisayarınızda kullanılabilir bir GUI ortamınız varsa, Linux için *Qjournalctl* ve *GNOME günlükleri*gibi birkaç grafik günlük görüntüleyicileri vardır.

`journalctl`kullanarak komut satırından `systemd` günlüğünü sorgulama hakkında daha fazla bilgi edinmek için, [adam sayfalarına](https://manpages.debian.org/buster/systemd/journalctl.1)bakın.

## <a name="https-certificates-for-self-hosted-applications"></a>Şirket içinde barındırılan uygulamalar için HTTPS sertifikaları

Üretimde bir gRPC uygulaması çalıştırırken, güvenilir bir sertifika yetkilisinden (CA) bir TLS sertifikası kullanmanız gerekir. Bu CA, bir genel CA veya kuruluşunuz için bir dahili olabilir.

Windows konakları üzerinde, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıfını kullanarak güvenli bir [sertifika deposundan](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sertifikayı yükleyebilirsiniz. `X509Store` sınıfını, bazı Linux konaklarındaki OpenSSL anahtar deposu ile de kullanabilirsiniz.

Ayrıca, [X509Certificate2 oluşturucularından](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)birini kullanarak da sertifikalar oluşturabilirsiniz:

* Güçlü bir parolayla korunan `.pfx` dosyası gibi bir dosya
* [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) gibi güvenli bir depolama hizmetinden alınan ikili veriler

Kestrel 'yi bir sertifikayı kullanmak için iki şekilde yapılandırabilirsiniz: yapılandırmadan veya koddan.

### <a name="set-https-certificates-by-using-configuration"></a>HTTPS sertifikalarını yapılandırma kullanarak ayarlama

Yapılandırma yaklaşımı, sertifika `.pfx` dosyası yolunu ve Kestrel yapılandırma bölümünde parolayı ayarlamayı gerektirir. `appsettings.json`, bu şöyle görünür:

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

Azure Key Vault veya HashiCorp kasası gibi güvenli bir yapılandırma kaynağı kullanarak parolayı girin.

> [!IMPORTANT]
> Şifrelenmemiş parolaları yapılandırma dosyalarında depolamamayın.

### <a name="set-https-certificates-in-code"></a>Kodda HTTPS sertifikaları ayarlama

Kodda HTTPS 'yi yapılandırmak için, `Program` sınıfında `IWebHostBuilder` `ConfigureKestrel` yöntemi kullanın.

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

Ayrıca, `.pfx` dosyanın parolasını içinde depoladığınızdan ve güvenli bir yapılandırma kaynağından geri aldığınızdan emin olun.

>[!div class="step-by-step"]
>[Önceki](grpc-in-production.md)
>[İleri](docker.md)
