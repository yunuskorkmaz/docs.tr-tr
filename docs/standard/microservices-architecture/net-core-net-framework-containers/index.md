---
title: Docker kapsayıcıları için .NET Core ve .NET Framework arasında seçim
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker kapsayıcıları için .NET Core ve .NET Framework arasında seçim
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 9abff2614e4022408a069be25440196111db19ab
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638866"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="3a4d5-103">Docker kapsayıcıları için .NET Core ve .NET Framework arasında seçim</span><span class="sxs-lookup"><span data-stu-id="3a4d5-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="3a4d5-104">Docker uygulamaları .NET ile kapsayıcılı hale sunucu tarafı oluşturmak için iki desteklenen çerçeveler şunlardır: [.NET Framework ve .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="3a4d5-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="3a4d5-105">Birçok .NET platformu bileşenleri paylaşır ve ikisi arasında kod paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4d5-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="3a4d5-106">Ancak, bunları ve kullandığınız hangi framework gerçekleştirmek istediğinize göre değişir arasındaki temel farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="3a4d5-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="3a4d5-107">Bu bölümde, ne zaman her bir çerçeve seçin hakkında yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a4d5-107">This section provides guidance on when to choose each framework.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3a4d5-108">[Önceki](../container-docker-introduction/docker-containers-images-registries.md)
[İleri](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="3a4d5-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
