---
title: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
description: Docker ve Microsoft platformu ve araçları ile Kapsayıcılı uygulamalar geliştirmeye ve dağıtmaya yönelik geliştirme ve dağıtım sürecine ileri düzey bir genel bakış alın.
ms.date: 07/30/2020
ms.openlocfilehash: c506a3423ac4511f23452192e361e88dce6efec4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160703"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="196ff-103">Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="196ff-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Kitap kapağı](./media/devops-book-cover-large-we.png)

<span data-ttu-id="196ff-105">**Sürüm v 3.1** -ASP.NET Core 3,1 ' ye güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="196ff-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="196ff-106">Bu kılavuz, Microsoft platformu ve araçları kullanılarak Docker ile Kapsayıcılı ASP.NET Core uygulamalar geliştirmeye ve dağıtmaya yönelik genel bir genel bakıştır.</span><span class="sxs-lookup"><span data-stu-id="196ff-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="196ff-107">Kılavuz, CI/CD işlem hatlarının yanı sıra Azure Container Registry (ACR) ve Azure Kubernetes Hizmetleri AKS ' i dağıtmak için Azure DevOps 'a yönelik yüksek düzeyde bir giriş içerir.</span><span class="sxs-lookup"><span data-stu-id="196ff-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="196ff-108">Düşük düzey, geliştirmeyle ilgili ayrıntılar için [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları](../microservices/index.md) Kılavuzu ve BT ile ilgili başvuru uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers)için mimari görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="196ff-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](../microservices/index.md) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="196ff-109">Bize geri bildirimlerinizi gönderin!</span><span class="sxs-lookup"><span data-stu-id="196ff-109">Send us your feedback!</span></span>

<span data-ttu-id="196ff-110">.NET 'teki Kapsayıcılı uygulamaların ve mikro hizmetlerin mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdık.</span><span class="sxs-lookup"><span data-stu-id="196ff-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="196ff-111">Kılavuz ve ilgili başvuru uygulaması geliştireceğiz, bu nedenle geri bildirimlerinize hoş geldiniz!</span><span class="sxs-lookup"><span data-stu-id="196ff-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="196ff-112">Bu kılavuzun nasıl iyileştirilen hakkında açıklamalara sahipseniz, konusunda geri bildirimde bulunun <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="196ff-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="196ff-113">Krediler</span><span class="sxs-lookup"><span data-stu-id="196ff-113">Credits</span></span>

<span data-ttu-id="196ff-114">Yazar:</span><span class="sxs-lookup"><span data-stu-id="196ff-114">Author:</span></span>

> <span data-ttu-id="196ff-115">**Cesar de La Torre**, SR. PM, .net ürün ekibi, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="196ff-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="196ff-116">Alım Düzenleyicisi:</span><span class="sxs-lookup"><span data-stu-id="196ff-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="196ff-117">**Ida Patrick**</span><span class="sxs-lookup"><span data-stu-id="196ff-117">**Janine Patrick**</span></span>

<span data-ttu-id="196ff-118">Geliştirme Düzenleyicisi:</span><span class="sxs-lookup"><span data-stu-id="196ff-118">Developmental Editor:</span></span>

> <span data-ttu-id="196ff-119">**Bob Russatı**, Microsoft 'Ta çözüm uzmanı</span><span class="sxs-lookup"><span data-stu-id="196ff-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="196ff-120">**Sekizlik yayımlama, Inc.**</span><span class="sxs-lookup"><span data-stu-id="196ff-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="196ff-121">Düzenleme üretimi:</span><span class="sxs-lookup"><span data-stu-id="196ff-121">Editorial Production:</span></span>

> [<span data-ttu-id="196ff-122">Dianne Russati</span><span class="sxs-lookup"><span data-stu-id="196ff-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="196ff-123">**Sekizlik yayımlama, Inc.**</span><span class="sxs-lookup"><span data-stu-id="196ff-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="196ff-124">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="196ff-124">Copyeditor:</span></span>

> <span data-ttu-id="196ff-125">**Bob Russatı**, Microsoft 'Ta çözüm uzmanı</span><span class="sxs-lookup"><span data-stu-id="196ff-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="196ff-126">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="196ff-126">Participants and reviewers:</span></span>

> <span data-ttu-id="196ff-127">**Hayvan anıl**, SR. Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="196ff-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="196ff-128">**MIGUEL Veloso**, düz kavramlarda yazılım geliştirme mühendisi</span><span class="sxs-lookup"><span data-stu-id="196ff-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="196ff-129">**Sumit Ghosh**, sorumlu danışman Neudesic</span><span class="sxs-lookup"><span data-stu-id="196ff-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="196ff-130">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="196ff-130">Copyright</span></span>

<span data-ttu-id="196ff-131">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="196ff-131">PUBLISHED BY</span></span>

<span data-ttu-id="196ff-132">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="196ff-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="196ff-133">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="196ff-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="196ff-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="196ff-134">One Microsoft Way</span></span>

<span data-ttu-id="196ff-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="196ff-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="196ff-136">Telif hakkı &copy; 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="196ff-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="196ff-137">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="196ff-137">All rights reserved.</span></span> <span data-ttu-id="196ff-138">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="196ff-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="196ff-139">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="196ff-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="196ff-140">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="196ff-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="196ff-141">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="196ff-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="196ff-142">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="196ff-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="196ff-143">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="196ff-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="196ff-144">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="196ff-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="196ff-145">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="196ff-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="196ff-146">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="196ff-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="196ff-147">Sonraki</span><span class="sxs-lookup"><span data-stu-id="196ff-147">Next</span></span>](introduction-to-containers-and-docker.md)
