---
title: Windows Kapsayıcıları ayarlamak için bir DockerFile içinde Windows PowerShell komutları kullanma (Docker standardına göre)
description: Windows kapsayıcılarında Docker ile çalışırken PowerShell 'in nasıl kullanılacağını öğrenin
ms.date: 08/06/2020
ms.openlocfilehash: 4e7b9e7fedf11b97b3f468aef541bf72a4e88ebc
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915389"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Windows Kapsayıcıları ayarlamak için bir DockerFile içinde Windows PowerShell komutları kullanma (Docker standardına göre)

[Windows kapsayıcıları](/virtualization/windowscontainers/about/index)ile, mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürebilir ve bunları Docker ekosisteminin geri kalanı ile aynı araçlarla dağıtabilirsiniz.

Windows kapsayıcıları kullanmak için, aşağıdaki örnekte gösterildiği gibi DockerFile dosyasına Windows PowerShell komutları yazmanız yeterlidir:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, Windows PowerShell 'i kullanarak Windows Server çekirdek temel görüntüsünü ve IIS 'yi de yüklersiniz.

Benzer şekilde, burada gösterildiği gibi geleneksel ASP.NET 4. x ve .NET 4,6 veya diğer Windows yazılımları gibi ek bileşenleri ayarlamak için Windows PowerShell komutlarını da kullanabilirsiniz:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Önceki](visual-studio-tools-for-docker.md) 
> [Sonraki](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
