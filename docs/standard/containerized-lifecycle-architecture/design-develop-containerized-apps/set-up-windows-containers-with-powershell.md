---
title: Windows kapsayıcıları (Docker standardına göre) ayarlamak için bir DockerFile içinde Windows PowerShell komutlarını kullanarak
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 5e85beea0efbee6a2b6594e3a49d705505a36e1c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149399"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Windows kapsayıcıları (Docker standardına göre) ayarlamak için bir DockerFile içinde Windows PowerShell komutlarını kullanarak

İle [Windows kapsayıcıları](/virtualization/windowscontainers/about/index), mevcut Windows uygulamalarınızı Docker görüntülerini dönüştürme ve Docker ekosistemi sayesinde geri kalanı gibi aynı araçları ile dağıtın.

Windows kapsayıcıları kullanmak için bir DockerFile içinde Windows PowerShell komutları yazmak aşağıdaki örnekte gösterildiği gibi yeterlidir:

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, bir Windows Server Core temel görüntü yanı sıra IIS yüklemek için Windows PowerShell kullanıyoruz.

Benzer şekilde, aynı zamanda Windows PowerShell komutlarını geleneksel ASP.NET gibi ek bileşenler ayarlamak için kullanabileceğinizi 4.x ve .NET 4.6 veya burada gösterildiği gibi herhangi diğer Windows yazılımlar:

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Önceki](visual-studio-tools-for-docker.md)
>[İleri](../docker-devops-workflow/index.md)
