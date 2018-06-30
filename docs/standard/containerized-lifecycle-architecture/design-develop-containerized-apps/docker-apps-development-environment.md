---
title: Docker uygulamalar için geliştirme ortamı
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3da7816127982c3657129561975eed6d1f5aad5a
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104513"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="8f269-103">Docker uygulamalar için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="8f269-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="8f269-104">Geliştirme araçları seçenekleri: IDE veya Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="8f269-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="8f269-105">Tam ve güçlü bir IDE veya basit ve Çevik Düzenleyicisi tercih ederseniz bağımsız Microsoft, Docker uygulamaları geliştirme geldiği zaman kapsamdaki sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8f269-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="8f269-106">Visual Studio Code ve Docker CLI (Mac, Linux ve Windows için platformlar arası araçları)</span><span class="sxs-lookup"><span data-stu-id="8f269-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="8f269-107">Herhangi bir geliştirme dili destekleyen bir basit, platformlar arası Düzenleyicisi tercih ederseniz, Visual Studio Code ve Docker CLI kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f269-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="8f269-108">Bu ürünler Geliştirici iş akışı hızlandırma için kritik bir basit ancak güçlü deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f269-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="8f269-109">"Docker için Mac" veya "Docker için Windows" (geliştirme ortamı) yükleyerek Docker geliştiriciler, Windows veya Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8f269-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="8f269-110">Ayrıca, Visual Studio Code uzantıları Docker Dockerfiles ve kısayol görevleri Düzenleyicisi'nden Docker komutları çalıştırmak için IntelliSense ile destekler.</span><span class="sxs-lookup"><span data-stu-id="8f269-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="8f269-111">Visual Studio Code indirmek için Git <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="8f269-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="8f269-112">Mac ve Windows için Docker indirmek için Git <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="8f269-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="8f269-113">Docker araçları ile Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f269-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="8f269-114">Visual Studio 2015 kullanırken eklenti Araçları "Visual Studio Araçları Docker". yükleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="8f269-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="8f269-115">Visual Studio 2017 Docker Araçları zaten içinde yerleşik olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8f269-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="8f269-116">Her iki durumda da geliştirmek, çalıştırmak ve uygulamalarınızı seçilen Docker ortamında doğrudan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8f269-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="8f269-117">F5 uygulamanıza (tek kapsayıcısı veya birden çok kapsayıcı) doğrudan bir Docker hata ayıklama ile ana bilgisayar veya düzenleyin ve kapsayıcı yeniden oluşturmak zorunda kalmadan, uygulamanızın yenilemek için Ctrl + F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="8f269-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="8f269-118">Linux veya Windows için Docker kapsayıcıları oluşturma Windows geliştiriciler için basit ve daha güçlü seçenek budur.</span><span class="sxs-lookup"><span data-stu-id="8f269-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="8f269-119">Visual Studio için Docker Araçları'nı indirmek için Git <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="8f269-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="8f269-120">Dil ve çerçeve seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8f269-120">Language and framework choices</span></span>

<span data-ttu-id="8f269-121">Docker uygulamaları ve çoğu modern dilleri Microsoft araçlarla geliştirme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f269-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="8f269-122">Başlangıç listesi aşağıda verilmiştir ancak ona sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="8f269-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="8f269-123">.NET core ve ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8f269-123">.NET Core and ASP.NET Core</span></span>
-   <span data-ttu-id="8f269-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="8f269-124">Node.js</span></span>
-   <span data-ttu-id="8f269-125">Golang</span><span class="sxs-lookup"><span data-stu-id="8f269-125">Golang</span></span>
-   <span data-ttu-id="8f269-126">Java</span><span class="sxs-lookup"><span data-stu-id="8f269-126">Java</span></span>
-   <span data-ttu-id="8f269-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="8f269-127">Ruby</span></span>
-   <span data-ttu-id="8f269-128">Python</span><span class="sxs-lookup"><span data-stu-id="8f269-128">Python</span></span>

<span data-ttu-id="8f269-129">Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f269-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8f269-130">[Önceki](orchestrate-high-scalability-availability.md)
[sonraki](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8f269-130">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
