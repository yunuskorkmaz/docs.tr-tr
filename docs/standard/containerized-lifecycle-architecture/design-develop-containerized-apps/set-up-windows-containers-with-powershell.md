---
title: "(Standart Docker tabanlı) Windows kapsayıcıları ayarlamak için bir DockerFile Windows PowerShell komutlarını kullanma"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3c9a4bec4f48d988ecf8c75ff340300b83a1faef
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>(Standart Docker tabanlı) Windows kapsayıcıları ayarlamak için bir DockerFile Windows PowerShell komutlarını kullanma

İle [Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), var olan Windows uygulamalarınız Docker resimlere dönüştürmek ve bunları Docker ekosistemi geri kalanı ile aynı araçlarıyla dağıtabilirsiniz.

Windows kapsayıcılar kullanmak için Windows PowerShell komutları DockerFile, yazma aşağıdaki örnekte gösterildiği gibi yeterlidir:

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, biz IIS yanı sıra bir Windows Server Core temel görüntü yüklemek için Windows PowerShell kullanıyorsanız.

Benzer şekilde, aynı zamanda Windows PowerShell komutlarını geleneksel ASP.NET gibi ek bileşenleri ayarlamak için kullanabileceğinizi 4.x ve .NET 4.6 ya da aşağıda gösterildiği gibi tüm diğer Windows yazılım:

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
[Önceki] (visual-studio-araçları-için-docker.md) [sonraki] (.. /docker-devops-Workflow/index.MD)
