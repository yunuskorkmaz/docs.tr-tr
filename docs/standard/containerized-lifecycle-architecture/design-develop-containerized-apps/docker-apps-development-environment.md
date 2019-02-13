---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsü destek en önemli geliştirme aracı seçenekleri tanışın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 1d22b45a8eee9198d337df9f0b8b4b78371fa31a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220003"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="bbeb7-103">Docker uygulamaları için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="bbeb7-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="bbeb7-104">Geliştirme aracı seçenekleri: IDE veya düzenleyici</span><span class="sxs-lookup"><span data-stu-id="bbeb7-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="bbeb7-105">Tam ve güçlü bir IDE ya da basit ve Çevik Düzenleyicisi, isterseniz olursa olsun Microsoft, Docker uygulamaları geliştirme geldiği zaman işinize yarayacaktır.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="bbeb7-106">Visual Studio Code ve Docker CLI'yı (Mac, Linux ve Windows için platformlar arası araçları)</span><span class="sxs-lookup"><span data-stu-id="bbeb7-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="bbeb7-107">Herhangi bir geliştirme dilini destekleyen basit, platformlar arası bir düzenleyici tercih ederseniz, Visual Studio Code ve Docker CLI'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="bbeb7-108">Bu ürünler, geliştirici iş akışını hızlandırma için kritik bir basit ama güçlü deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="bbeb7-109">"Docker için Mac" veya "Docker için Windows" (geliştirme ortamı) yükleyerek Docker geliştiricileri, Windows veya Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="bbeb7-110">Ayrıca, Visual Studio Code için Docker ile düzenleyiciden Docker komutlarını çalıştırmak dockerfile'ları ve kısayol görevler için IntelliSense uzantıları destekler.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="bbeb7-111">Visual Studio Code'u indirmek için Git <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="bbeb7-112">Mac ve Windows için Docker'ı indirmek için Git <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="bbeb7-113">Visual Studio ile Docker araçları</span><span class="sxs-lookup"><span data-stu-id="bbeb7-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="bbeb7-114">Visual Studio 2015 kullanıyorsanız "Visual Studio için Docker araçları." eklenti araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="bbeb7-115">Visual Studio 2017 için Docker Araçları zaten yerleşik gelir.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="bbeb7-116">Her iki durumda da geliştirin, çalıştırın ve uygulamalarınızı doğrudan seçtiğiniz Docker ortamında doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="bbeb7-117">F5 uygulamanıza (tek kapsayıcı ya da birden çok kapsayıcı) doğrudan bir Docker hata ayıklama ile ana bilgisayar veya düzenleyin ve kapsayıcıyı yeniden derlemeye gerek kalmadan uygulamanızı yenilemek için Ctrl + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="bbeb7-118">Linux veya Windows için Docker kapsayıcıları oluşturma Windows geliştiricileri için basit ve daha güçlü seçenek budur.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="bbeb7-119">Visual Studio için Docker araçları indirmek için Git <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="bbeb7-120">Dil ve çerçeve seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bbeb7-120">Language and framework choices</span></span>

<span data-ttu-id="bbeb7-121">Docker uygulamaları ve Microsoft araçları en modern dilde geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="bbeb7-122">İlk bir listesi verilmiştir, ancak kendisine sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="bbeb7-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="bbeb7-123">.NET Core ve ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bbeb7-123">.NET Core and ASP.NET Core</span></span>
-   <span data-ttu-id="bbeb7-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="bbeb7-124">Node.js</span></span>
-   <span data-ttu-id="bbeb7-125">Golang</span><span class="sxs-lookup"><span data-stu-id="bbeb7-125">Golang</span></span>
-   <span data-ttu-id="bbeb7-126">Java</span><span class="sxs-lookup"><span data-stu-id="bbeb7-126">Java</span></span>
-   <span data-ttu-id="bbeb7-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="bbeb7-127">Ruby</span></span>
-   <span data-ttu-id="bbeb7-128">Python</span><span class="sxs-lookup"><span data-stu-id="bbeb7-128">Python</span></span>

<span data-ttu-id="bbeb7-129">Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbeb7-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bbeb7-130">[Önceki](deploy-azure-kubernetes-service.md)
>[İleri](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bbeb7-130">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>