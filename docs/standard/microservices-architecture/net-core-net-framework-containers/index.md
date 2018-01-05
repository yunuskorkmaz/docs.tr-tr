---
title: ".NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60d21de06262a14f9be6a1a5ce80edf15ddf1b59
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="8442c-104">.NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme</span><span class="sxs-lookup"><span data-stu-id="8442c-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="8442c-105">.NET ile Docker uygulamaları kapsayıcılı sunucu tarafı oluşturmak için iki desteklenen uygulamalar şunlardır: [.NET Framework](https://www.microsoft.com/net/download/framework) ve [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="8442c-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="8442c-106">Birçok .NET standart bileşen paylaştıkları ve kodu arasında iki paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8442c-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="8442c-107">Ancak, bunları ve kullandığınız hangi uygulama gerçekleştirmek istediğinize göre değişir arasındaki temel farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="8442c-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="8442c-108">Bu bölümde her uygulama seçmek ne zaman hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8442c-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8442c-109">[Önceki] (.. / container-docker-introduction/docker-containers-images-registries.md) [sonraki] (genel-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="8442c-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
