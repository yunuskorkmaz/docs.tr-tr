---
title: Self-hosted gRPC uygulamaları-WCF geliştiricileri için gRPC
description: ASP.NET Core gRPC uygulamalarını self-hosted Hizmetleri olarak dağıtma.
ms.date: 12/15/2020
ms.openlocfilehash: a5e2316b8d76593f4eb53760d2609b5bbbc9d2c5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938539"
---
# <a name="self-hosted-grpc-applications"></a>Şirket içinde barındırılan gRPC uygulamaları

ASP.NET Core 5,0 uygulamaları Windows Server 'da IIS 'de barındırılamasa da, HTTP/2 işlevselliğinin bazıları desteklenmediğinden, şu anda IIS 'de bir gRPC uygulaması barındırılamaz. Bu işlevsellik, gelecekteki bir Windows Server güncelleştirmesi için bir hedeftir.

Uygulamanızı bir Windows hizmeti olarak çalıştırabilirsiniz. Veya .NET 5,0 barındırma uzantılarında yeni özellikler nedeniyle bu hizmeti [systemd](https://en.wikipedia.org/wiki/Systemd)tarafından denetlenen bir Linux hizmeti olarak çalıştırabilirsiniz.

## <a name="run-your-app-as-a-windows-service"></a>Uygulamanızı bir Windows hizmeti olarak çalıştırma

ASP.NET Core uygulamanızı bir Windows hizmeti olarak çalışacak şekilde yapılandırmak için, NuGet 'den [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) paketini yüklersiniz. Sonra `UseWindowsService` ' de yöntemine bir çağrı ekleyin `CreateHostBuilder` `Program.cs` .

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
> Uygulama bir Windows hizmeti olarak çalışmıyorsa, `UseWindowsService` Yöntem hiçbir şey yapmaz.

Şimdi aşağıdaki yöntemlerden birini kullanarak uygulamanızı yayımlayın:

* Visual Studio 'dan projeye sağ tıklayıp kısayol menüsünde **Yayımla** ' yı seçin.
* .NET CLı 'dan.

Bir .NET uygulaması yayımladığınızda, *çerçeveye bağımlı* bir dağıtım veya *kendi kendine dahil* edilen bir dağıtım oluşturmayı tercih edebilirsiniz. Çerçeveye bağımlı dağıtımlar, çalıştırıldıkları konakta .NET paylaşılan çalışma zamanının yüklenmesini gerektirir. Kendi içindeki dağıtımlar, .NET çalışma zamanının ve çerçevesinin tam kopyasıyla yayımlanır ve herhangi bir konakta çalıştırılabilir. Her yaklaşımın avantajları ve dezavantajları dahil daha fazla bilgi için bkz. [.NET uygulama dağıtımı](../../core/deploying/index.md) belgeleri.

.NET 5,0 çalışma zamanının konakta yüklü olmasını gerektirmeyen uygulamanın kendi içindeki bir derlemesini yayımlamak için, uygulamaya dahil edilecek çalışma zamanını belirtin. `-r`(Veya `--runtime` ) bayrağını kullanın.

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Çerçeveye bağımlı bir yapı yayımlamak için `-r` bayrağını atlayın.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Dizinin tüm içeriğini `publish` bir yükleme klasörüne kopyalayın. Ardından, bir yürütülebilir dosya için bir Windows hizmeti oluşturmak üzere [SC aracını](/windows/desktop/services/controlling-a-service-using-sc) kullanın.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Windows olay günlüğü 'ne Kaydet

`UseWindowsService`Yöntemi, Windows olay günlüğüne günlük iletilerini yazan bir [günlüğe kaydetme](/aspnet/core/fundamentals/logging/) sağlayıcısını otomatik olarak ekler. `EventLog` `Logging` `appsettings.json` Veya başka bir yapılandırma kaynağı bölümüne bir giriş ekleyerek bu sağlayıcının günlüğünü yapılandırabilirsiniz.

Bu ayarlarda bir özelliği ayarlayarak olay günlüğünde kullanılan kaynak adını geçersiz kılabilirsiniz `SourceName` . Bir ad belirtmezseniz, varsayılan uygulama adı (normalde yürütülebilir derleme adı) kullanılacaktır.

Günlüğe kaydetme hakkında daha fazla bilgi bu bölümün sonunda yer alır.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Uygulamanızı systemd ile Linux hizmeti olarak çalıştırma

ASP.NET Core uygulamanızı bir Linux hizmeti olarak çalışacak şekilde yapılandırmak için (veya Linux par, *arka plan programı* ), NuGet 'den [Microsoft.Extensions.Hosting.Systemtıd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) paketini yüklersiniz. Sonra `UseSystemd` ' de yöntemine bir çağrı ekleyin `CreateHostBuilder` `Program.cs` .

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
> Uygulama bir Linux hizmeti olarak çalışmıyorsa, `UseSystemd` Yöntem hiçbir şey yapmaz.

Şimdi uygulamanızı yayımlayın. Uygulama, ilgili Linux çalışma zamanı (örneğin,) için çerçeve bağımlı ya da kendi kendine dahil olabilir `linux-x64` . Aşağıdaki yöntemlerden birini kullanarak yayımlayabilirsiniz:

* Visual Studio 'dan projeye sağ tıklayıp kısayol menüsünde **Yayımla** ' yı seçin.
* Aşağıdaki komutu kullanarak .NET CLı 'dan:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
Dizinin tüm içeriğini `publish` Linux ana bilgisayarındaki bir yükleme klasörüne kopyalayın. Hizmeti kaydettirmek, dizine eklenmek üzere *birim dosyası* olarak adlandırılan özel bir dosya gerektirir `/etc/systemd/system` . Bu klasörde bir dosya oluşturmak için kök izninizin olması gerekir. Dosyayı kullanmak istediğiniz tanımlayıcıya `systemd` ve `.service` uzantıyı adlandırın. Örneğin, kullanın `/etc/systemd/system/myapp.service` .

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

`Type=notify`Özelliği `systemd` , uygulamanın bu uygulamayı başlatma ve kapatmayla bilgilendirmeyeceğini söyler. `WantedBy=multi-user.target`Bu ayar, Linux sistemi "Runlevel 2" değerine ulaştığında hizmetin başlatılmasına neden olur. Bu, grafik olmayan, çok kullanıcılı bir kabuğun etkin olduğu anlamına gelir.

`systemd`Hizmeti tanıyamadan önce, yapılandırmasını yeniden yüklemesi gerekir. `systemd`Komutunu kullanarak kontrol edersiniz `systemctl` . Yeniden yükledikten sonra, `status` uygulamanın başarıyla kaydedildiğini doğrulamak için alt komutunu kullanın.

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

`start`Hizmeti başlatmak için komutunu kullanın.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> `.service`Uzantı, kullanırken isteğe bağlıdır `systemctl start` .

`systemd`Hizmeti sistem başlangıcında otomatik olarak başlatmaya söylemek için `enable` komutunu kullanın.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Journald 'de günlüğe kaydet

Windows olay günlüğü 'nün Linux eşdeğeri `journald` , uygulamasının bir parçası olan yapılandırılmış bir günlük sistem hizmetidir `systemd` . Bir Linux Daemon tarafından standart çıktıya yazılan günlük iletileri otomatik olarak üzerine yazılır `journald` . Günlüğe kaydetme düzeylerini yapılandırmak için `Console` günlük yapılandırmasının bölümünü kullanın. `UseSystemd`Konak Oluşturucu yöntemi, konsol çıkış biçimini otomatik olarak günlüğe uyacak şekilde yapılandırır.

`journald`, Linux günlükleri için standart olduğundan, çeşitli araçlar onunla tümleştirilir. Günlükleri `journald` bir dış günlük sistemine kolayca yönlendirebilirsiniz. Yerel olarak konakta çalışırken komut `journalctl` satırından günlükleri görüntülemek için komutunu kullanabilirsiniz.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Ana bilgisayarınızda kullanılabilir bir GUI ortamınız varsa, Linux için *Qjournalctl* ve *GNOME günlükleri* gibi birkaç grafik günlük görüntüleyicileri vardır.

Kullanarak komut satırından günlüğü sorgulama hakkında daha fazla bilgi için `systemd` `journalctl` , bkz. [manpages](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Şirket içinde barındırılan uygulamalar için HTTPS sertifikaları

Üretimde bir gRPC uygulaması çalıştırırken, güvenilir bir sertifika yetkilisinden (CA) bir TLS sertifikası kullanmanız gerekir. Bu CA, bir genel CA veya kuruluşunuz için bir dahili olabilir.

Windows Konakları ' nde, sınıfını kullanarak güvenli bir [sertifika deposundan](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sertifikayı yükleyebilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509Store> . `X509Store`Sınıfını, bazı Linux konaklarındaki OpenSSL anahtar deposu ile de kullanabilirsiniz.

Ayrıca, [X509Certificate2 oluşturucularından](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)birini kullanarak da sertifikalar oluşturabilirsiniz:

* `.pfx`Güçlü bir parola ile korunan dosya gibi bir dosya
* [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) gibi güvenli bir depolama hizmetinden alınan ikili veriler

Kestrel 'yi bir sertifikayı kullanmak için iki şekilde yapılandırabilirsiniz: yapılandırmadan veya koddan.

### <a name="set-https-certificates-by-using-configuration"></a>HTTPS sertifikalarını yapılandırma kullanarak ayarlama

Yapılandırma yaklaşımı, `.pfx` Kestrel yapılandırma bölümünde sertifika dosyası yolunu ve parolayı ayarlamayı gerektirir. `appsettings.json`' De, bu şöyle görünür:

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

Kodda HTTPS 'yi yapılandırmak için, `ConfigureKestrel` `IWebHostBuilder` sınıfındaki içindeki yöntemi kullanın `Program` .

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

Bu durumda, dosyanın parolasını içinde depoladığınızdan `.pfx` ve güvenli bir yapılandırma kaynağından geri aldığınızdan emin olun.

>[!div class="step-by-step"]
>[Önceki](grpc-in-production.md) 
> [Sonraki](docker.md)
