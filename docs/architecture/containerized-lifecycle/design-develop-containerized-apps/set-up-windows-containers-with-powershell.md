---
title: Windows Kapsayıcıları ayarlamak için bir DockerFile içinde Windows PowerShell komutları kullanma (Docker standardına göre)
description: Windows kapsayıcılarında Docker ile çalışırken PowerShell'i nasıl kullanacağınızı öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295706"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Windows Kapsayıcıları ayarlamak için bir DockerFile içinde Windows PowerShell komutları kullanma (Docker standardına göre)

[Windows Kapsayıcıları](/virtualization/windowscontainers/about/index)ile, mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürebilir ve bunları Docker ekosisteminin geri kalanıyla aynı araçlarla dağıtabilirsiniz.

Windows Kapsayıcıları'nı kullanmak için, aşağıdaki örnekte gösterildiği gibi DockerFile'a Windows PowerShell komutları yazmanız gerekir:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, Windows PowerShell'i Windows Server Core temel görüntüsünü ve IIS'yi yüklemek için kullanıyoruz.

Benzer bir şekilde, burada gösterildiği gibi geleneksel ASP.NET 4.x ve .NET 4.6 veya başka bir Windows yazılımı gibi ek bileşenler ayarlamak için Windows PowerShell komutlarını da kullanabilirsiniz:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Önceki](visual-studio-tools-for-docker.md)
>[Sonraki](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
