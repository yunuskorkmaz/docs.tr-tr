---
title: Windows Kapsayıcıları ayarlamak için bir DockerFile içinde Windows PowerShell komutları kullanma (Docker standardına göre)
description: Windows kapsayıcılarında Docker ile çalışırken PowerShell 'in nasıl kullanılacağını öğrenin
ms.date: 08/06/2020
ms.openlocfilehash: d65538c821a848d83915e715ee3a02990b40e836
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681255"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="b33e7-103">Windows Kapsayıcıları ayarlamak için bir DockerFile içinde Windows PowerShell komutları kullanma (Docker standardına göre)</span><span class="sxs-lookup"><span data-stu-id="b33e7-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="b33e7-104">[Windows kapsayıcıları](/virtualization/windowscontainers/about/index)ile, mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürebilir ve bunları Docker ekosisteminin geri kalanı ile aynı araçlarla dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b33e7-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="b33e7-105">Windows kapsayıcıları kullanmak için, aşağıdaki örnekte gösterildiği gibi DockerFile dosyasına Windows PowerShell komutları yazmanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="b33e7-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```dockerfile
FROM mcr.microsoft.com/windows/servercore:ltsc2019
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="b33e7-106">Bu durumda, Windows PowerShell 'i kullanarak Windows Server çekirdek temel görüntüsünü ve IIS 'yi de yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="b33e7-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="b33e7-107">Benzer şekilde, burada gösterildiği gibi geleneksel ASP.NET 4. x ve .NET Framework 4,6 ya da başka bir Windows yazılımı gibi ek bileşenler ayarlamak için Windows PowerShell komutlarını da kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b33e7-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET Framework 4.6 or any other Windows software, as shown here:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="b33e7-108">[Önceki](visual-studio-tools-for-docker.md) 
> [Sonraki](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="b33e7-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
