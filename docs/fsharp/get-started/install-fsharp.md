---
title: "F #'ı yükleme"
description: 'F # ortamınıza bağlı olarak yüklemeyi öğrenin.'
ms.date: 07/03/2018
ms.openlocfilehash: 142265a95e1d3ee1603a89f650a24c6a45709181
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37878772"
---
# <a name="install-f"></a><span data-ttu-id="0ad13-103">F #'ı yükleme</span><span class="sxs-lookup"><span data-stu-id="0ad13-103">Install F#</span></span> #

<span data-ttu-id="0ad13-104">F # birden çok yolla, ortamınıza bağlı olarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad13-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="0ad13-105">F # ile Visual Studio'yu yükleyin</span><span class="sxs-lookup"><span data-stu-id="0ad13-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="0ad13-106">Karşıdan yükleme, [Visual Studio](https://visualstudio.microsoft.com/) ilk kez, Visual Studio yükleyicisi ilk yükler.</span><span class="sxs-lookup"><span data-stu-id="0ad13-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="0ad13-107">Uygun SKU, Visual Studio Yükleyicisi'nden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad13-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="0ad13-108">Yüklü zaten varsa tıklayın **Değiştir**.</span><span class="sxs-lookup"><span data-stu-id="0ad13-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="0ad13-109">Sonraki iş yüklerinin bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="0ad13-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="0ad13-110">Seçin **ASP.NET ve web geliştirme**, F # desteği, .NET Core desteği yükler ve ASP.NET Core için destek F # projeleri.</span><span class="sxs-lookup"><span data-stu-id="0ad13-110">Select **ASP.NET and web development**, which will install F# support, .NET Core support, and F# support for ASP.NET Core projects.</span></span>

<span data-ttu-id="0ad13-111">Ardından, **Değiştir** alt sağ tarafındaki.</span><span class="sxs-lookup"><span data-stu-id="0ad13-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="0ad13-112">Bu, seçtiğiniz her şeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="0ad13-112">This will install everything you have selected.</span></span> <span data-ttu-id="0ad13-113">Ardından Visual Studio 2017 F # dil desteğiyle tıklayarak açabileceğiniz **başlatma**.</span><span class="sxs-lookup"><span data-stu-id="0ad13-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="0ad13-114">F # Mac için Visual Studio ile yükleme</span><span class="sxs-lookup"><span data-stu-id="0ad13-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="0ad13-115">F # yüklendiğinde varsayılan olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/), hangi yapılandırma ne olursa olsun, seçin.</span><span class="sxs-lookup"><span data-stu-id="0ad13-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), no matter what configuration you choose.</span></span>

<span data-ttu-id="0ad13-116">Yükleme tamamlandıktan sonra "Visual Studio Başlat"'i seçin.</span><span class="sxs-lookup"><span data-stu-id="0ad13-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="0ad13-117">Ayrıca bu Bulucu Macos'ta başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad13-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="0ad13-118">F # ile Visual Studio Code'u yükleyin</span><span class="sxs-lookup"><span data-stu-id="0ad13-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="0ad13-119">Olması gerekir [yüklü git](https://git-scm.com/download) ve yapmak için PATH üzerindeki Ionide içinde proje şablonları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ad13-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="0ad13-120">Doğru yazarak yüklendiğinden emin olun `git --version` bir komut istemi ve tuşlarına basarak **Enter**.</span><span class="sxs-lookup"><span data-stu-id="0ad13-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="0ad13-121">macOS</span><span class="sxs-lookup"><span data-stu-id="0ad13-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="0ad13-122">Ionide kullanan [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="0ad13-122">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="0ad13-123">Homebrew Macos'ta Mono yükleme için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="0ad13-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="0ad13-124">Yalnızca, terminale aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="0ad13-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="0ad13-125">Ayrıca yüklemelisiniz [.NET Core SDK'sı](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="0ad13-125">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="0ad13-126">Linux</span><span class="sxs-lookup"><span data-stu-id="0ad13-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="0ad13-127">Linux üzerinde de Ionide kullanır [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="0ad13-127">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="0ad13-128">Debian veya Ubuntu'da üzerinde kullanıyorsanız aşağıdakileri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ad13-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="0ad13-129">Ayrıca yüklemelisiniz [.NET Core SDK'sı](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="0ad13-129">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="0ad13-130">Windows</span><span class="sxs-lookup"><span data-stu-id="0ad13-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="0ad13-131">Windows üzerinde kullanıyorsanız yapmanız gerekenler [F # desteği ile Visual Studio yükleme](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="0ad13-131">If you're on Windows, you must [install Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="0ad13-132">Bu, yazma, derleme ve F # kodu yürütmek için gereken tüm bileşenleri yükler.</span><span class="sxs-lookup"><span data-stu-id="0ad13-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="0ad13-133">Ayrıca yüklemelisiniz [.NET Core SDK'sı](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="0ad13-133">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="0ad13-134">Daha sonra ihtiyacınız olacak [Visual Studio Code](https://code.visualstudio.com) yüklü.</span><span class="sxs-lookup"><span data-stu-id="0ad13-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="0ad13-135">Ardından, "Ionide" için arama ve uzantıları simgesine tıklayın:</span><span class="sxs-lookup"><span data-stu-id="0ad13-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="0ad13-136">Visual Studio code'da F # desteği için gerekli yalnızca eklenti [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="0ad13-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="0ad13-137">Ancak, da yükleyebilirsiniz [Ionide sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) almak için [sahte](https://fsharp.github.io/FAKE/) desteklemek ve [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [Paket](https://fsprojects.github.io/Paket/) destekler.</span><span class="sxs-lookup"><span data-stu-id="0ad13-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="0ad13-138">SAHTE ve Paket projeleri derleme ve bağımlılıkları, sırasıyla yönetmek için ek F # topluluğu araçlar.</span><span class="sxs-lookup"><span data-stu-id="0ad13-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>