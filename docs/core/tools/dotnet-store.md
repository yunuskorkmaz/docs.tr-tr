---
title: DotNet depolama komutu
description: "'Dotnet deposu' komutunu belirtilen derlemeleri çalışma zamanı Paket Deposu."
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a12738d0cc8edcbb65d5b6fab6e7c8b209b0f4b5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029901"
---
# <a name="dotnet-store"></a>DotNet deposu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Ad

`dotnet store` -Belirli derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).

## <a name="synopsis"></a>Özeti

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Açıklama

`dotnet store` Belirtilen derlemede depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md). Varsayılan olarak, derlemeleri çerçevesi ve hedef çalışma zamanı için iyileştirilmiştir. Daha fazla bilgi için [çalışma zamanı Paket Deposu](../deploying/runtime-store.md) konu.

## <a name="required-options"></a>Gerekli seçenekleri

`-f|--framework <FRAMEWORK>`

Belirtir [hedef Framework'ü](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

*Paket Deposu bildirim dosyası* depolamak için paketler listesini içeren bir XML dosyasıdır. Bildirim dosyasının biçimi SDK stilinde proje biçimi ile uyumludur. Bu nedenle, istediğiniz paketleri başvuran bir proje dosyası ile birlikte kullanılabilir `-m|--manifest` derlemeler çalışma zamanı paketi deposuna seçeneği. Birden çok bildirim dosyaları belirtmek için her dosya için yolu ve seçeneği yineleyin. Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

[Çalışma zamanı tanımlayıcısı](../rid-catalog.md) hedef.

## <a name="optional-options"></a>İsteğe bağlı Seçenekler

`--framework-version <FRAMEWORK_VERSION>`

.NET Core SDK'sı sürümünü belirtir. Bu seçeneği tarafından belirtilen framework ötesinde bir özel framework sürümünü seçmenize olanak sağlayan `-f|--framework` seçeneği.

`-h|--help`

Yardım bilgisi gösterir.

`-o|--output <OUTPUT_DIRECTORY>`

Çalışma zamanı Paket Deposu yolunu belirtir. Belirtilmezse, varsayılan *depolamak* kullanıcı profili .NET Core yükleme dizininin alt.

`--skip-optimization`

İyileştirme aşamasından atlar.

`--skip-symbols`

Atlamalar nesil simge. Şu anda yalnızca Windows ve Linux üzerinde sembolleri oluşturabilirsiniz.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Komut tarafından kullanılan çalışma dizini. Belirtilmezse, kullandığı *obj* geçerli dizininin alt.

## <a name="examples"></a>Örnekler

Belirtilen paket Store *packages.csproj* .NET Core 2.0.0 için proje dosyası:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Belirtilen paket Store *packages.csproj* iyileştirme olmadan:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Ayrıca bkz.

* [Çalışma zamanı paket deposu](../deploying/runtime-store.md)