---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsünü destekleyen en önemli geliştirme aracı seçeneklerini öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 0f71ffa5e6870f45908e4def6577120a17ec744c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295303"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="accfc-103">Docker uygulamaları için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="accfc-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="accfc-104">Geliştirme araçları seçimleri: IDE veya düzenleyici</span><span class="sxs-lookup"><span data-stu-id="accfc-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="accfc-105">Tam ve güçlü bir IDE ya da hafif ve çevik bir düzenleyiciyi tercih ediyorsanız, Microsoft, Docker uygulamaları geliştirmeye ne zaman bahsedildiğinizi de kapsamıştır.</span><span class="sxs-lookup"><span data-stu-id="accfc-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="accfc-106">Visual Studio Code ve Docker CLı (Mac, Linux ve Windows için platformlar arası araçlar)</span><span class="sxs-lookup"><span data-stu-id="accfc-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="accfc-107">Herhangi bir geliştirme dilini destekleyen basit, platformlar arası bir düzenleyiciyi tercih ediyorsanız, Visual Studio Code ve Docker CLı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="accfc-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="accfc-108">Bu ürünler, geliştirici iş akışını hızlandırma açısından kritik olan basit ancak sağlam bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="accfc-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="accfc-109">Docker geliştiricileri, "Docker for Mac" veya "Docker for Windows" (geliştirme ortamı) yükleyerek, tek bir Docker CLı kullanarak hem Windows hem de Linux (çalışma zamanı ortamı) için uygulama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="accfc-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="accfc-110">Ayrıca, Visual Studio Code Dockerfiles için IntelliSense ile Docker uzantılarını ve düzenleyiciden Docker komutlarını çalıştırmak için kısayol görevlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="accfc-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
>
> <span data-ttu-id="accfc-111">Visual Studio Code indirmek için bölümüne gidin <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="accfc-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="accfc-112">Mac ve Windows için Docker indirmek için adresine gidin <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="accfc-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="accfc-113">Visual Studio ile Docker Araçları (Windows geliştirme makinesi)</span><span class="sxs-lookup"><span data-stu-id="accfc-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="accfc-114">Yerleşik Docker Araçları 'nın etkin olduğu Visual Studio 2017 (veya sonraki bir sürümü) kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="accfc-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="accfc-115">Visual Studio ile uygulamalarınızı doğrudan seçilen Docker ortamında geliştirebilir, çalıştırabilir ve doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="accfc-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="accfc-116">Uygulamanızda (tek kapsayıcı veya birden çok kapsayıcı) doğrudan bir Docker konağında hata ayıklamak için F5 tuşuna basın veya kapsayıcıyı yeniden oluşturmak zorunda kalmadan uygulamanızı düzenlemek ve yenilemek için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="accfc-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="accfc-117">Windows geliştiricilerinin Linux veya Windows için Docker Kapsayıcıları oluşturması için kullanabileceğiniz en basit ve en güçlü seçenektir.</span><span class="sxs-lookup"><span data-stu-id="accfc-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="accfc-118">Mac için Visual Studio (Mac geliştirme makinesi)</span><span class="sxs-lookup"><span data-stu-id="accfc-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="accfc-119">Docker tabanlı uygulamalar geliştirirken [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="accfc-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="accfc-120">Mac için Visual Studio, Mac için Visual Studio Code karşılaştırıldığında daha zengin bir IDE sağlar.</span><span class="sxs-lookup"><span data-stu-id="accfc-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="accfc-121">Dil ve çerçeve seçimleri</span><span class="sxs-lookup"><span data-stu-id="accfc-121">Language and framework choices</span></span>

<span data-ttu-id="accfc-122">En modern dillerle Microsoft araçları 'nı kullanarak Docker uygulamaları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="accfc-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="accfc-123">Aşağıda bir başlangıç listesi verilmiştir ancak bunlarla sınırlı değilsiniz:</span><span class="sxs-lookup"><span data-stu-id="accfc-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="accfc-124">.NET Core ve ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="accfc-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="accfc-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="accfc-125">Node.js</span></span>
- <span data-ttu-id="accfc-126">Git</span><span class="sxs-lookup"><span data-stu-id="accfc-126">Go</span></span>
- <span data-ttu-id="accfc-127">Java</span><span class="sxs-lookup"><span data-stu-id="accfc-127">Java</span></span>
- <span data-ttu-id="accfc-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="accfc-128">Ruby</span></span>
- <span data-ttu-id="accfc-129">Python</span><span class="sxs-lookup"><span data-stu-id="accfc-129">Python</span></span>

<span data-ttu-id="accfc-130">Temel olarak, Linux veya Windows 'da Docker tarafından desteklenen tüm modern dilleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="accfc-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="accfc-131">[Önceki](deploy-azure-kubernetes-service.md)İleri
>[](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="accfc-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
