---
ms.openlocfilehash: 87c7abf6a20dd8e9769f3b3b3cbe271d32fd62c3
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507006"
---

### <a name="install-the-sdk"></a>SDK Yükleme

.NET SDK, .NET ile uygulama geliştirmenize olanak tanır. .NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. .NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

> [!IMPORTANT]
> **DotNet-SDK-5,0** ' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

ASP.NET Core çalışma zamanı, .NET ile yapılan ve çalışma zamanı sağlamayan uygulamaları çalıştırmanızı sağlar. Aşağıdaki komutlar, .NET için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler. Terminalinizde aşağıdaki komutları çalıştırın:

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```

> [!IMPORTANT]
> Bir hata iletisi alırsanız, **aspnetcore-Runtime-5,0 paketini bulamazsanız** , bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.

ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: `aspnetcore-runtime-5.0` önceki komutta ile değiştirin `dotnet-runtime-5.0` :

```bash
sudo apt-get install -y dotnet-runtime-5.0
```
