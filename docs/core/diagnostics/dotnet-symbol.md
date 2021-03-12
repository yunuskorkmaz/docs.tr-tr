---
title: DotNet-symbol Tanılama aracı-.NET CLı
description: .NET dökümlerinde ve mini dökümlerinde hata ayıklamak için gereken dosyaları indirmek için DotNet-symbol CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 4543bd965c889d93d7dc0b89ff2d6f62c4343e5f
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189910"
---
# <a name="symbol-downloader-dotnet-symbol"></a>Sembol yükleyici (DotNet-Symbol)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="install"></a>Yükleme

NuGet paketinin en son sürümünü yüklemek için `dotnet-symbol` [](https://www.nuget.org/packages/dotnet-symbol) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install --global dotnet-symbol
```

## <a name="synopsis"></a>Özeti

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a>Description

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

  Yalnızca, çekirdek dökümlerini yüklemek için gereken ana bilgisayar programını (DotNet) indirin.

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

   Sembol indirme yalnızca resmi [Web sitesi](https://dotnet.microsoft.com/download/dotnet) gibi resmi kanallar aracılığıyla elde edilen resmi .NET Core çalışma zamanı sürümleri ve [DotNet yükleme betiklerindeki varsayılan kaynaklar](../tools/dotnet-install-script.md)için desteklenir. Hata ayıklama dosyalarını karşıdan yüklerken 404 hatası, döküm dosyasının yerel olarak veya belirli bir Linux dışından oluşturulmuş bir .NET Core çalışma zamanı ile oluşturulduğunu veya arşiv Linux gibi topluluk sitelerini gösteriyor olabilir. Bu gibi durumlarda, hata ayıklama için gereken dosya (DotNet, libcoreclr.so ve libmscordaccore.so) bu kaynaklardan veya döküm dosyasının oluşturulduğu ortamdan kopyalanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

* [Semboller ile hata ayıklama](/windows/win32/dxtecharts/debugging-with-symbols)
* [Semboller ve taşınabilir pdb 'leri](./symbols.md)
