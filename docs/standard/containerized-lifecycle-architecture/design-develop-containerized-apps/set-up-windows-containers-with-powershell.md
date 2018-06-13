---
title: (Standart Docker tabanlı) Windows kapsayıcıları ayarlamak için bir DockerFile Windows PowerShell komutlarını kullanma
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 48af11117ec8eb0034d9557a332b89d3418d4b31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567864"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="727f6-103">(Standart Docker tabanlı) Windows kapsayıcıları ayarlamak için bir DockerFile Windows PowerShell komutlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="727f6-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="727f6-104">İle [Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), var olan Windows uygulamalarınız Docker resimlere dönüştürmek ve bunları Docker ekosistemi geri kalanı ile aynı araçlarıyla dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="727f6-104">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="727f6-105">Windows kapsayıcılar kullanmak için Windows PowerShell komutları DockerFile, yazma aşağıdaki örnekte gösterildiği gibi yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="727f6-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="727f6-106">Bu durumda, biz IIS yanı sıra bir Windows Server Core temel görüntü yüklemek için Windows PowerShell kullanıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="727f6-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="727f6-107">Benzer şekilde, aynı zamanda Windows PowerShell komutlarını geleneksel ASP.NET gibi ek bileşenleri ayarlamak için kullanabileceğinizi 4.x ve .NET 4.6 ya da aşağıda gösterildiği gibi tüm diğer Windows yazılım:</span><span class="sxs-lookup"><span data-stu-id="727f6-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="727f6-108">[Önceki] (visual-studio-araçları-için-docker.md) [sonraki] (.. /docker-devops-Workflow/index.MD)</span><span class="sxs-lookup"><span data-stu-id="727f6-108">[Previous] (visual-studio-tools-for-docker.md) [Next] (../docker-devops-workflow/index.md)</span></span>
