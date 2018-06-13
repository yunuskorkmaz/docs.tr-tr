---
title: .NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b483214e7bd039a71ae642aa26e69d63222af8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580133"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="d3b95-103">.NET Core ve .NET Framework arasında Docker kapsayıcıları için seçme</span><span class="sxs-lookup"><span data-stu-id="d3b95-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="d3b95-104">.NET ile Docker uygulamaları kapsayıcılı sunucu tarafı oluşturmak için iki desteklenen uygulamalar şunlardır: [.NET Framework](https://www.microsoft.com/net/download/framework) ve [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="d3b95-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="d3b95-105">Birçok .NET standart bileşen paylaştıkları ve kodu arasında iki paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3b95-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="d3b95-106">Ancak, bunları ve kullandığınız hangi uygulama gerçekleştirmek istediğinize göre değişir arasındaki temel farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="d3b95-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="d3b95-107">Bu bölümde her uygulama seçmek ne zaman hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3b95-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d3b95-108">[Önceki] (.. / container-docker-introduction/docker-containers-images-registries.md) [sonraki] (genel-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="d3b95-108">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
