---
title: F# yükleme
description: Ortamınıza göre yüklemeyi F# öğrenin.
ms.date: 09/05/2019
ms.openlocfilehash: dffa30eac0bdb59c85a66dca6cafd62b25daa572
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855797"
---
# <a name="install-f"></a><span data-ttu-id="80def-103">F 'yi yükler\#</span><span class="sxs-lookup"><span data-stu-id="80def-103">Install F\#</span></span>

<span data-ttu-id="80def-104">Ortamınıza bağlı olarak F# birden çok şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80def-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="80def-105">Visual F# Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="80def-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="80def-106">[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ilk kez indiriyorsanız, Ilk olarak Visual Studio yükleyicisi 'ni yükler.</span><span class="sxs-lookup"><span data-stu-id="80def-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="80def-107">Yükleyiciden uygun Visual Studio SKU 'sunu yükleme.</span><span class="sxs-lookup"><span data-stu-id="80def-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="80def-108">Zaten yüklüyse **Değiştir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80def-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="80def-109">Daha sonra Iş yüklerinin bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="80def-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="80def-110">ASP.NET Core projelerine yönelik destek ve .NET Core desteğini F# yükleyecek **ASP.net ve Web geliştirme '** yi seçin.</span><span class="sxs-lookup"><span data-stu-id="80def-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="80def-111">Sonra sağ alt taraftaki **Değiştir** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80def-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="80def-112">Bu işlem, seçtiğiniz her şeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="80def-112">This will install everything you have selected.</span></span> <span data-ttu-id="80def-113">Ardından Başlat ' a tıklayarak Visual Studio 2017 F# ' i dil desteğiyleaçabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80def-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="80def-114">Mac için Visual Studio F# ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="80def-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="80def-115">F#, seçtiğiniz yapılandırma bağımsız olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)varsayılan olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="80def-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="80def-116">Yüklemesi tamamlandıktan sonra, "Visual Studio 'Yu Başlat" ı seçin.</span><span class="sxs-lookup"><span data-stu-id="80def-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="80def-117">MacOS 'ta Finder aracılığıyla da başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80def-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="80def-118">Visual Studio Code F# ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="80def-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="80def-119">Proje şablonlarını kullanabilmeniz için, git ' in sizin YOLUNUZDA [yüklü](https://git-scm.com/download) ve kullanılabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="80def-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="80def-120">Bir komut istemine yazıp `git --version` **ENTER**tuşuna basarak doğru şekilde yüklendiğini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80def-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="80def-121">macOS</span><span class="sxs-lookup"><span data-stu-id="80def-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="80def-122">[Mono](https://www.mono-project.com) , [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80def-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="80def-123">MacOS 'ta mono yüklemenin en kolay yolu homebrew aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="80def-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="80def-124">Yalnızca aşağıdakileri terminalinize yazmanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="80def-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="80def-125">[.NET Core SDK](https://dotnet.microsoft.com/download)de yükler.</span><span class="sxs-lookup"><span data-stu-id="80def-125">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="80def-126">Linux</span><span class="sxs-lookup"><span data-stu-id="80def-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="80def-127">[Mono](https://www.mono-project.com) , [ F# etkileşimli](../tutorials/fsharp-interactive/index.md) destek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80def-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="80def-128">Decan veya Ubuntu kullanıyorsanız, aşağıdakileri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="80def-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="80def-129">[.NET Core SDK](https://dotnet.microsoft.com/download)de yükler.</span><span class="sxs-lookup"><span data-stu-id="80def-129">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="80def-130">Windows</span><span class="sxs-lookup"><span data-stu-id="80def-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="80def-131">[Visual Studio 'yu desteğiyle F# birlikte](#install-f-with-visual-studio)yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="80def-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="80def-132">Bu, kod yazmak, derlemek ve yürütmek F# için gerekli tüm bileşenleri yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="80def-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="80def-133">[.NET Core SDK](https://dotnet.microsoft.com/download)de yükler.</span><span class="sxs-lookup"><span data-stu-id="80def-133">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

---

<span data-ttu-id="80def-134">Daha sonra [Visual Studio Code](https://code.visualstudio.com) yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="80def-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="80def-135">Sonra, uzantılar simgesine tıklayın ve "ıonıde" araması yapın:</span><span class="sxs-lookup"><span data-stu-id="80def-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="80def-136">Visual Studio Code ' de destek için F# gereken tek eklenti [ıonıde-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)' dir.</span><span class="sxs-lookup"><span data-stu-id="80def-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="80def-137">Ancak, [paket](https://fsprojects.github.io/Paket/) desteğini almak için [sahte](https://fsharp.github.io/FAKE/) destek ve [ıonıde-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) sağlamak üzere [ıonıde-sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ' i de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80def-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="80def-138">SAHTE ve paket, sırasıyla F# projeler oluşturmaya ve bağımlılıkları yönetmeye yönelik ek topluluk araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="80def-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="80def-139">Derleme F# sunucusuna yüklensin</span><span class="sxs-lookup"><span data-stu-id="80def-139">Install F# on a Build Server</span></span>

<span data-ttu-id="80def-140">.NET Core veya .NET SDK aracılığıyla .NET Framework kullanıyorsanız, derleme sunucunuza .NET SDK 'yı yüklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="80def-140">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="80def-141">İhtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="80def-141">It has everything you need.</span></span>

<span data-ttu-id="80def-142">.NET Framework kullanıyorsanız ve .NET **SDK kullanmıyorsanız,** [Visual Studio derleme araçları SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 'sunu Windows sunucunuza yüklemeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="80def-142">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="80def-143">Yükleyicide, **.net masaüstü derleme araçları** ' nı seçin ve ardından yükleyici menüsünün sağ tarafındaki  **F# derleyici** bileşenini seçin.</span><span class="sxs-lookup"><span data-stu-id="80def-143">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
