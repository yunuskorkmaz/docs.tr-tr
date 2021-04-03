---
title: .NET 'i alp-.NET üzerine yükler
description: .NET SDK ve .NET çalışma zamanının alp 'ye yüklenmesi için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6cd36fa6329d3c1a5835d4c202ac0024ffa41892
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079511"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>.NET SDK 'sını veya .NET çalışma zamanını alp 'ye yükler

Bu makalede, alp 'de .NET yüklemesinin nasıl yapılacağı açıklanır. Bir alp sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir. Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a>Yükleme

Yükleyiciler alp Linux için kullanılamaz. .NET 'i aşağıdaki yöntemlerle birini yüklemelisiniz:

- [Yaslama paketi](linux-snap.md)
- [_İnstall-DotNet.sh_ ile betikleştirilmiş install](linux-scripted-manual.md#scripted-install)
- [El ile ikili ayıklama](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.

- ✔️, alp veya .NET sürümünün hala desteklendiğini gösterir.
- A ❌ , alp veya .NET sürümünün bu alp sürümünde desteklenmediğini belirtir.
- Hem alp hem de bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-------- |---------------|---------------|----------------|
| ✔️ 3,13 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ 3,12 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ 3,11 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ 3,10 | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ 3,9  | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ 3,8  | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |

Aşağıdaki .NET sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3.0
- 2,2
- 2.0

## <a name="dependencies"></a>Bağımlılıklar

.NET alp Linux 'ta aşağıdaki bağımlılıkların yüklü olmasını gerektirir:

- ICU-libs
- krb5-libs
- libgcc
- libgdiplus (.NET uygulaması *System. Drawing. Common* derlemesini gerektiriyorsa)
- libintl
- libssl 1.1 (alp v 3.9 veya üzeri)
- libssl 1.0 (alp v 3.8 veya Lower)
- libstdc + +
- zlib

Gerekli gereksinimleri yüklemek için şu komutu çalıştırın:

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

**Libgdiplus**'yi yüklemek için bir depo belirtmeniz gerekebilir:

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a>Sonraki adımlar

- [.NET CLı için sekme tamamlamayı etkinleştirme](../tools/enable-tab-autocomplete.md)
- [Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
