---
title: .NET 'i alp-.NET üzerine yükler
description: .NET SDK ve .NET çalışma zamanının alp 'ye yüklenmesi için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506833"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>.NET SDK 'sını veya .NET çalışma zamanını alp 'ye yükler

Bu makalede, alp 'de .NET yüklemesinin nasıl yapılacağı açıklanır. Bir alp sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir. Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Alp için yükleyiciler yok. [Install betiğini](#scripted-install) kullanmanız veya [el ile Install](#manual-install) yönergelerini izlemeniz gerekir.

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.

- ✔️, alp veya .NET sürümünün hala desteklendiğini gösterir.
- A ❌ , alp veya .NET sürümünün bu alp sürümünde desteklenmediğini belirtir.
- Hem alp hem de bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Alpine  | .NET Core 2.1 | .NET Core 3,1 | .NET 5,0 |
|-------- |---------------|---------------|----------------|
| ✔️ 3,12 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ 3,11 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ 3,10 | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ 3,9  | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ 3,8  | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |

Aşağıdaki .NET sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3,0
- 2.2
- 2,0

## <a name="dependencies"></a>Bağımlılıklar

.NET alp Linux 'ta aşağıdaki bağımlılıkların yüklü olmasını gerektirir:

- ICU-libs
- krb5-libs
- libgcc
- libintl
- libssl 1.1 (alp v 3.9 veya üzeri)
- libssl 1.0 (alp v 3.8 veya Lower)
- libstdc + +
- zlib

## <a name="scripted-install"></a>Komut dosyalı yüklemesi

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>El ile yüklemesi

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Sonraki adımlar

- [Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
