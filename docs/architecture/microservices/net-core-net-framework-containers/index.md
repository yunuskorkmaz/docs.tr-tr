---
title: .NET 5 ve Docker kapsayıcıları için .NET Framework arasında seçim yapma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET 5 ve Docker kapsayıcıları için .NET Framework arasında seçim yapma
ms.date: 01/13/2021
ms.openlocfilehash: 5c7ea1be02722fce7c5784afa89c18defbe4eeaf
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188653"
---
# <a name="choosing-between-net-and-net-framework-for-docker-containers"></a><span data-ttu-id="72dbf-103">Docker kapsayıcıları için .NET ve .NET Framework arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="72dbf-103">Choosing Between .NET and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="72dbf-104">.NET: [.NET Framework ve .NET 5](https://dotnet.microsoft.com/download)ile sunucu tarafı Kapsayıcılı Docker uygulamaları oluşturmaya yönelik iki desteklenen çerçeve vardır.</span><span class="sxs-lookup"><span data-stu-id="72dbf-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET 5](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="72dbf-105">Bunlar birçok .NET Platform bileşenini paylaşır ve kodu iki arasında paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72dbf-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="72dbf-106">Ancak bunlar arasında temel farklılıklar vardır ve kullandığınız çerçeve, gerçekleştirmek istediğiniz işe göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="72dbf-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="72dbf-107">Bu bölüm her bir çerçevenin ne zaman seçlenebileceğine ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="72dbf-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="72dbf-108">[Önceki](../container-docker-introduction/docker-containers-images-registries.md) 
> [Sonraki](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="72dbf-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
