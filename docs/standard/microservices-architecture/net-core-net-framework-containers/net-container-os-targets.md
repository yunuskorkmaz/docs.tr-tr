---
title: "Hedef .NET kapsayıcıları ile hangi işletim sistemi"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Hedef .NET kapsayıcıları ile hangi işletim sistemi"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
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

-   Microsoft /**dotnet:2.0.0-çalışma zamanı-jessie**

        .NET Core 2.0 runtime-only on Linux

-   Microsoft /**dotnet:2.0.0-çalışma zamanı-nanoserver-1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   Microsoft /**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[Önceki] (kapsayıcı-framework-seçim-factors.md) [sonraki] (resmi-net-docker-images.md)
