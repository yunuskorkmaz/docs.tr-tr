---
title: Azure .NET ve .NET Core geliştiricileri için araçlar
description: Windows, Linux ve Mac ortamından Azure .NET kitaplıklarını kullanmaya başlamak için araçları alın.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071943"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="b3e03-103">.NET ve .NET Core Azure geliştiricileri için araçlar</span><span class="sxs-lookup"><span data-stu-id="b3e03-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="b3e03-104">SDK indirme</span><span class="sxs-lookup"><span data-stu-id="b3e03-104">SDK downloads</span></span>

<span data-ttu-id="b3e03-105">.NET için azure kitaplıkları [NuGet paketleri](https://www.nuget.org/packages?q=windowsazureofficial)olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b3e03-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="b3e03-106">Azure hizmeti tarafından düzenlenen yükleme yönergeleri için [API Başvurusu'na](/dotnet/api/overview/azure/?view=azure-dotnet) bakın.</span><span class="sxs-lookup"><span data-stu-id="b3e03-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="b3e03-107">Geliştirme araçları</span><span class="sxs-lookup"><span data-stu-id="b3e03-107">Development tools</span></span>

<span data-ttu-id="b3e03-108">Visual Studio'da birçok Azure hizmeti için araçlama bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3e03-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="b3e03-109">Bazı Azure hizmetlerinin kullanılabilir ek araçları veya emülatörleri vardır( örneğin [Azure Depolama Gezgini).](https://azure.microsoft.com/features/storage-explorer/)</span><span class="sxs-lookup"><span data-stu-id="b3e03-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="b3e03-110">Gerekirse ek araçlar için Azure hizmetinizin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="b3e03-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="b3e03-111">Bu yönergeler işletim sisteminiz için önerilen başlangıç geliştirme ortamını yükler.</span><span class="sxs-lookup"><span data-stu-id="b3e03-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="b3e03-112">Windows</span><span class="sxs-lookup"><span data-stu-id="b3e03-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="b3e03-113">Visual Studio sürümleri 2017 ve daha sonra Azure geliştirme için yerleşik destek var.</span><span class="sxs-lookup"><span data-stu-id="b3e03-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="b3e03-114">Aşağıdaki adımlar, Visual Studio'da Azure geliştirme desteğini etkinleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3e03-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="b3e03-115">Visual Studio 2015 ve daha önceki kullanımlar için <a href="vs2015-install.md">aşağıdaki talimatları uygulayın.</a></span><span class="sxs-lookup"><span data-stu-id="b3e03-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="b3e03-116">Adım 1: Visual Studio 2019 İndir</span><span class="sxs-lookup"><span data-stu-id="b3e03-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="b3e03-117">Visual Studio 2019 yüklüyse bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3e03-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b3e03-118">Visual Studio 2019’u İndirin</span><span class="sxs-lookup"><span data-stu-id="b3e03-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="b3e03-119">Adım 2: İki Azure iş yükünü yükleme</span><span class="sxs-lookup"><span data-stu-id="b3e03-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="b3e03-120">Visual Studio yükleyicisinde Visual Studio'yu yükleyin (veya varolan bir yüklemeyi değiştirin).</span><span class="sxs-lookup"><span data-stu-id="b3e03-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="b3e03-121">*Azure geliştirme* ve *ASP.NET ve web geliştirme* iş yüklerinin seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3e03-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="b3e03-122">Adım 3: Azure'da .NET ile geliştirin</span><span class="sxs-lookup"><span data-stu-id="b3e03-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="b3e03-123">[İlk ASP.NET Core web uygulamanızı Azure App Service'de dağıtarak](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet)başlayın.</span><span class="sxs-lookup"><span data-stu-id="b3e03-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="b3e03-124">Mac OS</span><span class="sxs-lookup"><span data-stu-id="b3e03-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="b3e03-125">Mac için Visual Studio, Azure geliştirme için ihtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b3e03-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="b3e03-126">Adım 1: Mac için Visual Studio'u İndirin</span><span class="sxs-lookup"><span data-stu-id="b3e03-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b3e03-127">Mac için Visual Studio'u İndirin</span><span class="sxs-lookup"><span data-stu-id="b3e03-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="b3e03-128">Yükleme sırasında Azure araçları varsayılan olarak seçilir.</span><span class="sxs-lookup"><span data-stu-id="b3e03-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="b3e03-129">Linux</span><span class="sxs-lookup"><span data-stu-id="b3e03-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="b3e03-130">Visual Studio Code, Linux'ta Azure geliştirme için ihtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b3e03-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="b3e03-131">Adım 1: .NET Core SDK'yı indirin</span><span class="sxs-lookup"><span data-stu-id="b3e03-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="b3e03-132">.NET Core uygulamaları için SDK ve komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="b3e03-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b3e03-133">Karşıdan yükleme .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="b3e03-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="b3e03-134">Adım 2: Görsel Stüdyo Kodu</span><span class="sxs-lookup"><span data-stu-id="b3e03-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="b3e03-135">Windows, Mac ve Linux gibi işletim sistemlerinde .NET Core uygulamalarını düzenle ve hata ayıkla.</span><span class="sxs-lookup"><span data-stu-id="b3e03-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b3e03-136">Visual Studio Kodu İndir</span><span class="sxs-lookup"><span data-stu-id="b3e03-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
