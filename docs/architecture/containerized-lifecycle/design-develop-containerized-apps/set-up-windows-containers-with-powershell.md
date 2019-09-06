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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="a47a5-103">Windows kapsayıcıları ayarlamak için bir DockerFile içindeki Windows PowerShell komutlarını kullanma (Docker Standard tabanlı)</span><span class="sxs-lookup"><span data-stu-id="a47a5-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="a47a5-104">[Windows kapsayıcıları](/virtualization/windowscontainers/about/index)ile, mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürebilir ve bunları Docker ekosisteminin geri kalanı ile aynı araçlarla dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47a5-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="a47a5-105">Windows kapsayıcıları kullanmak için, aşağıdaki örnekte gösterildiği gibi DockerFile dosyasına Windows PowerShell komutları yazmanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="a47a5-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="a47a5-106">Bu durumda, Windows PowerShell 'i kullanarak Windows Server çekirdek temel görüntüsünü ve IIS 'yi de yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="a47a5-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="a47a5-107">Benzer şekilde, burada gösterildiği gibi geleneksel ASP.NET 4. x ve .NET 4,6 veya diğer Windows yazılımları gibi ek bileşenleri ayarlamak için Windows PowerShell komutlarını da kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a47a5-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="a47a5-108">[Önceki](visual-studio-tools-for-docker.md)İleri
>[](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="a47a5-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
