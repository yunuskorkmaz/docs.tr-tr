---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603008"
---

Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir. Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:

- lttng-ust
- libkıvrık
- OpenSSL-libs
- krb5-libs
- libıu
- zlib
- librüzgar
- libuuid

Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10**yüklemeniz gerekir.

Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:

- [libgdiplus (sürüm 6.0.1 veya üzeri)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.
