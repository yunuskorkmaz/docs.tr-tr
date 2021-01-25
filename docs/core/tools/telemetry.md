---
title: .NET SDK telemetrisi
description: Analiz için kullanım bilgilerini toplayan .NET SDK telemetrisi özelliklerini, hangi verilerin toplandığı ve devre dışı bırakılacağını bulun.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 137b703dc9369f09fb535af40edf057e4e02117a
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757843"
---
# <a name="net-sdk-telemetry"></a>.NET SDK telemetrisi

[.NET SDK](index.md) , .net CLI kilitlenirse kullanım verilerini ve özel durum bilgilerini toplayan bir telemetri özelliği içerir. .Net CLı, .NET SDK ile birlikte gelir ve .NET uygulamalarınızı oluşturmanızı, test etmeniz ve yayımlamanıza olanak tanıyan fiiller kümesidir. .NET ekibinin, araçların iyileştirilmesi için nasıl kullanıldığını anladığından emin olmanız önemlidir. Hatalar hakkında bilgi, takımın sorunları çözmesine ve hataları düzeltmesine yardımcı olur.

Toplanan veriler, [Creative Commons Attribution Lisansı](https://creativecommons.org/licenses/by/4.0/)kapsamında toplu olarak yayımlanır.

## <a name="scope"></a>Kapsam

`dotnet` iki işleve sahiptir: uygulamaları çalıştırmak ve CLı komutlarını yürütmek için.  `dotnet` Aşağıdaki biçimde bir uygulamayı başlatmak için kullanılırken telemetri toplanmaz:

- `dotnet [path-to-app].dll`

Telemetri, [.net CLI komutlarının](index.md)herhangi biri kullanılırken *toplanır* , örneğin:

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Devre dışı bırakma

.NET SDK telemetri özelliği varsayılan olarak etkindir. Telemetri özelliğini devre dışı bırakmak için, `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenini veya olarak ayarlayın `1` `true` .

Başarılı bir yükleme gerçekleştiğinde .NET SDK yükleyicisi tarafından tek bir telemetri girişi de gönderilir. Devre dışı bırakmak için `DOTNET_CLI_TELEMETRY_OPTOUT` .NET SDK 'yı yüklemeden önce ortam değişkenini ayarlayın.

> [!IMPORTANT]
> Yükleyiciyi başlattıktan sonra devre dışı bırakmak için: yükleyiciyi kapatın, ortam değişkenini ayarlayın ve ardından yükleyiciyi bu değer kümesiyle yeniden çalıştırın.

## <a name="disclosure"></a>Savunmasız

.NET SDK, [.net CLI komutlarından](index.md) birini (örneğin,) ilk kez çalıştırdığınızda aşağıdakine benzer bir metin görüntüler `dotnet build` . Metin, çalıştırmakta olduğunuz SDK sürümüne bağlı olarak biraz farklılık gösterebilir. Bu "ilk çalıştırma" deneyimi, Microsoft 'un veri toplamayı nasıl bildisidir.

```console
Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. The data is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

Bu iletiyi ve .NET hoş geldiniz iletisini devre dışı bırakmak için `DOTNET_NOLOGO` ortam değişkenini olarak ayarlayın `true` . Bu değişkenin telemetri geri çevirme üzerinde hiçbir etkisi olmadığını unutmayın.

## <a name="data-points"></a>Veri noktaları

Telemetri özelliği, Kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz. Kodunuzu taramaz ve ad, depo veya yazar gibi proje düzeyi verileri ayıklamaz. Veriler, [Azure izleyici](https://azure.microsoft.com/services/monitor/) teknolojisini kullanan Microsoft sunucularına güvenli bir şekilde gönderilir, sınırlı erişim altında tutulur ve güvenli [Azure depolama](https://azure.microsoft.com/services/storage/) sistemlerinden katı güvenlik denetimleri altında yayımlanır.

Gizliliğinizi korumak bizim için önemlidir. Telemetrinin hassas verileri toplamasını veya verilerin güvenli veya uygun şekilde işlenmekte olduğunu düşünüyorsanız, [DotNet/SDK](https://github.com/dotnet/sdk/issues) deposunda bir sorun yapın veya araştırma için adresine bir e-posta gönderin [dotnet@microsoft.com](mailto:dotnet@microsoft.com) .

Telemetri özelliği aşağıdaki verileri toplar:

| SDK sürümleri | Veriler |
|--------------|------|
| Tümü          | Çağırma zaman damgası. |
| Tümü          | Komut çağrıldı (örneğin, "Build"), 2,1 'den başlayarak karma hale getirilmiş. |
| Tümü          | Coğrafi konumu belirlemede kullanılan üç sekizli IP adresi. |
| Tümü          | İşletim sistemi ve sürümü. |
| Tümü          | SDK 'nın üzerinde çalıştığı çalışma zamanı KIMLIĞI (RID). |
| Tümü          | .NET SDK sürümü. |
| Tümü          | Telemetri profili: isteğe bağlı bir değer yalnızca açık Kullanıcı kabul etme ve Microsoft 'ta dahili olarak kullanılan bir değerdir. |
| >= 2,0        | Komut bağımsız değişkenleri ve seçenekleri: birkaç bağımsız değişken ve seçenek toplanır (rastgele dizeler değil). [Toplanan seçeneklere](#collected-options)bakın. 2.1.300 sonrasında karma hale getirilir. |
| >= 2,0         | SDK 'nın bir kapsayıcıda çalışıp çalışmadığını belirtir. |
| >= 2,0         | `TargetFramework`2,1 ' den başlayarak karma hale getirilmiş hedef çerçeveler (olaydan). |
| >= 2,0         | Karma medya Access Control (MAC) adresi (SHA256). |
| >= 2,0         | Karma hale getirilmiş geçerli çalışma dizini. |
| >= 2,0         | Karma yükleyici exe dosya adına sahip başarı raporunu yükleme. |
| >= 2.1.300     | Çekirdek sürümü. |
| >= 2.1.300     | Libc sürümü/sürümü. |
| >= 3.0.100     | Çıktının yeniden yönlendirilme (true veya false). |
| >= 3.0.100     | CLı/SDK kilitlenmesinde, özel durum türü ve yığın izlemesi (yalnızca CLı/SDK kodu, gönderilen yığın izlemesinde bulunur). Daha fazla bilgi için bkz. [.net CLI/SDK kilitlenme özel durum telemetrisi toplandı](#net-clisdk-crash-exception-telemetry-collected). |

### <a name="collected-options"></a>Toplanan seçenekler

Bazı komutlar ek veriler gönderir. Bir komut alt kümesi ilk bağımsız değişkeni gönderir:

| Komut               | Gönderilen ilk bağımsız değişken verileri                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | İçin komut yardımı sorgulanırken.  |
| `dotnet new <arg>`    | Şablon adı (karma).             |
| `dotnet add <arg>`    | Sözcük `package` veya `reference` .      |
| `dotnet remove <arg>` | Sözcük `package` veya `reference` .      |
| `dotnet list <arg>`   | Sözcük `package` veya `reference` .      |
| `dotnet sln <arg>`    | , `add` Veya sözcüğü `list` `remove` .    |
| `dotnet nuget <arg>`  | , `delete` Veya sözcüğü `locals` `push` . |

Bir komut alt kümesi, kullanıldıkları takdirde, değerleriyle birlikte, seçili seçenekleri gönderir:

| Seçenek                  | Komutlar                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | Tüm komutlar                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`                  |
| `--framework`           | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest` |
| `--runtime`             | `dotnet build`,  `dotnet publish`                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

Ve dışında `--verbosity` `--sdk-package-version` , diğer tüm değerler .NET Core 2.1.100 SDK ile başlayarak karma hale getirilir.

## <a name="net-clisdk-crash-exception-telemetry-collected"></a>.NET CLı/SDK kilitlenme özel durum telemetrisi toplandı

.NET CLı/SDK kilitlenirse, CLı/SDK kodunun özel durum ve yığın izlemesinin adını toplar. Bu bilgiler, sorunları değerlendirmek ve .NET SDK ve CLı kalitesini geliştirmek için toplanır. Bu makalede Topladığımız veriler hakkında bilgi sağlanır. Ayrıca, kullanıcıların .NET SDK 'nın kendi sürümünü oluşturmayla ilgili ipuçları, kişisel veya hassas bilgilerin yanlışlıkla açıklanmasını önleyebilir.

### <a name="types-of-collected-data"></a>Toplanan veri türleri

.NET CLı, uygulamanızda özel durumlar değil yalnızca CLı/SDK özel durumları için bilgi toplar. Toplanan veriler, özel durumun ve yığın izlemenin adını içerir. Bu yığın izlemesi CLı/SDK kodudur.

Aşağıdaki örnek, toplanan veri türünü gösterir:

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a>Bilgilerin yanlışlıkla açıklanmasını önleyin

.NET SDK 'sının kendi kendilerini oluşturdukları bir .NET SDK sürümü çalıştıran herkes, SDK kaynak kodu yolunu kabul etmelidir. Özel hata ayıklama derlemesi olan veya özel derleme sembol dosyalarıyla yapılandırılmış bir .NET SDK kullanırken kilitlenme oluşursa, derleme makinesinden SDK kaynak dosyası yolu, yığın izlemenin bir parçası olarak toplanır ve karma değildir.

Bu nedenle, .NET SDK 'nın özel derlemeleri yol adları kişisel veya hassas bilgileri sunan dizinlerde yer içermemelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET CLı telemetri verileri](https://dotnet.microsoft.com/platform/telemetry)
- [Telemetri başvuru kaynağı (DotNet/SDK deposu)](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
