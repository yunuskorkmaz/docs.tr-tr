---
title: .NET Çekirdek SDK telemetri
description: Analiz için kullanım bilgilerini toplayan .NET Core SDK telemetri özelliklerini, hangi verilerin toplandığını ve nasıl devre dışı kalındığını keşfedin.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: a79b791abc99331ff39f5e281ee0fdc62b258989
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507288"
---
# <a name="net-core-sdk-telemetry"></a>.NET Çekirdek SDK telemetri

[.NET Core SDK, .NET Core](index.md) CLI çöktüğinde kullanım verilerini ve özel durum bilgilerini toplayan bir telemetri özelliği içerir. .NET Core CLI .NET Core SDK ile birlikte gelir ve .NET Core uygulamalarınızı oluşturmanızı, test etmenizi ve yayınlamanızı sağlayan fiiller kümesidir. .NET ekibinin araçların nasıl kullanıldığını anlayıp geliştirilmelerini laması önemlidir. Hatalar la ilgili bilgiler, takımın sorunları çözmesi ve hataları düzeltmesi yardımcı olur.

Toplanan veriler anonimdir ve [Creative Commons Atıf Lisansı](https://creativecommons.org/licenses/by/4.0/)altında toplu olarak yayınlanır.

## <a name="scope"></a>Kapsam

`dotnet`uygulamaları çalıştırmak ve CLI komutlarını yürütmek için iki işlevi vardır. Bir uygulamayı aşağıdaki biçimde başlatmak `dotnet` için kullanırken telemetri *toplanmaz:*

- `dotnet [path-to-app].dll`

Telemetri,.NET [Core CLI komutlarından](index.md)herhangi biri (örneğin) kullanılarak *toplanır:*

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Nasıl devre dışı bırakmak için

.NET Core SDK telemetri özelliği varsayılan olarak etkinleştirilir. Telemetri özelliğini devre dışı bırakmak `DOTNET_CLI_TELEMETRY_OPTOUT` için `1` ortam `true`değişkenini veya '

Başarılı bir yükleme gerçekleştiğinde .NET Core SDK yükleyicisi tarafından da tek bir telemetri girişi gönderilir. Devre dışı bırakmak `DOTNET_CLI_TELEMETRY_OPTOUT` için ,.NET Core SDK'yı yüklemeden önce ortam değişkenini ayarlayın.

## <a name="disclosure"></a>Açıklama

.NET Core SDK, [.NET Core CLI komutlarından](index.md) birini ilk çalıştırdığınızda (örneğin, `dotnet build`aşağıdakilere benzer bir metin görüntüler). Metin, çalıştırdığınız SDK sürümüne bağlı olarak biraz değişiklik gösterebilir. Bu "ilk çalıştırma" deneyimi, Microsoft'un veri toplama hakkında sizi nasıl bilgi edindiğini ortaya attırdığıdır.

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

Bu iletiyi ve .NET Core karşılama iletisini devre dışı kılabilir, ortam değişkenini `DOTNET_NOLOGO` `true`. Bu değişkenin telemetri devre dışı bırakma üzerinde hiçbir etkisi olmadığını unutmayın.

## <a name="data-points"></a>Veri noktaları

Telemetri özelliği, kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz. Kodunuzu tarayıp ad, depo veya yazar gibi proje düzeyinde veri ayıklamaz. Veriler, [Azure Monitor](https://azure.microsoft.com/services/monitor/) teknolojisini kullanarak Microsoft sunucularına güvenli bir şekilde gönderilir, sınırlı erişim altında tutulur ve güvenli [Azure Depolama](https://azure.microsoft.com/services/storage/) sistemlerinden gelen sıkı güvenlik denetimleri altında yayımlanır.

Gizliliğinizi korumak bizim için önemlidir. Telemetrinin hassas verileri topladığından veya verilerin güvensiz veya uygunsuz şekilde işlendiğinden şüpheleniyorsanız, [dotnet/cli](https://github.com/dotnet/cli/issues) deposunda bir sorun [dotnet@microsoft.com](mailto:dotnet@microsoft.com) dosyala veya soruşturma için bir e-posta gönderin.

Telemetri özelliği aşağıdaki verileri toplar:

| SDK sürümleri | Veri |
|--------------|------|
| Tümü          | Çağırma zaman damgası. |
| Tümü          | Komut çağrıldı (örneğin, "inşa"), 2.1'den başlayarak haşiye. |
| Tümü          | Coğrafi konumu belirlemek için kullanılan üç sekizli IP adresi. |
| Tümü          | İşletim sistemi ve sürüm. |
| Tümü          | Çalışma Zamanı Kimliği (RID) SDK üzerinde çalışıyor. |
| Tümü          | .NET Çekirdek SDK versiyonu. |
| Tümü          | Telemetri profili: yalnızca açık kullanıcı tercihi ile kullanılan ve Microsoft'ta dahili olarak kullanılan isteğe bağlı bir değerdir. |
| >=2.0        | Komut bağımsız değişkenleri ve seçenekleri: çeşitli bağımsız değişkenler ve seçenekler toplanır (rasgele dizeleri değil). [Toplanan seçeneklere](#collected-options)bakın. 2.1.300'den sonra hashed. |
| >=2.0         | SDK'nın bir kapta çalışıp çalışmadığı. |
| >=2.0         | Hedef çerçeveler `TargetFramework` (olaydan), 2.1'den başlayan bir hadde. |
| >=2.0         | Karma Medya Erişim Kontrolü (MAC) adresi: bir makine için şifreleme (SHA256) anonim ve benzersiz bir kimlik. |
| >=2.0         | Hashed geçerli çalışma dizini. |
| >=2.0         | Hashed installer exe dosya adı ile başarı raporu yükleyin. |
| >=2.1.300     | Çekirdek versiyonu. |
| >=2.1.300     | Libc sürümü/sürümü. |
| >=3.0.100     | Çıktının yönlendirilip yönlendirilmediği (doğru veya yanlış). |
| >=3.0.100     | CLI/SDK kilitlenmesinde, özel durum türü ve yığın izi (gönderilen yığın izlemesine yalnızca CLI/SDK kodu dahildir). Daha fazla bilgi için [bkz.](#net-core-clisdk-crash-exception-telemetry-collected) |

### <a name="collected-options"></a>Toplanan seçenekler

Bazı komutlar ek veri gönderir. Komutların bir alt kümesi ilk bağımsız değişkeni gönderir:

| Komut               | Gönderilen ilk bağımsız değişken verileri                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | Komut yardımı için sorgulanıyor.  |
| `dotnet new <arg>`    | Şablon adı (hashed).             |
| `dotnet add <arg>`    | Kelime `package` ya `reference`da .      |
| `dotnet remove <arg>` | Kelime `package` ya `reference`da .      |
| `dotnet list <arg>`   | Kelime `package` ya `reference`da .      |
| `dotnet sln <arg>`    | Kelime `add`, `list`, `remove`veya .    |
| `dotnet nuget <arg>`  | Kelime `delete`, `locals`, `push`veya . |

Komutların bir alt kümesi, değerleriyle birlikte kullanılırsa seçili seçenekleri gönderir:

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

`--verbosity` .NET Core 2.1.100 SDK ile başlayan diğer tüm değerler karnedir. `--sdk-package-version`

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>.NET Core CLI/SDK çarpışma istisnatelemetri toplanan

.NET Core CLI/SDK çökerse, özel durum adını toplar ve CLI/SDK kodunun yığın izini toplar. Bu bilgiler, sorunları değerlendirmek ve .NET Core SDK ve CLI kalitesini artırmak için toplanır. Bu makalede, topladığımız veriler hakkında bilgi verilmektedir. Ayrıca, .NET Core SDK'nın kendi sürümünü oluşturan kullanıcıların kişisel veya hassas bilgilerin yanlışlıkla açıklanmasını nasıl önleyebildiği hakkında ipuçları da sağlar.

### <a name="types-of-collected-data"></a>Toplanan veri türleri

.NET Core CLI, uygulamanızdaki istisnalar için değil, yalnızca CLI/SDK istisnaları için bilgi toplar. Toplanan veriler özel durum ve yığın izleme adını içerir. Bu yığın izi CLI/SDK koduna ait.

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

### <a name="avoid-inadvertent-disclosure-of-information"></a>Bilgilerin yanlışlıkla ifşa edilmesinden kaçının

.NET Core katılımcıları ve .NET Core SDK'nın kendi kurdukları bir sürümünü çalıştıran herkes, SDK kaynak kodlarına giden yolu göz önünde bulundurmalıdır. Özel hata ayıklama yapılı veya özel yapı simgesi dosyalarıyla yapılandırılan bir .NET Core SDK kullanırken bir kilitlenme oluşursa, yapı makinesinden Gelen SDK kaynak dosya yolu yığın izlemenin bir parçası olarak toplanır ve haşlanmadı.

Bu nedenle, .NET Core SDK'nın özel yapılarının, yol adları kişisel veya hassas bilgileri açığa çıkaran dizinlerde bulunmaması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI Telemetri - 2019 S2 Verileri](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [Telemetri referans kaynağı (dotnet/cli deposu)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
