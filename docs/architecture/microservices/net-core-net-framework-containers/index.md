---
title: .NET Core ve Docker kapsayıcıları için .NET Framework arasında seçim yapma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET Core ve Docker kapsayıcıları için .NET Framework arasında seçim yapma
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849280"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="3c730-103">.NET Core ve Docker kapsayıcıları için .NET Framework arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="3c730-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="3c730-104">.NET: [.NET Framework ve .NET Core](https://dotnet.microsoft.com/download)ile sunucu tarafı Kapsayıcılı Docker uygulamaları oluşturmaya yönelik iki desteklenen çerçeve vardır.</span><span class="sxs-lookup"><span data-stu-id="3c730-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="3c730-105">Bunlar birçok .NET Platform bileşenini paylaşır ve kodu iki arasında paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c730-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="3c730-106">Ancak bunlar arasında temel farklılıklar vardır ve kullandığınız çerçeve, gerçekleştirmek istediğiniz işe göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c730-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="3c730-107">Bu bölüm her bir çerçevenin ne zaman seçlenebileceğine ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c730-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3c730-108">[Önceki](../container-docker-introduction/docker-containers-images-registries.md)
>[İleri](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="3c730-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
