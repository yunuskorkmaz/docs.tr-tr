---
title: Hedef .NET kapsayıcıları ile hangi işletim sistemi
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Hedef .NET kapsayıcıları ile hangi işletim sistemi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 53b279a3325ae0fb662cd91a6f7f454b765196ff
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251018"
---
# <a name="what-os-to-target-with-net-containers"></a>Hedef .NET kapsayıcıları ile hangi işletim sistemi

Docker ve .NET Framework ve .NET Core arasındaki farklar tarafından desteklenen işletim sistemleri seviyelerine verildiğinde, belirli bir işletim sistemi ve kullandığınız framework bağlı olarak belirli sürümlerini hedefleyen. 

Windows, Windows Server Core veya Windows Nano Server kullanabilirsiniz. Bu Windows sürümlerini .NET Framework veya .NET Core tarafından sırasıyla gerçekleştirmeniz gerekebilecek farklı özellikleri (Windows Server Core Kestrel Nano Server gibi kendi kendini barındıran web sunucusu yerine IIS) sağlar. 

Linux için kullanılabilir ve desteklenen (Debian gibi) resmi .NET Docker görüntülerinde birden çok distro'lar.

Şekil 3-1'de kullanılan .NET framework bağlı olarak olası işletim sistemi sürümü görebilirsiniz.

![](./media/image1.png)

**Şekil 3-1.** .NET framework sürümleri bağlı olarak hedeflemek için işletim sistemleri

Farklı Linux distro kullanmak istediğiniz veya görüntü Microsoft tarafından sağlanmayan sürümleriyle istediğiniz durumlarda de kendi Docker görüntü oluşturabilirsiniz. Örneğin, ASP.NET geleneksel .NET Framework ve Docker değil pek yaygın senaryodur Windows Server Core üzerinde çalışan temel bir görüntü oluşturabilirsiniz.

Görüntü adı Dockerfile dosyanızı eklediğinizde, işletim sistemi ve sürümüne bağlı olarak, aşağıdaki örneklerde olduğu gibi kullandığınız etiketi seçebilirsiniz:

-   Microsoft /**dotnet:2.1-çalışma zamanı**

        .NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.

-   Microsoft /**dotnet:2.1-aspnetcore-çalışma zamanı**
    
        ASP.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 

-   Microsoft /**dotnet:2.1-aspnetcore-çalışma zamanı-alpine** 

        .NET Core 2.1 runtime-only on Linux Alpine distro

-   Microsoft /**dotnet:2.1-aspnetcore-çalışma zamanı-nanoserver-1803** 

        .NET Core 2.1 runtime-only on Windows Nano Server (Windows Server version 1803)




>[!div class="step-by-step"]
[Önceki] (kapsayıcı-framework-seçim-factors.md) [sonraki] (resmi-net-docker-images.md)
