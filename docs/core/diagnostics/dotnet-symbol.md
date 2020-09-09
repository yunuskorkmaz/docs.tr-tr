---
title: DotNet-symbol-.NET Core
description: DotNet-symbol komut satırı aracını yükleme ve kullanma.
ms.date: 08/26/2020
ms.openlocfilehash: feaa64ad756878f85b829ab0cecf6ea2736014ba
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598354"
---
# <a name="symbol-downloader-dotnet-symbol"></a>Sembol yükleyici (DotNet-Symbol)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="install-dotnet-symbol"></a>DotNet 'yi Install-symbol

NuGet paketinin en son sürümünü yüklemek için `dotnet-symbol` [NuGet package](https://www.nuget.org/packages/dotnet-symbol) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install -g dotnet-symbol
```

## <a name="synopsis"></a>Özeti

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a>Açıklama

`dotnet-symbol`Genel araç, çekirdek dökümlerinde ve mini dökümlerinde hata ayıklamak için gereken dosyaları (semboller, dac, modüller vb.) indirir. Bu, başka bir makinede yakalanan dökümlerinin hata ayıklaması sırasında yararlı olabilir. `dotnet-symbol` , dökümünü çözümlemek için gereken modülleri ve sembolleri indirebilir.

## <a name="options"></a>Seçenekler

- **`--microsoft-symbol-server`**

  ' http://msdl.microsoft.com/download/symbols ' Sembol sunucusu yolu ekleyin (varsayılan).

- **`--server-path <symbol server path>`**

  Sunucu yoluna bir sembol sunucusu ekleyin.

- **`authenticated-server-path <pat> <server path>`**

  Bir kişisel erişim belirteci (PAT) kullanarak sunucu yoluna kimliği doğrulanmış bir sembol sunucusu ekleyin.

- **`--cache-directory <file cache directory>`**

  Önbellek dizini ekler.

- **`--recurse-subdirectories`**

  Giriş dosyalarını tüm alt dizinlerde işle.

- **`--host-only`**

  Yalnızca çekirdek dökümlerini yüklemek için gereken bir ana bilgisayar programını (örneğin, DotNet) indirin.

- **`--symbols`**

  Sembol dosyalarını (. pdb,. dbg,. Dwarf) indirin.

- **`--modules`**

  Modül dosyalarını (. dll,. so,. dylib) indirin.

- **`--debugging`**

  Özel hata ayıklama modüllerini (DAC, DBI, SOS) indirin.

- **`--windows-pdbs`**

  Taşınabilir pdb 'leri de kullanılabilir olduğunda Windows pdb 'leri indirmeye zorlayın.

- **`-o, --output <output directory>`**

  Çıkış dizinini ayarlayın. Aksi takdirde, giriş dosyasının yanına yazın (varsayılan).

- **`-d, --diagnostics`**

  Tanılama çıkışını etkinleştirin.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="download-symbols"></a>Sembolleri indir

`dotnet-symbol`Bir döküm dosyasına karşı çalıştırmak, varsayılan olarak, yönetilen derlemeler dahil olmak üzere dökümdeki hataları ayıklamak için gereken tüm modülleri, sembolleri ve dac/DBı dosyalarını indirir. SOS artık gerektiğinde sembolleri indirebildiğinden, çoğu Linux çekirdek dökümü yalnızca Konak (DotNet) ve hata ayıklama modülleriyle lldb kullanılarak analiz edilebilir. Lldb çalıştırmasında bir çekirdek dökümünü tanılamak için gerekli olan bu dosyaları almak için:

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a>Sorun giderme

- sembol indirilirken 404 bulunamadı.

   Sembol indirme yalnızca resmi [Web sitesi](https://dotnet.microsoft.com/download/dotnet-core) gibi resmi kanallar aracılığıyla elde edilen resmi .NET Core çalışma zamanı sürümleri ve [DotNet yükleme betiklerindeki varsayılan kaynaklar](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-scripts)için desteklenir. Hata ayıklama dosyalarını karşıdan yüklerken 404 hatası, döküm dosyasının yerel olarak veya belirli bir Linux dışından oluşturulmuş bir .NET Core çalışma zamanı ile oluşturulduğunu veya arşiv Linux gibi topluluk sitelerini gösteriyor olabilir. Bu gibi durumlarda, hata ayıklama için gereken dosya (DotNet, libcoreclr.so ve libmscordaccore.so) bu kaynaklardan veya döküm dosyasının oluşturulduğu ortamdan kopyalanmalıdır.
