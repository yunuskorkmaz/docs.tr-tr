---
title: .NET core CLI araçlarını telemetri
description: Analiz, hangi verileri toplanır ve nasıl devre dışı bırakmak için kullanım bilgilerini toplamasına .NET Core araçları telemetri özellikleri keşfedin.
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.openlocfilehash: 4c04867f5db512ef53c23ec41ea66db570a82021
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216089"
---
# <a name="net-core-cli-tools-telemetry"></a>.NET core CLI araçlarını telemetri

[.NET Core SDK](index.md) içeren bir [telemetri özellik](https://github.com/dotnet/cli/pull/2145) kullanım bilgilerini toplar. .NET ekibi, böylece biz artırabilir araçları nasıl kullanıldığını algıladığını önemlidir. Daha fazla bilgi için bkz: [ne biz .NET Core SDK Telemetri öğrendiğinize](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).

Anonim ve kullanmak için toplanan biçimde yayınlanan hem Microsoft hem de altında topluluk tarafından toplanan veriler [Creative Commons Attribution lisans](https://creativecommons.org/licenses/by/4.0/). 

## <a name="scope"></a>Kapsam

`dotnet` Komutu, hem uygulamalar hem de .NET Core CLI başlatmak için kullanılır. `dotnet` Komutu kendisi telemetri toplamak değil. .NET Core CLI komutları tarafından çalıştırılan `dotnet` komutu telemetri topla.

Telemetri *etkinleştirilmemiş* kullanırken `dotnet` kendisine bağlı hiçbir komutuyla komutu:

- `dotnet`
- `dotnet [path-to-app]`

Telemetri *etkin* kullanırken [.NET Core CLI komutları](index.md), gibi:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a>Davranış

.NET Core CLI araçlarını telemetri özellik varsayılan olarak etkindir. Üyelikten çıkmak ayarlayarak telemetri özelliğinin `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.

## <a name="data-points"></a>Veri noktaları

Bu özellik aşağıdaki verileri toplar:

- Zaman damgası çağırma&#8224;
- (Örneğin "Oluştur") çağrılan komutu&#8224;
- Coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresi&#8224;
- `ExitCode` komutu
- Test Çalıştırıcısı (için test projeleri)
- İşletim sistemi ve sürümü&#8224;
- Çalışma zamanı kimlikleri çalışma zamanları düğümünde mevcut olup olmadığı
- .NET core SDK sürümü&#8224;

&#8224;Bu ölçüm yayımlanır.

.NET Core SDK 2.0 ile başlayarak, yeni veri noktaları toplanır:

- `dotnet` komut bağımsız değişkenleri ve seçenekleri: yalnızca bağımsız değişkenleri ve seçenekleri toplanan (değil rastgele dizeleri) bilinir.
- SDK bir kapsayıcıda çalışıp çalışmadığını.
- Bir hedef çerçeve.
- Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz kimliği için bir makine. Bu ölçüm yayımlanmaz.
- Karma geçerli çalışma dizini.

Özellik kullanıcı adlarını veya e-posta adresleri gibi kişisel verilerini topla değil. Kodunuzu taramaz ve adı, depodaki veya yazar gibi hassas proje düzeyi verileri ayıklamak değil. Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) altında kısıtlı erişim tutulur ve katı güvenlik denetimleri güvenli altında yayımlanan teknolojisi [Azure Storage](https://azure.microsoft.com/services/storage/) sistemler.

Araçlar nasıl kullanıldığı ve bunlar da, ne araçlarla oluşturmakta değil çalışırken bilmek isteriz. Telemetri hassas verileri veya güvenli şekilde çalışıyoruz toplama veya açamayacağı veri işleme şüpheleniyorsanız [bir sorun dotnet/CLI depodaki sorunları dosya](https://github.com/dotnet/cli/issues) araştırma için.

## <a name="published-data"></a>Yayımlanan veriler

Yayımlanan verileri üç aylık olarak kullanılabilir ve adresinde listelenmiş [.NET Core SDK kullanım verilerini](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md). Bir veri dosyası sütunlarının şunlardır:
- zaman damgası
- Yineleme&#8224;
- Komut
- Coğrafi konum&#8225;
- OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;*Oluşum* sütunu bu komut, sıranın ölçümleri kullanılmak o gün toplam sayısını görüntüler. 

&#8225;Genellikle, *Coğrafya* sütun bir ülke adını görüntüler. Bazı durumlarda, bu sütun, .NET Core Antarktika veya yanlış konumu verileri kullanarak araştırmacılarının nedeniyle Antarktika kıtada görünür.

### <a name="example"></a>Örnek

| zaman damgası      | Yineleme | Komut | coğrafi konum | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | çalıştırma     | Uganda    | Darwin   | osx.10.12 x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Veri kümeleri

[2016 - S3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016 - 4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017 - S1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017 - S2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

Ek veri kümeleri, standart bir URL biçimi kullanılarak gönderilir. Değiştir `<YEAR>` değiştirin ve yıl `<QUARTER>` çeyreği ile (kullanmak `1`, `2`, `3`, veya `4`). Dosyaları sekmeyle ayrılmış değerler (*TSV*) biçimi. 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a>Lisans

.NET Core Microsoft dağıtılması ile lisanslı [MICROSOFT .NET kitaplığı EULA](https://aka.ms/dotnet-core-eula). Bu lisans telemetri (aşağıda gösterilen) etkinleştirmek için "DATA" bölüm içerir.

[.NET NuGet paketleri](https://www.nuget.org/profiles/dotnetframework) aynı lisans kullanır ancak telemetri etkinleştirmezseniz (bkz [kapsam](#scope)).

> 2. VERİLER. Yazılım ve yazılımı kullanımınız hakkında bilgi toplamak ve Microsoft'a göndermek. Microsoft, bu bilgiler, ürünlerimizi ve hizmetlerimizi geliştirmek için kullanabilir. Veri toplama hakkında daha fazla bilgi ve Yardım belgelerine ve adresindeki Gizlilik Bildirimi'ne kullanma http://go.microsoft.com/fwlink/?LinkId=528096. Bu uygulamalar için onay yazılımı kullanımınız çalışır.

## <a name="disclosure"></a>Açığa çıkması

.NET Core CLI araçlarını komutlarından birini ilk kez çalıştırdığınızda, aşağıdaki metni görüntüle (örneğin, `dotnet restore`). Metin, çalıştırmakta olduğunuz SDK'sı sürümüne bağlı olarak biraz değişebilir. Bu "ilk Çalıştır" nasıl Microsoft, verilerin toplanması hakkında bilgilendirir deneyimidir.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a>Ayrıca bkz.

[Ne biz .NET Core SDK Telemetri öğrendiniz](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[Telemetri başvuru kaynağı (dotnet/CLI depodaki; release/2.0.0 dalı)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry)   
[.NET core SDK kullanım verileri](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
