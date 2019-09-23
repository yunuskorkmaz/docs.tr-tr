---
title: Self-hosted gRPC uygulamaları-WCF geliştiricileri için gRPC
description: ASP.NET Core gRPC uygulamalarını self-hosted Hizmetleri olarak dağıtma.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1269137b58f4d25f407a6a04327c51bc9f069c1b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184108"
---
# <a name="self-hosted-grpc-applications"></a>Şirket içinde barındırılan gRPC uygulamaları

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Core 3,0 uygulamaları Windows Server 'da IIS 'de barındırılamasa da, HTTP/2 işlevselliğinin bazıları henüz desteklenmediğinden, şu anda IIS 'de bir gRPC uygulaması barındırılamaz. Bu işlevsellik, gelecekteki bir Windows Server güncelleştirmesinde beklenmektedir.

.NET Core 3,0 barındırma uzantılarında bazı yeni özellikler sayesinde uygulamanızı Windows hizmeti olarak veya [systemd](https://en.wikipedia.org/wiki/Systemd)tarafından denetlenen bir Linux hizmeti olarak çalıştırabilirsiniz.

## <a name="run-your-app-as-a-windows-service"></a>Uygulamanızı bir Windows hizmeti olarak çalıştırma

ASP.NET Core uygulamanızı bir Windows hizmeti olarak çalışacak şekilde yapılandırmak için, NuGet 'den [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) paketini yüklersiniz. Sonra ' de `UseWindowsService` `CreateHostBuilder` yönteminebirçağrıekleyin`Program.cs`.

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
> Uygulama bir Windows hizmeti olarak çalışmıyorsa, `UseWindowsService` yöntem hiçbir şey yapmaz.

Şimdi, Visual Studio 'dan projeye sağ tıklayıp bağlam menüsünden *Yayımla* ' yı seçerek veya .NET Core CLI uygulamanızı yayımlayın.

Bir .NET Core uygulaması yayımladığınızda, *çerçeveye bağımlı* bir dağıtım veya *kendi kendine dahil* edilen bir dağıtım oluşturmayı tercih edebilirsiniz. Çerçeveye bağımlı dağıtımlar, çalıştırıldıkları konakta .NET Core paylaşılan çalışma zamanının yüklenmesini gerektirir. Kendi içindeki dağıtımlar, .NET Core çalışma zamanının ve çerçevesinin tam kopyasıyla yayımlanır ve herhangi bir konakta çalıştırılabilir. Her yaklaşımın avantajları ve dezavantajları dahil daha fazla bilgi için [.NET Core uygulama dağıtım](https://docs.microsoft.com/dotnet/core/deploying/) belgelerine bakın.

.NET Core 3,0 çalışma zamanının konakta yüklü olmasını gerektirmeyen uygulamanın kendi kendine dahil edilmiş bir derlemesini yayımlamak için, `-r` (veya `--runtime`) bayrağını kullanarak uygulamaya dahil edilecek çalışma zamanını belirtin.

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

Çerçeveye bağımlı bir yapı yayımlamak için `-r` bayrağını atlayın.

```console
dotnet publish -c Release -o ./publish
```

`publish` Dizinin tüm içeriğini bir yükleme klasörüne kopyalayın ve bir yürütülebilir dosya için Windows hizmeti oluşturmak üzere [sc yardımcı programını](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) kullanın.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>Windows olay günlüğü 'ne Kaydet

Yöntemi `UseWindowsService` , Windows olay günlüğüne günlük iletilerini yazan bir [günlüğe kaydetme](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) sağlayıcısını otomatik olarak ekler. Veya diğer yapılandırma kaynağı `EventLog` `Logging` bölümüne bir giriş ekleyerek bu sağlayıcının günlüğünü yapılandırabilirsiniz. `appsettings.json` Olay günlüğünde kullanılan kaynak adı, bu ayarlarda bir `SourceName` özellik ayarlanarak geçersiz kılınabilir; bir ad belirtmezseniz, varsayılan uygulama adı (normalde yürütülebilir derleme adı) kullanılacaktır.

Günlüğe kaydetme hakkında daha fazla bilgi bu bölümün sonunda yer alır.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Uygulamanızı systemd ile Linux hizmeti olarak çalıştırma

ASP.NET Core uygulamanızı bir Linux hizmeti olarak çalışacak şekilde yapılandırmak için (veya Linux paranın *arka plan programı* ), NuGet 'den [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) paketini yüklersiniz. Sonra ' de `UseSystemd` `CreateHostBuilder` yönteminebirçağrıekleyin`Program.cs`.

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

Şimdi, Visual Studio 'dan projeye sağ tıklayıp bağlam menüsünden *Yayımla* ' yı seçerek veya .net ' den, uygulamanızı (Framework `linux-x64`'e bağımlı veya ilgili Linux çalışma zamanı için bağımsız) yayımlayın. Aşağıdaki komutu kullanarak çekirdek CLı.

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

`publish` Dizinin tüm içeriğini Linux ana bilgisayarındaki bir yükleme klasörüne kopyalayın. Hizmeti kaydettirmek, `/etc/systemd/system` dizine eklenmek üzere "birim dosyası" olarak adlandırılan özel bir dosya gerektirir. Bu klasörde bir dosya oluşturmak için kök izninizin olması gerekir. Dosyayı kullanmak istediğiniz tanımlayıcıya `systemd` `.service` ve uzantıyı adlandırın. Örneğin, uygulamasında yönetilen Hyper-V konakları olarak eklemek için aşağıdaki yordamı kullanabilirsiniz.

Hizmet dosyası, bu örnekte gösterildiği gibi ıNı biçimini kullanır.

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

Özelliği, uygulamanın bu uygulamayı başlatma ve kapatmayla bilgilendirmeyeceğini söyler `systemd`. `Type=notify` Bu `WantedBy=multi-user.target` ayar, Linux sistemi "Runlevel 2" değerine ulaştığında hizmetin başlatılmasına neden olur, yani grafik olmayan bir çok kullanıcılı kabuk etkin olur.

Hizmeti `systemd` tanıyamadan önce, yapılandırmasını yeniden yüklemesi gerekir. Komutunu kullanarak kontrol `systemd`edersiniz. `systemctl` Yeniden yükledikten sonra, uygulamanın `status` başarıyla kaydedildiğini doğrulamak için alt komutunu kullanın.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Hizmeti doğru şekilde yapılandırdıysanız aşağıdaki çıktı gösterilir:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Hizmeti başlatmak için komutunu kullanın. `start`

```console
sudo systemctl start myapp.service
```

> [!TIP]
> Uzantı `.service` , kullanılırken `systemctl start`isteğe bağlıdır.

Hizmeti sistem `systemd` başlangıcında otomatik olarak başlatmaya söylemek için `enable` komutunu kullanın.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Journald 'de günlüğe kaydet

Windows olay günlüğü `journald`'nün Linux eşdeğeri, bir `systemd`parçası olan yapılandırılmış bir günlük sistem hizmetidir. Bir Linux Daemon tarafından standart çıktıya yazılan günlük iletileri otomatik olarak öğesine `journald`yazılır, bu nedenle günlüğe kaydetme düzeylerini yapılandırmak için günlük yapılandırmasının `Console` bölümünü kullanın. `UseSystemd` Konak Oluşturucu yöntemi, konsol çıkış biçimini otomatik olarak günlüğe uyacak şekilde yapılandırır.

, Linux günlükleri için standart olduğundan, bununla tümleştirilen çeşitli araçlar vardır ve `journald` günlükleri bir dış günlük sistemine kolayca yönlendirebilirsiniz. `journald` Yerel olarak konakta çalışırken komut satırından günlükleri görüntülemek için `journalctl` komutunu kullanabilirsiniz.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Ana bilgisayarınızda kullanılabilir bir GUI ortamınız varsa, Linux için *Qjournalctl* ve *GNOME günlükleri*gibi birkaç grafik günlük görüntüleyicileri vardır.

İle `journalctl`komut satırından systemd günlüğünü sorgulama hakkında daha fazla bilgi edinmek için, [Man sayfalarına](https://manpages.debian.org/buster/systemd/journalctl.1)bakın.

## <a name="https-certificates-for-self-hosted-applications"></a>Şirket içinde barındırılan uygulamalar için HTTPS sertifikaları

Bir gRPC uygulamasını üretimde çalıştırırken, güvenilir bir sertifika yetkilisinden (CA) bir TLS sertifikası kullanmanız gerekir. Bu CA, genel bir CA veya kuruluşunuz için bir dahili olabilir.

Windows konakları üzerinde, sertifika, [X509Store sınıfı](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0)kullanılarak güvenli bir [sertifika deposundan](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) yüklenebilir. `X509Store` Sınıfı, bazı Linux konaklarındaki OpenSSL anahtar deposu ile de kullanılabilir.

Sertifikalar, bir dosyadan ( [Örneğin, güçlü](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0)bir parolayla korunan bir `.pfx` dosya) veya Azure Key Vault gibi güvenli bir depolama hizmetinden alınan ikili verilerden biri kullanılarak da oluşturulabilir. [ ](https://azure.microsoft.com/services/key-vault/).

Kestrel, bir sertifikayı iki şekilde kullanacak şekilde yapılandırılabilir: yapılandırmadan veya kodda.

### <a name="set-https-certificates-using-configuration"></a>Yapılandırma kullanarak HTTPS sertifikaları ayarlama

Yapılandırma yaklaşımı, Kestrel yapılandırma bölümünde sertifika `.pfx` dosyası yolunu ve parolayı ayarlamayı gerektirir. Bu `appsettings.json` , içinde olduğu gibi görünür.

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

Parolanın Azure Keykasası veya HashiCorp kasası gibi güvenli bir yapılandırma kaynağı kullanılarak sağlanması gerekir.

Şifrelenmemiş parolaları yapılandırma dosyalarında depolamamalısınız.

### <a name="set-https-certificates-in-code"></a>Kodda HTTPS sertifikaları ayarlama

Kodda https 'yi yapılandırmak için, `ConfigureKestrel` `Program` sınıfındaki `IWebHostBuilder` içindeki yöntemi kullanın.

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

Yine, `.pfx` dosyanın parolasının ' de depolanması ve güvenli bir yapılandırma kaynağından alınması gerekir.

>[!div class="step-by-step"]
>[Önceki](grpc-in-production.md)
>[İleri](docker.md)
