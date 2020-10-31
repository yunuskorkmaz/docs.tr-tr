---
ms.openlocfilehash: 2edb06106283c26573863f230e5e9956728cdfa3
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135985"
---

### <a name="install-the-sdk"></a>SDK Yükleme

.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır. .NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. .NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:

```bash
sudo dnf install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır. Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanını yükleyebilirsiniz: `aspnetcore-runtime-3.1` ile önceki komutta değiştirin `dotnet-runtime-3.1` .

```bash
sudo dnf install dotnet-runtime-3.1
```
