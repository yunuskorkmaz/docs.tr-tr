---
title: Windows kapsayıcıları (Docker standardına göre) ayarlamak için bir DockerFile içinde Windows PowerShell komutlarını kullanarak
description: Windows kapsayıcıları Docker kullanmaya çalışırken PowerShell kullanmayı öğrenin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: df9e98e3f963b6492e1008455251b61a8cb6e771
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219977"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="24dd8-103">Windows kapsayıcıları (Docker standardına göre) ayarlamak için bir DockerFile içinde Windows PowerShell komutlarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="24dd8-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="24dd8-104">İle [Windows kapsayıcıları](/virtualization/windowscontainers/about/index), mevcut Windows uygulamalarınızı Docker görüntülerini dönüştürme ve Docker ekosistemi sayesinde geri kalanı gibi aynı araçları ile dağıtın.</span><span class="sxs-lookup"><span data-stu-id="24dd8-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="24dd8-105">Windows kapsayıcıları kullanmak için bir DockerFile içinde Windows PowerShell komutları yazmak aşağıdaki örnekte gösterildiği gibi yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="24dd8-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="24dd8-106">Bu durumda, bir Windows Server Core temel görüntü yanı sıra IIS yüklemek için Windows PowerShell kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="24dd8-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="24dd8-107">Benzer şekilde, aynı zamanda Windows PowerShell komutlarını geleneksel ASP.NET gibi ek bileşenler ayarlamak için kullanabileceğinizi 4.x ve .NET 4.6 veya burada gösterildiği gibi herhangi diğer Windows yazılımlar:</span><span class="sxs-lookup"><span data-stu-id="24dd8-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="24dd8-108">[Önceki](visual-studio-tools-for-docker.md)
>[İleri](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="24dd8-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
