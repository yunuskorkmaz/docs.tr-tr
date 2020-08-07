---
title: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
description: Docker ve Microsoft platformu ve araçları ile Kapsayıcılı uygulamalar geliştirmeye ve dağıtmaya yönelik geliştirme ve dağıtım sürecine ileri düzey bir genel bakış alın.
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915163"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="2b321-103">Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="2b321-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Kitap kapağı](./media/devops-book-cover-large-we.png)

<span data-ttu-id="2b321-105">**Sürüm v 3.1** -ASP.NET Core 3,1 ' ye güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="2b321-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="2b321-106">Bu kılavuz, Microsoft platformu ve araçları kullanılarak Docker ile Kapsayıcılı ASP.NET Core uygulamalar geliştirmeye ve dağıtmaya yönelik genel bir genel bakıştır.</span><span class="sxs-lookup"><span data-stu-id="2b321-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="2b321-107">Kılavuz, CI/CD işlem hatlarının yanı sıra Azure Container Registry (ACR) ve Azure Kubernetes Hizmetleri AKS ' i dağıtmak için Azure DevOps 'a yönelik yüksek düzeyde bir giriş içerir.</span><span class="sxs-lookup"><span data-stu-id="2b321-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="2b321-108">Düşük düzey, geliştirmeyle ilgili ayrıntılar için [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları](https://docs.microsoft.com/dotnet/architecture/microservices/) Kılavuzu ve BT ile ilgili başvuru uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers)için mimari görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b321-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="2b321-109">Görüşlerinizi bize gönderin!</span><span class="sxs-lookup"><span data-stu-id="2b321-109">Send us your feedback!</span></span>

<span data-ttu-id="2b321-110">.NET 'teki Kapsayıcılı uygulamaların ve mikro hizmetlerin mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdık.</span><span class="sxs-lookup"><span data-stu-id="2b321-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="2b321-111">Kılavuz ve ilgili başvuru uygulaması geliştireceğiz, bu nedenle geri bildirimlerinize hoş geldiniz!</span><span class="sxs-lookup"><span data-stu-id="2b321-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="2b321-112">Bu kılavuzun nasıl iyileştirilen hakkında açıklamalara sahipseniz, konusunda geri bildirimde bulunun <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="2b321-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="2b321-113">Krediler</span><span class="sxs-lookup"><span data-stu-id="2b321-113">Credits</span></span>

<span data-ttu-id="2b321-114">Yazar:</span><span class="sxs-lookup"><span data-stu-id="2b321-114">Author:</span></span>

> <span data-ttu-id="2b321-115">**Cesar de La Torre**, SR. PM, .net ürün ekibi, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="2b321-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="2b321-116">Alım Düzenleyicisi:</span><span class="sxs-lookup"><span data-stu-id="2b321-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="2b321-117">**Ida Patrick**</span><span class="sxs-lookup"><span data-stu-id="2b321-117">**Janine Patrick**</span></span>

<span data-ttu-id="2b321-118">Geliştirme Düzenleyicisi:</span><span class="sxs-lookup"><span data-stu-id="2b321-118">Developmental Editor:</span></span>

> <span data-ttu-id="2b321-119">**Bob Russatı**, Microsoft 'Ta çözüm uzmanı</span><span class="sxs-lookup"><span data-stu-id="2b321-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="2b321-120">**Sekizlik yayımlama, Inc.**</span><span class="sxs-lookup"><span data-stu-id="2b321-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="2b321-121">Düzenleme üretimi:</span><span class="sxs-lookup"><span data-stu-id="2b321-121">Editorial Production:</span></span>

> [<span data-ttu-id="2b321-122">Dianne Russati</span><span class="sxs-lookup"><span data-stu-id="2b321-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="2b321-123">**Sekizlik yayımlama, Inc.**</span><span class="sxs-lookup"><span data-stu-id="2b321-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="2b321-124">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="2b321-124">Copyeditor:</span></span>

> <span data-ttu-id="2b321-125">**Bob Russatı**, Microsoft 'Ta çözüm uzmanı</span><span class="sxs-lookup"><span data-stu-id="2b321-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="2b321-126">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="2b321-126">Participants and reviewers:</span></span>

> <span data-ttu-id="2b321-127">**Hayvan anıl**, SR. Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="2b321-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="2b321-128">**MIGUEL Veloso**, düz kavramlarda yazılım geliştirme mühendisi</span><span class="sxs-lookup"><span data-stu-id="2b321-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="2b321-129">**Sumit Ghosh**, sorumlu danışman Neudesic</span><span class="sxs-lookup"><span data-stu-id="2b321-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="2b321-130">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="2b321-130">Copyright</span></span>

<span data-ttu-id="2b321-131">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="2b321-131">PUBLISHED BY</span></span>

<span data-ttu-id="2b321-132">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="2b321-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="2b321-133">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="2b321-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="2b321-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="2b321-134">One Microsoft Way</span></span>

<span data-ttu-id="2b321-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="2b321-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="2b321-136">Telif hakkı &copy; 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2b321-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="2b321-137">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="2b321-137">All rights reserved.</span></span> <span data-ttu-id="2b321-138">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b321-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="2b321-139">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="2b321-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="2b321-140">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b321-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="2b321-141">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="2b321-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="2b321-142">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b321-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="2b321-143">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="2b321-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="2b321-144">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="2b321-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="2b321-145">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="2b321-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="2b321-146">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="2b321-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="2b321-147">Sonraki</span><span class="sxs-lookup"><span data-stu-id="2b321-147">Next</span></span>](introduction-to-containers-and-docker.md)
