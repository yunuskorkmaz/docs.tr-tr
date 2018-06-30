---
title: .NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 0f6689468eda1dd1b12c24927e650b2b01381274
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104448"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="aadc5-103">.NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme</span><span class="sxs-lookup"><span data-stu-id="aadc5-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="aadc5-104">.NET ile Docker uygulamaları kapsayıcılı sunucu tarafı oluşturmak için iki desteklenen uygulamalar şunlardır: [.NET Framework](https://www.microsoft.com/net/download/framework) ve [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="aadc5-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="aadc5-105">Birçok .NET standart bileşen paylaştıkları ve kodu arasında iki paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aadc5-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="aadc5-106">Ancak, bunları ve kullandığınız hangi uygulama gerçekleştirmek istediğinize göre değişir arasındaki temel farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="aadc5-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="aadc5-107">Bu bölümde her uygulama seçmek ne zaman hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aadc5-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="aadc5-108">[Önceki](../container-docker-introduction/docker-containers-images-registries.md)
[sonraki](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="aadc5-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
