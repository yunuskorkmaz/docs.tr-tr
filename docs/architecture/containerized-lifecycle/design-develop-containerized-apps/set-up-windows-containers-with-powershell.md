---
title: Windows kapsayıcıları ayarlamak için bir DockerFile içindeki Windows PowerShell komutlarını kullanma (Docker Standard tabanlı)
description: Windows kapsayıcılarında Docker ile çalışırken PowerShell 'in nasıl kullanılacağını öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295706"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Windows kapsayıcıları ayarlamak için bir DockerFile içindeki Windows PowerShell komutlarını kullanma (Docker Standard tabanlı)

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
>[Önceki](visual-studio-tools-for-docker.md)İleri
>[](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
