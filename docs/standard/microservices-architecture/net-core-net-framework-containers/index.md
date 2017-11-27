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
ms.openlocfilehash: f7a5fee26f4d138ae22f3551a25a674b22a2f6d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="ccc68-104">.NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme</span><span class="sxs-lookup"><span data-stu-id="ccc68-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="ccc68-105">.NET ile Docker uygulamaları kapsayıcılı sunucu tarafı oluşturmak için iki desteklenen uygulamalar şunlardır: [.NET Framework](https://www.microsoft.com/net/download/framework) ve [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="ccc68-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="ccc68-106">Birçok .NET standart bileşen paylaştıkları ve kodu arasında iki paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccc68-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="ccc68-107">Ancak, bunları ve kullandığınız hangi uygulama gerçekleştirmek istediğinize göre değişir arasındaki temel farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="ccc68-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="ccc68-108">Bu bölümde her uygulama seçmek ne zaman hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccc68-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ccc68-109">[Önceki] (.. / container-docker-introduction/docker-containers-images-registries.md) [sonraki] (genel-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="ccc68-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
