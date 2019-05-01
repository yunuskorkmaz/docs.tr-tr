---
title: .NET core SDK'sı telemetri
description: Analiz, hangi verileri toplanır ve nasıl devre dışı bırakmak için kullanım bilgileri toplamasına .NET Core SDK'sı telemetri özellikleri keşfedin.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 2ef6ade36092ff5a17b0cc420dc4859409d459ce
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63773845"
---
# <a name="net-core-sdk-telemetry"></a>.NET core SDK'sı telemetri

[.NET Core SDK'sı](index.md) içeren bir [telemetri özellik](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) , kullanım bilgilerini toplar. .NET ekibi geliştirilebilir bu nedenle araçları nasıl kullanıldığını anladığını önemlidir. Daha fazla bilgi için [.NET Core SDK'sı Telemetri öğrendiklerimizi](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).

Anonim ve yayınlanan hem Microsoft hem de altında topluluk tarafından kullanım için toplu bir biçimde toplanan verileri [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Kapsam

`dotnet` Komutu, hem uygulama hem de .NET Core CLI başlatmak için kullanılır. `dotnet` Komutun kendisindeki telemetri toplamak değil. .NET Core CLI komutları tarafından çalıştırılan `dotnet` komut telemetri toplar.

Telemetri *etkin değilse* kullanırken `dotnet` kendisine bağlı bir komut ile komutu:

- `dotnet`
- `dotnet [path-to-app]`

Telemetri *etkin* kullanırken [.NET Core CLI komutları](index.md), örneğin:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a>İptal etme

.NET Core SDK'sı telemetri özellik varsayılan olarak etkindir. Ayarlayarak telemetri özelliği iyileştirilmiş `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.

## <a name="data-points"></a>Veri noktaları

Bu özellik aşağıdaki verileri toplar:

- Zaman damgası çağırma&#8224;
- Komutu (örneğin "derleme") çağrılır&#8224;
- Coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresi&#8224;
- `ExitCode` komutu
- Test Çalıştırıcısı (için test projeleri)
- İşletim sistemi ve sürümü&#8224;
- Çalışma zamanı kimlikleri çalışma zamanları düğümünde mevcut olup olmadığı
- .NET core SDK sürümü&#8224;

&#8224;Bu ölçüm yayımlanır.

.NET Core 2.0 SDK'sı ile başlayarak, yeni veri noktaları toplanır:

- `dotnet` komut bağımsız değişkenleri ve seçenekleri: yalnızca bağımsız değişkenleri ve seçenekleri toplanan (değil rasgele dizeleri) bilinir.
- SDK'sı bir kapsayıcıda kullanılıp kullanılmadığını.
- Hedef çerçeve.
- Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz bir kimliği için bir makine. Bu ölçüm yayımlanan değil.
- Karma geçerli çalışma dizini.

Bu özellik, kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz. Bu, kodunuzu taramaz ve adı, depo veya yazar gibi hassas proje düzeyi verileri ayıklamak değil. Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) kısıtlı erişim'in altında tutulması ve katı güvenlik denetimleri güvenli altında yayımlanan teknoloji [Azuredepolama](https://azure.microsoft.com/services/storage/) sistemler.

.NET ekibi araçları nasıl kullanıldığını ve bunlar da ne araçlarla hedeflediğiniz platformun değil çalışıyorsanız bilmek istemektedir. Telemetri hassas veriler ya da toplama şüpheleniyorsanız veri endpoınt yapılıyor veya uygunsuz bir şekilde ele, sorunu bildirin [dotnet/CLI](https://github.com/dotnet/cli/issues) araştırma için depo.

## <a name="published-data"></a>Yayımlanan veriler

Yayımlanan veriler üç aylık olarak kullanılabilir ve listelenen [.NET Core SDK'sı kullanım verilerini](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md). Bir veri dosyasının sütunları şunlardır:

- Zaman damgası
- Örnekleri&#8224;
- Komut
- Coğrafi konum&#8225;
- OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;*Oluşum* sütunu bu komutun kullanın, sıranın ölçümler için o gün toplam sayısını görüntüler.

&#8225;Genellikle, *Coğrafya* sütun ülke adını görüntüler. Bazı durumlarda, bu sütunda, .NET Core Antarktika ya da yanlış konum verileri kullanarak Araştırmacıları nedeniyle Antarktika, kıta görünür.

### <a name="example"></a>Örnek

| Zaman damgası      | Örnekleri | Komut | Geography | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | Çalıştırma     | Uganda    | Darwin   | osx.10.12 x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Veri kümeleri

- [2016 - S3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)
- [2016 - 4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)
- [2017 - S1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)
- [2017 - S2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)
- [2017 - S3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)
- [2017 - 4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)

Ek veri kümeleri, standart bir URL biçimi kullanılarak gönderilir. Değiştirin `<YEAR>` yıl ve Değiştir `<QUARTER>` yılın çeyreği ile (kullanın `1`, `2`, `3`, veya `4`). Dosyaları sekmeyle ayrılmış değerler (*TSV*) biçimi.

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Lisans

Microsoft Dağıtım .NET Core ile lisanslanan [Microsoft Yazılımı Lisans koşulları: Mirosoft .NET kitaplığı](https://aka.ms/dotnet-core-eula). Veri toplama ve işleme hakkında daha fazla bilgi için "Veri" başlıklı bölüme bakın.

[.NET NuGet paketleri](https://www.nuget.org/profiles/dotnetframework) aynı lisans kullanın, ancak telemetri etkinleştirme (bkz [kapsam](#scope)).

## <a name="disclosure"></a>Açığa çıkması

İlk birini çalıştırdığınızda, .NET Core SDK'sı aşağıdaki metni görüntüler [.NET Core CLI komutları](index.md) (örneğin, `dotnet restore`). Metin, çalıştırmakta olduğunuz SDK'sı sürümüne bağlı olarak biraz değişebilir. Nasıl Microsoft, veri toplama hakkında size bildirir, bu "İlk Çalıştırma" deneyimi sunar.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core SDK'sı Telemetri öğrendiklerimizi](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/)
- [Telemetri başvuru kaynağı (dotnet/CLI depo)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [.NET core SDK'sı kullanım verileri](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
