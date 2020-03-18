---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsünü destekleyen en önemli geliştirme aracı seçeneklerini tanıyın.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71214297"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="b6836-103">Docker uygulamaları için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="b6836-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="b6836-104">Geliştirme araçları seçenekleri: IDE veya düzenleyici</span><span class="sxs-lookup"><span data-stu-id="b6836-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="b6836-105">Tam ve güçlü bir IDE veya hafif ve çevik bir düzenleyici tercih ederseniz edin, Microsoft docker uygulamaları geliştirme söz konusu olduğunda size kapalı vardır.</span><span class="sxs-lookup"><span data-stu-id="b6836-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="b6836-106">Visual Studio Code ve Docker CLI (Mac, Linux ve Windows için çapraz platform araçları)</span><span class="sxs-lookup"><span data-stu-id="b6836-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="b6836-107">Herhangi bir geliştirme dilini destekleyen hafif, çapraz platform düzenleyicisini tercih ederseniz, Visual Studio Code ve Docker CLI'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6836-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="b6836-108">Bu ürünler, geliştirici iş akışını kolaylaştırmak için kritik öneme sahip basit ama sağlam bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6836-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="b6836-109">Docker geliştiricileri "Docker for Mac" veya "Docker for Windows" (geliştirme ortamı) yazılımlarını yükleyerek, hem Windows hem de Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI kullanabilirler.</span><span class="sxs-lookup"><span data-stu-id="b6836-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="b6836-110">Ayrıca, Visual Studio Code, Docker dosyaları için IntelliSense ile Docker uzantılarını ve editörden Docker komutlarını çalıştırmak için kısayol görevlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="b6836-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="b6836-111">Visual Studio Code'u <https://code.visualstudio.com/download>indirmek için .</span><span class="sxs-lookup"><span data-stu-id="b6836-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="b6836-112">Mac ve Windows için Docker'ı <https://www.docker.com/products/docker>indirmek için .</span><span class="sxs-lookup"><span data-stu-id="b6836-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="b6836-113">Docker Tools ile Visual Studio (Windows geliştirme makinesi)</span><span class="sxs-lookup"><span data-stu-id="b6836-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="b6836-114">Yerleşik Docker Tools etkinken Visual Studio 2017 (veya sonraki) kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="b6836-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="b6836-115">Visual Studio ile uygulamalarınızı doğrudan seçilen Docker ortamında geliştirebilir, çalıştırabilir ve doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6836-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="b6836-116">Uygulamanızı doğrudan docker ana bilgisayarda hata ayıklamak için F5 tuşuna basın veya kapsayıcıyı yeniden oluşturmadan uygulamanızı düzenleyip yenilemek için Ctrl+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6836-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="b6836-117">Windows geliştiricilerinin Linux veya Windows için Docker kapsayıcıları oluşturması en basit ve en güçlü seçimdir.</span><span class="sxs-lookup"><span data-stu-id="b6836-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="b6836-118">Mac için Visual Studio (Mac geliştirme makinesi)</span><span class="sxs-lookup"><span data-stu-id="b6836-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="b6836-119">Docker tabanlı uygulamalar geliştirirken [Mac için Visual Studio'yu](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6836-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="b6836-120">Mac için Visual Studio, Mac için Visual Studio Code ile karşılaştırıldığında daha zengin bir IDE sunar.</span><span class="sxs-lookup"><span data-stu-id="b6836-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="b6836-121">Dil ve çerçeve seçimleri</span><span class="sxs-lookup"><span data-stu-id="b6836-121">Language and framework choices</span></span>

<span data-ttu-id="b6836-122">En modern dillere sahip Microsoft araçlarını kullanarak Docker uygulamaları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6836-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="b6836-123">Aşağıdaki bir başlangıç listesidir, ancak bununla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="b6836-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="b6836-124">.NET Core ve ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b6836-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="b6836-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="b6836-125">Node.js</span></span>
- <span data-ttu-id="b6836-126">Başlayın</span><span class="sxs-lookup"><span data-stu-id="b6836-126">Go</span></span>
- <span data-ttu-id="b6836-127">Java</span><span class="sxs-lookup"><span data-stu-id="b6836-127">Java</span></span>
- <span data-ttu-id="b6836-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="b6836-128">Ruby</span></span>
- <span data-ttu-id="b6836-129">Python</span><span class="sxs-lookup"><span data-stu-id="b6836-129">Python</span></span>

<span data-ttu-id="b6836-130">Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6836-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b6836-131">[Önceki](deploy-azure-kubernetes-service.md)
>[Sonraki](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b6836-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
