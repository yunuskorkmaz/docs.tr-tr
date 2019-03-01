---
title: YüklemeF#
description: Yüklemeyi öğrenin F# ortamınıza bağlı.
ms.date: 08/28/2018
ms.openlocfilehash: 873d3021ba884ec81992469e5d0f3b7c18b1e0f4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975257"
---
# <a name="install-f"></a><span data-ttu-id="fd72c-103">F yükleyin\#</span><span class="sxs-lookup"><span data-stu-id="fd72c-103">Install F\#</span></span>

<span data-ttu-id="fd72c-104">Yükleyebileceğiniz F# ortamınıza bağlı olarak birden çok yolla.</span><span class="sxs-lookup"><span data-stu-id="fd72c-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="fd72c-105">Yükleme F# Visual Studio ile</span><span class="sxs-lookup"><span data-stu-id="fd72c-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="fd72c-106">Karşıdan yükleme, [Visual Studio](https://visualstudio.microsoft.com/) ilk kez, Visual Studio yükleyicisi ilk yükler.</span><span class="sxs-lookup"><span data-stu-id="fd72c-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="fd72c-107">Uygun SKU, Visual Studio Yükleyicisi'nden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fd72c-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="fd72c-108">Yüklü zaten varsa tıklayın **Değiştir**.</span><span class="sxs-lookup"><span data-stu-id="fd72c-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="fd72c-109">Sonraki iş yüklerinin bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fd72c-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="fd72c-110">Seçin **ASP.NET ve web geliştirme** hangi yükleme F# desteği ve .NET Core, ASP.NET Core projeleri için destek.</span><span class="sxs-lookup"><span data-stu-id="fd72c-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="fd72c-111">Ardından, **Değiştir** alt sağ tarafındaki.</span><span class="sxs-lookup"><span data-stu-id="fd72c-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="fd72c-112">Bu, seçtiğiniz her şeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="fd72c-112">This will install everything you have selected.</span></span> <span data-ttu-id="fd72c-113">Daha sonra Visual Studio 2017 ile açabilirsiniz F# tıklayarak dil desteği **başlatma**.</span><span class="sxs-lookup"><span data-stu-id="fd72c-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="fd72c-114">Yükleme F# Mac için Visual Studio ile</span><span class="sxs-lookup"><span data-stu-id="fd72c-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="fd72c-115">F#Varsayılan olarak yüklü [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/), seçtiğiniz yapılandırma ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="fd72c-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), no matter which configuration you choose.</span></span>

<span data-ttu-id="fd72c-116">Yükleme tamamlandıktan sonra "Visual Studio Başlat"'i seçin.</span><span class="sxs-lookup"><span data-stu-id="fd72c-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="fd72c-117">Ayrıca bu Bulucu Macos'ta başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd72c-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="fd72c-118">Yükleme F# Visual Studio Code ile</span><span class="sxs-lookup"><span data-stu-id="fd72c-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="fd72c-119">Olması gerekir [yüklü git](https://git-scm.com/download) ve kullanılabilir hale getirmek için yol proje şablonlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd72c-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="fd72c-120">Doğru yazarak yüklendiğinden emin olun `git --version` bir komut istemi ve tuşlarına basarak **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fd72c-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="fd72c-121">macOS</span><span class="sxs-lookup"><span data-stu-id="fd72c-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="fd72c-122">[Mono](https://www.mono-project.com) için kullanılan [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destekler.</span><span class="sxs-lookup"><span data-stu-id="fd72c-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="fd72c-123">Homebrew Macos'ta Mono yükleme için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="fd72c-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="fd72c-124">Yalnızca, terminale aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="fd72c-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="fd72c-125">Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="fd72c-125">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="fd72c-126">Linux</span><span class="sxs-lookup"><span data-stu-id="fd72c-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="fd72c-127">[Mono](https://www.mono-project.com) için kullanılan [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destekler.</span><span class="sxs-lookup"><span data-stu-id="fd72c-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="fd72c-128">Debian veya Ubuntu'da üzerinde kullanıyorsanız aşağıdakileri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fd72c-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="fd72c-129">Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="fd72c-129">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="fd72c-130">Windows</span><span class="sxs-lookup"><span data-stu-id="fd72c-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="fd72c-131">Yükleme [Visual Studio'yla F# Destek](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="fd72c-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="fd72c-132">Bu yazma, derlemek ve çalıştırmak için gereken tüm bileşenleri yükler F# kod.</span><span class="sxs-lookup"><span data-stu-id="fd72c-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="fd72c-133">Ayrıca yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="fd72c-133">Also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="fd72c-134">Daha sonra ihtiyacınız olacak [Visual Studio Code](https://code.visualstudio.com) yüklü.</span><span class="sxs-lookup"><span data-stu-id="fd72c-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="fd72c-135">Ardından, "Ionide" için arama ve uzantıları simgesine tıklayın:</span><span class="sxs-lookup"><span data-stu-id="fd72c-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="fd72c-136">Yalnızca eklenti gereklidir F# desteği Visual Studio code'da [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="fd72c-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="fd72c-137">Ancak, da yükleyebilirsiniz [Ionide sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) almak için [sahte](https://fsharp.github.io/FAKE/) desteklemek ve [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [Paket](https://fsprojects.github.io/Paket/) destekler.</span><span class="sxs-lookup"><span data-stu-id="fd72c-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="fd72c-138">SAHTE ve Paket ek F# projeleri derleme ve bağımlılıkları, sırasıyla yönetmek için topluluk araçları.</span><span class="sxs-lookup"><span data-stu-id="fd72c-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>
