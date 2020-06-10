---
ms.openlocfilehash: 164d7a8277cf985735b959c73eb87391944e795b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602903"
---

### <a name="install-the-sdk"></a>SDK Yükleme

.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır. .NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. .NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> **DotNet-SDK-2,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır. Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> Bir hata iletisi alırsanız, **aspnetcore-Runtime-2,1 paketini bulamazsanız**, bkz. [apt sorun giderme](#apt-troubleshooting) bölümü.

ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: `aspnetcore-runtime-2.1` Yukarıdaki komutu ile değiştirin `dotnet-runtime-2.1` .

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
