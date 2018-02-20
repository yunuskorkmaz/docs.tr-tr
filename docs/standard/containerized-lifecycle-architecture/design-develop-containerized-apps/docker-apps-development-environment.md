---
title: "Docker uygulamalar için geliştirme ortamı"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad1a6e4cb0974ebb067cf1a7be987d696e8bc82a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="504b7-104">Docker uygulamalar için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="504b7-104">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="504b7-105">Geliştirme araçları seçenekleri: IDE veya Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="504b7-105">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="504b7-106">Tam ve güçlü bir IDE veya basit ve Çevik Düzenleyicisi tercih ederseniz bağımsız Microsoft, Docker uygulamaları geliştirme geldiği zaman kapsamdaki sahiptir.</span><span class="sxs-lookup"><span data-stu-id="504b7-106">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="504b7-107">Visual Studio Code ve Docker CLI (Mac, Linux ve Windows için platformlar arası araçları)</span><span class="sxs-lookup"><span data-stu-id="504b7-107">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="504b7-108">Herhangi bir geliştirme dili destekleyen bir basit, platformlar arası Düzenleyicisi tercih ederseniz, Visual Studio Code ve Docker CLI kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="504b7-108">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="504b7-109">Bu ürünler Geliştirici iş akışı hızlandırma için kritik bir basit ancak güçlü deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="504b7-109">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="504b7-110">"Docker için Mac" veya "Docker için Windows" (geliştirme ortamı) yükleyerek Docker geliştiriciler, Windows veya Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="504b7-110">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="504b7-111">Ayrıca, Visual Studio Code uzantıları Docker Dockerfiles ve kısayol görevleri Düzenleyicisi'nden Docker komutları çalıştırmak için IntelliSense ile destekler.</span><span class="sxs-lookup"><span data-stu-id="504b7-111">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="504b7-112">Visual Studio Code indirmek için Git <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="504b7-112">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="504b7-113">Mac ve Windows için Docker indirmek için Git <http://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="504b7-113">To download Docker for Mac and Windows, go to <http://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="504b7-114">Docker araçları ile Visual Studio</span><span class="sxs-lookup"><span data-stu-id="504b7-114">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="504b7-115">Visual Studio 2015 kullanırken eklenti Araçları "Visual Studio Araçları Docker". yükleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="504b7-115">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="504b7-116">Visual Studio 2017 Docker Araçları zaten içinde yerleşik olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="504b7-116">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="504b7-117">Her iki durumda da geliştirmek, çalıştırmak ve uygulamalarınızı seçilen Docker ortamında doğrudan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="504b7-117">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="504b7-118">F5 uygulamanıza (tek kapsayıcısı veya birden çok kapsayıcı) doğrudan bir Docker hata ayıklama ile ana bilgisayar veya düzenleyin ve kapsayıcı yeniden oluşturmak zorunda kalmadan, uygulamanızın yenilemek için Ctrl + F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="504b7-118">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="504b7-119">Linux veya Windows için Docker kapsayıcıları oluşturma Windows geliştiriciler için basit ve daha güçlü seçenek budur.</span><span class="sxs-lookup"><span data-stu-id="504b7-119">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="504b7-120">Visual Studio için Docker Araçları'nı indirmek için Git <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="504b7-120">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="504b7-121">Dil ve çerçeve seçenekleri</span><span class="sxs-lookup"><span data-stu-id="504b7-121">Language and framework choices</span></span>

<span data-ttu-id="504b7-122">Docker uygulamaları ve çoğu modern dilleri Microsoft araçlarla geliştirme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="504b7-122">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="504b7-123">Başlangıç listesi aşağıda verilmiştir ancak ona sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="504b7-123">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="504b7-124">.NET core ve ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="504b7-124">.NET Core and ASP.NET Core</span></span>

-   <span data-ttu-id="504b7-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="504b7-125">Node.js</span></span>

-   <span data-ttu-id="504b7-126">Golang</span><span class="sxs-lookup"><span data-stu-id="504b7-126">Golang</span></span>

-   <span data-ttu-id="504b7-127">Java</span><span class="sxs-lookup"><span data-stu-id="504b7-127">Java</span></span>

-   <span data-ttu-id="504b7-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="504b7-128">Ruby</span></span>

-   <span data-ttu-id="504b7-129">Python</span><span class="sxs-lookup"><span data-stu-id="504b7-129">Python</span></span>

<span data-ttu-id="504b7-130">Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="504b7-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="504b7-131">[Önceki] (düzenlemek-yüksek-ölçeklenebilirlik-availability.md) [sonraki] (docker-apps-iç-döngü-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="504b7-131">[Previous] (orchestrate-high-scalability-availability.md) [Next] (docker-apps-inner-loop-workflow.md)</span></span>
