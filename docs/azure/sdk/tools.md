---
title: Azure .NET ve .NET Core geliştiricileri için Araçlar
description: Azure .NET kitaplıklarını bir Windows, Linux ve Mac ortamından kullanmaya başlamak için Araçları alın.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071943"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="60ca6-103">.NET ve .NET Core Azure geliştiricileri için Araçlar</span><span class="sxs-lookup"><span data-stu-id="60ca6-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="60ca6-104">SDK İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="60ca6-104">SDK downloads</span></span>

<span data-ttu-id="60ca6-105">.NET için Azure kitaplıkları, [NuGet paketleri](https://www.nuget.org/packages?q=windowsazureofficial)olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="60ca6-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="60ca6-106">Azure hizmeti tarafından düzenlenen yükleme yönergeleri için [API başvurusuna](/dotnet/api/overview/azure/?view=azure-dotnet) bakın.</span><span class="sxs-lookup"><span data-stu-id="60ca6-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="60ca6-107">Geliştirme araçları</span><span class="sxs-lookup"><span data-stu-id="60ca6-107">Development tools</span></span>

<span data-ttu-id="60ca6-108">Visual Studio, yerleşik birçok Azure hizmeti için araç içerir.</span><span class="sxs-lookup"><span data-stu-id="60ca6-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="60ca6-109">Bazı Azure hizmetlerinde [Azure Depolama Gezgini](https://azure.microsoft.com/features/storage-explorer/)gibi ek araçlar veya Öykünücüler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="60ca6-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="60ca6-110">Gerekirse, ek araçlar için Azure hizmetinize yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="60ca6-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="60ca6-111">Bu yönergeler, işletim sisteminiz için önerilen başlangıç geliştirme ortamını yükler.</span><span class="sxs-lookup"><span data-stu-id="60ca6-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="60ca6-112">Windows</span><span class="sxs-lookup"><span data-stu-id="60ca6-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="60ca6-113">Visual Studio sürümleri 2017 ve üzeri, Azure geliştirme için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="60ca6-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="60ca6-114">Aşağıdaki adımlarda, Visual Studio 'da Azure geliştirme desteğinin etkinleştirilmesi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="60ca6-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="60ca6-115">Visual Studio 2015 ve önceki sürümleri için <a href="vs2015-install.md">Bu yönergeleri izleyin</a>.</span><span class="sxs-lookup"><span data-stu-id="60ca6-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="60ca6-116">1. Adım: Visual Studio 2019 ' i Indirin</span><span class="sxs-lookup"><span data-stu-id="60ca6-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="60ca6-117">Visual Studio 2019 zaten yüklüyse, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60ca6-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60ca6-118">Visual Studio 2019’u İndirin</span><span class="sxs-lookup"><span data-stu-id="60ca6-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="60ca6-119">2. Adım: iki Azure iş yükünü yüklerken</span><span class="sxs-lookup"><span data-stu-id="60ca6-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="60ca6-120">Visual Studio yükleyicisi ' nde, Visual Studio 'Yu (veya var olan bir yüklemeyi değiştirme) yükleme.</span><span class="sxs-lookup"><span data-stu-id="60ca6-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="60ca6-121">*Azure geliştirme* ve *ASP.net ve Web geliştirme* iş yüklerinin seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="60ca6-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="60ca6-122">3. Adım: Azure 'da .NET ile geliştirme</span><span class="sxs-lookup"><span data-stu-id="60ca6-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="60ca6-123">[İlk ASP.NET Core Web uygulamanızı Azure App Service dağıtmaya](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet)başlayın.</span><span class="sxs-lookup"><span data-stu-id="60ca6-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="60ca6-124">Mac OS</span><span class="sxs-lookup"><span data-stu-id="60ca6-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="60ca6-125">Mac için Visual Studio Azure geliştirme için ihtiyacınız olan her şey vardır.</span><span class="sxs-lookup"><span data-stu-id="60ca6-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="60ca6-126">1. Adım: Indirme Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="60ca6-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60ca6-127">Mac için Visual Studio indir</span><span class="sxs-lookup"><span data-stu-id="60ca6-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="60ca6-128">Yükleme sırasında Azure Araçları varsayılan olarak seçilidir.</span><span class="sxs-lookup"><span data-stu-id="60ca6-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="60ca6-129">Linux</span><span class="sxs-lookup"><span data-stu-id="60ca6-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="60ca6-130">Visual Studio Code, Linux üzerinde Azure geliştirme için ihtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="60ca6-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="60ca6-131">1. Adım: .NET Core SDK Indirin</span><span class="sxs-lookup"><span data-stu-id="60ca6-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="60ca6-132">.NET Core uygulamaları için SDK ve komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="60ca6-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60ca6-133">.NET Core SDK indir</span><span class="sxs-lookup"><span data-stu-id="60ca6-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="60ca6-134">2. Adım: Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="60ca6-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="60ca6-135">Herhangi bir işletim sisteminde .NET Core uygulamalarını düzenleyin ve hatalarını ayıklayın: Windows, Mac ve Linux.</span><span class="sxs-lookup"><span data-stu-id="60ca6-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60ca6-136">Visual Studio Code indir</span><span class="sxs-lookup"><span data-stu-id="60ca6-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
