---
title: .NET 5 ve Docker kapsayıcıları için .NET Framework arasında seçim yapma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET 5 ve Docker kapsayıcıları için .NET Framework arasında seçim yapma
ms.date: 02/02/2021
ms.openlocfilehash: 5c3d4eff00399c8a6a041daaa71cf9fe5c9d854f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665165"
---
# <a name="choosing-between-net-5-and-net-framework-for-docker-containers"></a><span data-ttu-id="020a7-103">.NET 5 ve Docker kapsayıcıları için .NET Framework arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="020a7-103">Choosing Between .NET 5 and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="020a7-104">.NET: [.NET Framework ve .NET 5](https://dotnet.microsoft.com/download)ile sunucu tarafı Kapsayıcılı Docker uygulamaları oluşturmaya yönelik iki desteklenen çerçeve vardır.</span><span class="sxs-lookup"><span data-stu-id="020a7-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET 5](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="020a7-105">Bunlar birçok .NET Platform bileşenini paylaşır ve kodu iki arasında paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="020a7-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="020a7-106">Ancak bunlar arasında temel farklılıklar vardır ve kullandığınız çerçeve, gerçekleştirmek istediğiniz işe göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="020a7-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="020a7-107">Bu bölüm her bir çerçevenin ne zaman seçlenebileceğine ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="020a7-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="020a7-108">[Önceki](../container-docker-introduction/docker-containers-images-registries.md) 
> [Sonraki](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="020a7-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
