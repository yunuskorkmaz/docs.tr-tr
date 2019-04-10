---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsü destek en önemli geliştirme aracı seçenekleri tanışın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3a2fcbe3b9380083622b6ce72cea4bab17d7c2ea
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318829"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="2a3a7-103">Docker uygulamaları için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="2a3a7-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="2a3a7-104">Geliştirme aracı seçenekleri: IDE veya düzenleyici</span><span class="sxs-lookup"><span data-stu-id="2a3a7-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="2a3a7-105">Tam ve güçlü bir IDE ya da basit ve Çevik Düzenleyicisi, isterseniz olursa olsun Microsoft, Docker uygulamaları geliştirme geldiği zaman işinize yarayacaktır.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="2a3a7-106">Visual Studio Code ve Docker CLI'yı (Mac, Linux ve Windows için platformlar arası araçları)</span><span class="sxs-lookup"><span data-stu-id="2a3a7-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="2a3a7-107">Herhangi bir geliştirme dilini destekleyen basit, platformlar arası bir düzenleyici tercih ederseniz, Visual Studio Code ve Docker CLI'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="2a3a7-108">Bu ürünler, geliştirici iş akışını hızlandırma için kritik bir basit ama güçlü deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="2a3a7-109">"Docker için Mac" veya "Docker için Windows" (geliştirme ortamı) yükleyerek Docker geliştiricileri, Windows veya Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="2a3a7-110">Ayrıca, Visual Studio Code için Docker ile düzenleyiciden Docker komutlarını çalıştırmak dockerfile'ları ve kısayol görevler için IntelliSense uzantıları destekler.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
>
> <span data-ttu-id="2a3a7-111">Visual Studio Code'u indirmek için Git <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="2a3a7-112">Mac ve Windows için Docker'ı indirmek için Git <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="2a3a7-113">Visual Studio ile Docker Araçları (Windows geliştirme makinesi)</span><span class="sxs-lookup"><span data-stu-id="2a3a7-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="2a3a7-114">Visual Studio 2017 (veya üstü) kullanmanızı öneririz etkin yerleşik Docker araçları ile.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="2a3a7-115">Visual Studio ile geliştirin, çalıştırın ve uygulamalarınızı doğrudan seçtiğiniz Docker ortamında doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="2a3a7-116">Uygulamanızda (tek kapsayıcı ya da birden çok kapsayıcı) doğrudan bir Docker konağı hata ayıklamak için F5 tuşuna basın veya düzenleyin ve kapsayıcıyı yeniden derlemeye gerek kalmadan uygulamanızı yenilemek için Ctrl + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="2a3a7-117">Linux veya Windows için Docker kapsayıcıları oluşturmak Windows geliştiricileri için basit ve en güçlü seçenek var.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="2a3a7-118">(Mac geliştirme makinesi) Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a3a7-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="2a3a7-119">Kullanabileceğiniz [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Docker tabanlı uygulamalar geliştirirken.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="2a3a7-120">Mac için Visual Studio Mac için Visual Studio Code için karşılaştırıldığında daha zengin bir IDE sunar.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="2a3a7-121">Dil ve çerçeve seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2a3a7-121">Language and framework choices</span></span>

<span data-ttu-id="2a3a7-122">Microsoft araçları ile modern dilleri kullanarak Docker uygulamaları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="2a3a7-123">İlk bir listesi verilmiştir, ancak kendisine sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="2a3a7-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="2a3a7-124">.NET Core ve ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a3a7-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="2a3a7-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="2a3a7-125">Node.js</span></span>
- <span data-ttu-id="2a3a7-126">Git</span><span class="sxs-lookup"><span data-stu-id="2a3a7-126">Go</span></span>
- <span data-ttu-id="2a3a7-127">Java</span><span class="sxs-lookup"><span data-stu-id="2a3a7-127">Java</span></span>
- <span data-ttu-id="2a3a7-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="2a3a7-128">Ruby</span></span>
- <span data-ttu-id="2a3a7-129">Python</span><span class="sxs-lookup"><span data-stu-id="2a3a7-129">Python</span></span>

<span data-ttu-id="2a3a7-130">Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a3a7-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2a3a7-131">[Önceki](deploy-azure-kubernetes-service.md)
>[İleri](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2a3a7-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
