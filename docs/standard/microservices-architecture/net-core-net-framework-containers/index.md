---
title: Docker kapsayıcıları için .NET Core ve .NET Framework arasında seçim
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker kapsayıcıları için .NET Core ve .NET Framework arasında seçim
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 9abff2614e4022408a069be25440196111db19ab
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990927"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="0af45-103">Docker kapsayıcıları için .NET Core ve .NET Framework arasında seçim</span><span class="sxs-lookup"><span data-stu-id="0af45-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="0af45-104">Docker uygulamaları .NET ile kapsayıcılı hale sunucu tarafı oluşturmak için iki desteklenen çerçeveler şunlardır: [.NET Framework ve .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="0af45-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="0af45-105">Birçok .NET platformu bileşenleri paylaşır ve ikisi arasında kod paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0af45-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="0af45-106">Ancak, bunları ve kullandığınız hangi framework gerçekleştirmek istediğinize göre değişir arasındaki temel farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="0af45-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="0af45-107">Bu bölümde, ne zaman her bir çerçeve seçin hakkında yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0af45-107">This section provides guidance on when to choose each framework.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0af45-108">[Önceki](../container-docker-introduction/docker-containers-images-registries.md)
[İleri](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="0af45-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
