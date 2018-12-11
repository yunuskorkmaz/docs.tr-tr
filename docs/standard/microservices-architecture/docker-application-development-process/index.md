---
title: Geliştirme işlemi için Docker tabanlı uygulamalar
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Geliştirme işlemi için Docker tabanlı uygulamalar
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 7736c1fe4cb1a2a4553ba36cecceab37e2fe90c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144474"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="2006a-103">Docker tabanlı uygulamalar için geliştirme işlemi</span><span class="sxs-lookup"><span data-stu-id="2006a-103">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="2006a-104">*Kapsayıcılı .NET uygulamaları, istediğiniz şekilde Docker için Visual Studio ve Visual Studio Araçları ile odaklanmış IDE veya CLI/düzenleyici ile Docker CLI ve Visual Studio Code odaklı geliştirin.*</span><span class="sxs-lookup"><span data-stu-id="2006a-104">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="2006a-105">Docker uygulamaları için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="2006a-105">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="2006a-106">Geliştirme aracı seçenekleri: IDE veya düzenleyici</span><span class="sxs-lookup"><span data-stu-id="2006a-106">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="2006a-107">Tam ve güçlü bir IDE ya da basit ve Çevik bir düzenleyici tercih olsun, Microsoft Docker uygulamaları geliştirmek için kullanabileceğiniz araçları vardır.</span><span class="sxs-lookup"><span data-stu-id="2006a-107">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="2006a-108">**Visual Studio (Windows)**.</span><span class="sxs-lookup"><span data-stu-id="2006a-108">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="2006a-109">Docker tabanlı uygulamalar geliştirmek için Visual Studio 2017 veya zaten yerleşik için Docker araçları ile birlikte gelen sonraki sürümleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2006a-109">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="2006a-110">Geliştirin, çalıştırın ve uygulamalarınızı doğrudan hedef Docker ortamında doğrulamak için Docker araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="2006a-110">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="2006a-111">F5 tuşuna basarak çalıştırın ve doğrudan bir Docker Konağı (tek kapsayıcı ya da birden çok kapsayıcı), uygulamanızın hata ayıklama veya düzenleyin ve kapsayıcıyı yeniden derlemeye gerek kalmadan uygulamanızı yenilemek için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="2006a-111">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="2006a-112">Docker tabanlı uygulamalar için en güçlü geliştirme seçenek budur.</span><span class="sxs-lookup"><span data-stu-id="2006a-112">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="2006a-113">**Mac için Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2006a-113">**Visual Studio for Mac**.</span></span> <span data-ttu-id="2006a-114">Bu, bir IDE macOS üzerinde çalışır ve Docker tabanlı uygulama geliştirmeyi destekleyen Xamarin Studio evrimi olur.</span><span class="sxs-lookup"><span data-stu-id="2006a-114">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="2006a-115">Bu da güçlü bir IDE kullanmak isteyen Mac makinelerinizde çalışan geliştiriciler için tercih edilen seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2006a-115">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="2006a-116">**Visual Studio Code ve Docker CLI**.</span><span class="sxs-lookup"><span data-stu-id="2006a-116">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="2006a-117">Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyici tercih ederseniz, Microsoft Visual Studio Code (VS Code) ve Docker CLI'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2006a-117">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="2006a-118">Bu, Mac, Linux ve Windows için platformlar arası geliştirme yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="2006a-118">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="2006a-119">Yükleyerek [Docker Community Edition'ı (CE)](https://www.docker.com/community-edition) araçları, Windows ve Linux için uygulamalar oluşturmak için tek bir Docker CLI'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2006a-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="2006a-120">Ayrıca, Visual Studio Code için Docker düzenleyiciden Docker komutlarını çalıştırmak için dockerfile'ları ve kısayol görevler için IntelliSense gibi uzantıları destekler.</span><span class="sxs-lookup"><span data-stu-id="2006a-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2006a-121">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2006a-121">Additional resources</span></span>

-   <span data-ttu-id="2006a-122">**Docker için Visual Studio Araçları**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="2006a-122">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="2006a-123">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="2006a-123">**Visual Studio Code**.</span></span> <span data-ttu-id="2006a-124">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="2006a-124">Official site.</span></span>
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   <span data-ttu-id="2006a-125">**Mac ve Windows için docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="2006a-125">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="2006a-126">.NET dil ve çerçeveyi kullanabilmek için Docker kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="2006a-126">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="2006a-127">Geliştirme Docker kapsayıcılı .NET uygulamaları, bu kılavuzun önceki bölümlerde belirtildiği gibi .NET Framework, .NET Core ve açık kaynaklı Mono projesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2006a-127">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="2006a-128">C'de geliştirebilirsiniz\#, F\#, ya da Linux veya Windows kapsayıcıları, bağlı olarak hangi .NET framework, kullanımda olan hedeflenirken VisualBasic.</span><span class="sxs-lookup"><span data-stu-id="2006a-128">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="2006a-129">Daha fazla ayrıntı about.NET diller için blog gönderisine bakın [.NET dil stratejisi](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="2006a-129">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2006a-130">[Önceki](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[İleri](docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2006a-130">[Previous](../architect-microservice-container-applications/using-azure-service-fabric.md)
[Next](docker-app-development-workflow.md)</span></span>