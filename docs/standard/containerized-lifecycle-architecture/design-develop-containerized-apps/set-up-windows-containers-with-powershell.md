---
title: Windows kapsayıcıları (Docker standardına göre) ayarlamak için bir DockerFile içinde Windows PowerShell komutlarını kullanarak
description: Windows kapsayıcıları Docker kullanmaya çalışırken PowerShell kullanmayı öğrenin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: d9c0bc28f62d44eb7471b99c63055ef43da12a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644651"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Windows kapsayıcıları (Docker standardına göre) ayarlamak için bir DockerFile içinde Windows PowerShell komutlarını kullanarak

İle [Windows kapsayıcıları](/virtualization/windowscontainers/about/index), mevcut Windows uygulamalarınızı Docker görüntülerini dönüştürme ve Docker ekosistemi sayesinde geri kalanı gibi aynı araçları ile dağıtın.

Windows kapsayıcıları kullanmak için bir DockerFile içinde Windows PowerShell komutları yazmak aşağıdaki örnekte gösterildiği gibi yeterlidir:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, bir Windows Server Core temel görüntü yanı sıra IIS yüklemek için Windows PowerShell kullanıyoruz.

Benzer şekilde, aynı zamanda Windows PowerShell komutlarını geleneksel ASP.NET gibi ek bileşenler ayarlamak için kullanabileceğinizi 4.x ve .NET 4.6 veya burada gösterildiği gibi herhangi diğer Windows yazılımlar:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Önceki](visual-studio-tools-for-docker.md)
>[İleri](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
