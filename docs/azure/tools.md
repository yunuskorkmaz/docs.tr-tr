---
title: Azure .NET geliştiricileri için Araçlar
description: Azure .NET kitaplıklarını bir Windows, Linux ve Mac ortamından kullanmaya başlamak için Araçları alın.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174955"
---
# <a name="azure-tools-for-developing-with-net"></a><span data-ttu-id="922fc-103">.NET ile geliştirmeye yönelik Azure Araçları</span><span class="sxs-lookup"><span data-stu-id="922fc-103">Azure tools for developing with .NET</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="922fc-104">SDK İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="922fc-104">SDK downloads</span></span>

<span data-ttu-id="922fc-105">.NET için Azure kitaplıkları, [NuGet paketleri](https://www.nuget.org/packages?q=windowsazureofficial)olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="922fc-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="922fc-106">Azure hizmeti tarafından düzenlenen başvuru belgeleri için [API başvurusuna](/dotnet/api/overview/azure/?view=azure-dotnet) bakın.</span><span class="sxs-lookup"><span data-stu-id="922fc-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for reference documentation organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="922fc-107">Geliştirme araçları</span><span class="sxs-lookup"><span data-stu-id="922fc-107">Development tools</span></span>

<span data-ttu-id="922fc-108">Visual Studio, yerleşik birçok Azure hizmeti için araç içerir.</span><span class="sxs-lookup"><span data-stu-id="922fc-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="922fc-109">Bazı Azure hizmetlerinde [Azure Depolama Gezgini](https://azure.microsoft.com/features/storage-explorer/)gibi ek araçlar veya Öykünücüler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="922fc-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="922fc-110">Gerekirse, ek araçlar için Azure hizmetinize yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="922fc-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="922fc-111">Aşağıda tercih ettiğiniz geliştirme ortamınızı seçin.</span><span class="sxs-lookup"><span data-stu-id="922fc-111">Select your preferred development environment below.</span></span>

## <a name="visual-studio-on-windows"></a>[<span data-ttu-id="922fc-112">Windows üzerinde Visual Studio</span><span class="sxs-lookup"><span data-stu-id="922fc-112">Visual Studio on Windows</span></span>](#tab/vs)

<span data-ttu-id="922fc-113">Visual Studio sürüm 2017 ve üzeri, Azure geliştirme için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="922fc-113">Visual Studio version 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="922fc-114">Aşağıdaki adımlarda, Visual Studio 'da Azure geliştirme desteğinin etkinleştirilmesi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="922fc-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="922fc-115">Visual Studio 2015 ve önceki sürümleri için <a href="vs2015-install.md">Bu yönergeleri izleyin</a>.</span><span class="sxs-lookup"><span data-stu-id="922fc-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="922fc-116">1. Adım: Visual Studio 2019 ' i Indirin</span><span class="sxs-lookup"><span data-stu-id="922fc-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="922fc-117">Visual Studio 2019 zaten yüklüyse, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="922fc-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="922fc-118">Visual Studio 2019’u İndirin</span><span class="sxs-lookup"><span data-stu-id="922fc-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="922fc-119">2. Adım: iki Azure iş yükünü yüklerken</span><span class="sxs-lookup"><span data-stu-id="922fc-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="922fc-120">Visual Studio yükleyicisi ' nde, Visual Studio 'Yu (veya var olan bir yüklemeyi değiştirme) yükleme.</span><span class="sxs-lookup"><span data-stu-id="922fc-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="922fc-121">*Azure geliştirme* ve *ASP.net ve Web geliştirme* iş yüklerinin seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="922fc-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="922fc-122">3. Adım: Azure 'da .NET ile geliştirme</span><span class="sxs-lookup"><span data-stu-id="922fc-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="922fc-123">[İlk ASP.NET Core Web uygulamanızı Azure App Service dağıtmaya](/azure/app-service-web/app-service-web-get-started-dotnet)başlayın.</span><span class="sxs-lookup"><span data-stu-id="922fc-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="visual-studio-code-cross-platform"></a>[<span data-ttu-id="922fc-124">Visual Studio Code (platformlar arası)</span><span class="sxs-lookup"><span data-stu-id="922fc-124">Visual Studio Code (cross-platform)</span></span>](#tab/vscode)

<span data-ttu-id="922fc-125">Visual Studio Code platformlar arası Azure geliştirme için ihtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="922fc-125">Visual Studio Code has everything you need for cross-platform Azure development.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="922fc-126">1. Adım: .NET Core SDK Indirin</span><span class="sxs-lookup"><span data-stu-id="922fc-126">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="922fc-127">.NET Core uygulamaları için SDK ve komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="922fc-127">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="922fc-128">.NET Core SDK indir</span><span class="sxs-lookup"><span data-stu-id="922fc-128">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="922fc-129">2. Adım: Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="922fc-129">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="922fc-130">Herhangi bir işletim sisteminde .NET Core uygulamalarını düzenleyin ve hatalarını ayıklayın: Windows, Mac ve Linux.</span><span class="sxs-lookup"><span data-stu-id="922fc-130">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="922fc-131">Visual Studio Code indir</span><span class="sxs-lookup"><span data-stu-id="922fc-131">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a><span data-ttu-id="922fc-132">3. Adım: Azure Araçları uzantısı</span><span class="sxs-lookup"><span data-stu-id="922fc-132">Step 3: Azure Tools extension</span></span>

<span data-ttu-id="922fc-133">Azure Araçları uzantısını Visual Studio Code ' ye yükler.</span><span class="sxs-lookup"><span data-stu-id="922fc-133">Install the Azure Tools extension in Visual Studio Code.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="922fc-134">Azure Araçları uzantısını yükler</span><span class="sxs-lookup"><span data-stu-id="922fc-134">Install Azure Tools extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a><span data-ttu-id="922fc-135">4. Adım: Azure 'da .NET ile geliştirme</span><span class="sxs-lookup"><span data-stu-id="922fc-135">Step 4: Develop with .NET on Azure</span></span>

<span data-ttu-id="922fc-136">[Linux üzerinde Azure App Service üzerinde ilk ASP.NET Core Web uygulamanızı dağıtmaya](/azure/app-service/containers/quickstart-dotnetcore)başlayın.</span><span class="sxs-lookup"><span data-stu-id="922fc-136">Get started by [deploying your first ASP.NET Core web app on Azure App Service on Linux](/azure/app-service/containers/quickstart-dotnetcore).</span></span>

---
