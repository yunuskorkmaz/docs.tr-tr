---
title: "Geliştirme işlemi için Docker tabanlı uygulamaları"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Geliştirme işlemi için Docker tabanlı uygulamaları"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 97dfa3261c8ddc7a869b0991673b7a8d298972dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="9dc2d-104">Docker tabanlı uygulamalar için geliştirme işlemi</span><span class="sxs-lookup"><span data-stu-id="9dc2d-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="9dc2d-105">*Kapsayıcılı .NET uygulamaları, istediğiniz şekilde Visual Studio ve Visual Studio Araçları ile için Docker odaklanmış IDE veya CLI/Düzenleyicisi Docker CLI ve Visual Studio Code ile odaklanmış geliştirin.*</span><span class="sxs-lookup"><span data-stu-id="9dc2d-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="9dc2d-106">Docker uygulamalar için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="9dc2d-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="9dc2d-107">Geliştirme aracı seçenekleri: IDE veya Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="9dc2d-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="9dc2d-108">Microsoft, tam ve güçlü bir IDE ya da basit ve Çevik Düzenleyicisi tercih olsun, Docker uygulamaları geliştirmek için kullanabileceğiniz araçlar sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="9dc2d-109">**Visual Studio (Windows için)**.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-109">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="9dc2d-110">Docker tabanlı uygulamalar geliştirmek için Visual Studio 2017 veya Docker zaten yerleşik araçlarıyla birlikte gelir sonraki sürümlerinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-110">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="9dc2d-111">Docker için araçları geliştirmek, çalıştırmak ve uygulamalarınızda doğrudan hedef Docker ortam doğrulamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-111">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="9dc2d-112">Çalıştırın ve uygulamanızda (tek kapsayıcısı veya birden çok kapsayıcı) doğrudan bir Docker ana hata ayıklama için F5 tuşuna basın veya düzenleyin ve kapsayıcı yeniden oluşturmak zorunda kalmadan, uygulamanızın yenilemek için CTRL + F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-112">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="9dc2d-113">Bu Docker tabanlı uygulamalar için en güçlü geliştirme seçimdir.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-113">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="9dc2d-114">**Mac için Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-114">**Visual Studio for Mac**.</span></span> <span data-ttu-id="9dc2d-115">Bu, bir IDE macOS üzerinde çalışır ve Docker tabanlı uygulama geliştirme destekleyen Xamarin Studio evrimi olur.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-115">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="9dc2d-116">Bu Mac makinelerinizde çalışma de güçlü bir IDE kullanmak isteyen geliştiriciler için tercih edilen seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-116">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="9dc2d-117">**Visual Studio Code ve Docker CLI**.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-117">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="9dc2d-118">Herhangi bir geliştirme dili destekleyen bir basit ve platformlar arası Düzenleyicisi tercih ederseniz, Microsoft Visual Studio Code (VS Code) ve Docker CLI kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-118">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="9dc2d-119">Bu, Mac, Linux ve Windows için platformlar arası geliştirme yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-119">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="9dc2d-120">Yükleyerek [Docker Community Edition (CE)](https://www.docker.com/community-edition) araçları, Windows ve Linux için uygulamalar oluşturmak için tek bir Docker CLI kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-120">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="9dc2d-121">Ayrıca, Visual Studio Code Docker Düzenleyicisi'nden Docker komutları çalıştırmak için Dockerfiles ve kısayol görevleri için IntelliSense gibi uzantıları destekler.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-121">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9dc2d-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9dc2d-122">Additional resources</span></span>

-   <span data-ttu-id="9dc2d-123">**Docker için Visual Studio Araçları**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="9dc2d-123">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="9dc2d-124">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-124">**Visual Studio Code**.</span></span> <span data-ttu-id="9dc2d-125">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-125">Official site.</span></span>
    [<span data-ttu-id="9dc2d-126">*https://Code.VisualStudio.com/download*</span><span class="sxs-lookup"><span data-stu-id="9dc2d-126">*https://code.visualstudio.com/download*</span></span>](https://code.visualstudio.com/download)

-   <span data-ttu-id="9dc2d-127">**Mac ve Windows için docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="9dc2d-127">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="9dc2d-128">.NET dilleri ve çerçeveleri Docker kapsayıcıları için</span><span class="sxs-lookup"><span data-stu-id="9dc2d-128">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="9dc2d-129">Geliştirme Docker .NET uygulamaları kapsayıcılı olduğunda bu kılavuzun önceki bölümlerinde belirtildiği gibi .NET Framework, .NET Core ve açık kaynaklı Mono proje kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-129">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="9dc2d-130">C'de geliştirebilirsiniz\#, F\#, ya da Linux veya Windows kapsayıcıları, bağlı olarak hangi .NET framework kullanılıyor hedeflerken Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9dc2d-130">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="9dc2d-131">Daha fazla ayrıntı about.NET diller için blog gönderisine bakın [.NET dil stratejisi](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="9dc2d-131">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9dc2d-132">[Önceki] (.. / architect-microservice-container-applications/using-azure-service-fabric.md) [sonraki] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9dc2d-132">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
