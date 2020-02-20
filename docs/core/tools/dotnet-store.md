---
title: DotNet depo komutu
description: "' DotNet Store ' komutu, belirtilen derlemeleri çalışma zamanı paket deposunda depolar."
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503583"
---
# <a name="dotnet-store"></a>dotnet store

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet store`-belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a>Açıklama

`dotnet store`, belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar. Varsayılan olarak, derlemeler hedef çalışma zamanına ve çerçeveye en iyi duruma getirilir. Daha fazla bilgi için bkz. [çalışma zamanı paket deposu](../deploying/runtime-store.md) konusu.

## <a name="required-options"></a>Gerekli seçenekler

- **`-f|--framework <FRAMEWORK>`**

  [Hedef çerçeveyi](../../standard/frameworks.md)belirtir. Hedef çerçeve proje dosyasında belirtilmelidir.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  *Paket deposu bildirim dosyası* , depolanacak paketlerin listesini IÇEREN bir XML dosyasıdır. Bildirim dosyasının biçimi, SDK stili proje biçimiyle uyumludur. Bu nedenle, istenen paketlere başvuran bir proje dosyası, derlemeleri çalışma zamanı paket deposunda depolamak için `-m|--manifest` seçeneği ile birlikte kullanılabilir. Birden çok bildirim dosyası belirtmek için, her bir dosyanın seçeneğini ve yolunu tekrarlayın. Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Hedeflenecek [çalışma zamanı tanımlayıcısı](../rid-catalog.md) .

## <a name="optional-options"></a>İsteğe bağlı seçenekler

- **`--framework-version <FRAMEWORK_VERSION>`**

  .NET Core SDK sürümünü belirtir. Bu seçenek, `-f|--framework` seçeneği tarafından belirtilen çerçevenin ötesinde belirli bir çerçeve sürümü seçmenizi sağlar.

- **`-h|--help`**

  Yardım bilgilerini gösterir.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Çalışma zamanı paket deposunun yolunu belirtir. Belirtilmemişse, varsayılan olarak Kullanıcı profili .NET Core yükleme dizininin *Depo* alt dizini olur.

- **`--skip-optimization`**

  İyileştirme aşamasını atlar.

- **`--skip-symbols`**

  Sembol oluşturmayı atlar. Şu anda yalnızca Windows ve Linux üzerinde semboller oluşturabilirsiniz.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  Komut tarafından kullanılan çalışma dizini. Belirtilmemişse, geçerli dizinin *obj* alt dizinini kullanır.

## <a name="examples"></a>Örnekler

- .NET Core 2.0.0 için *Packages. csproj* proje dosyasında belirtilen paketleri depolayın:

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- *Packages. csproj* içinde belirtilen paketleri iyileştirme olmadan depola:

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı paket deposu](../deploying/runtime-store.md)
