---
title: Docker Konteynerler için .NET Core ve .NET Framework arasında seçim
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Docker Konteynerler için .NET Core ve .NET Framework arasında seçim
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70849280"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="f53b5-103">Docker Konteynerler için .NET Core ve .NET Framework arasında seçim</span><span class="sxs-lookup"><span data-stu-id="f53b5-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="f53b5-104">.NET ile sunucu tarafı kapsayıcı Docker uygulamaları oluşturmak için desteklenen iki çerçeve vardır: [.NET Framework ve .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="f53b5-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="f53b5-105">Birçok .NET platform bileşenini paylaşırlar ve kodu ikisi arasında paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f53b5-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="f53b5-106">Ancak, aralarında temel farklılıklar vardır ve hangi çerçeveyi kullandığınız neyi başarmak istediğinize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f53b5-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="f53b5-107">Bu bölümde, her bir çerçevenin ne zaman seçileceklerine ilişkin kılavuzluk sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f53b5-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f53b5-108">[Önceki](../container-docker-introduction/docker-containers-images-registries.md)
>[Sonraki](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="f53b5-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
