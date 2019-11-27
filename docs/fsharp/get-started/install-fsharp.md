---
title: F# yükleme
description: Ortamınıza göre yüklemeyi F# öğrenin.
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204867"
---
# <a name="install-f"></a><span data-ttu-id="d7894-103">F\# 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="d7894-103">Install F\#</span></span>

<span data-ttu-id="d7894-104">Ortamınıza bağlı olarak F# birden çok şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7894-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="d7894-105">Visual F# Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="d7894-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="d7894-106">[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ilk kez indiriyorsanız, Ilk olarak Visual Studio yükleyicisi 'ni yükler.</span><span class="sxs-lookup"><span data-stu-id="d7894-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="d7894-107">Yükleyiciden uygun Visual Studio SKU 'sunu yükleme.</span><span class="sxs-lookup"><span data-stu-id="d7894-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="d7894-108">Zaten yüklüyse **Değiştir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d7894-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="d7894-109">Daha sonra Iş yüklerinin bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d7894-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="d7894-110">ASP.NET Core projelerine yönelik destek ve .NET Core desteğini F# yükleyecek **ASP.net ve Web geliştirme '** yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d7894-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="d7894-111">Sonra sağ alt taraftaki **Değiştir** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d7894-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="d7894-112">Bu işlem, seçtiğiniz her şeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="d7894-112">This will install everything you have selected.</span></span> <span data-ttu-id="d7894-113">Ardından Başlat ' a tıklayarak Visual Studio 2017 F# ' i dil desteğiyleaçabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7894-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="d7894-114">Visual Studio Code F# ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="d7894-114">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="d7894-115">İlk olarak, git ' in [yüklü](https://git-scm.com/download) olduğundan ve yolunuzda kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d7894-115">First, ensure you have [git installed](https://git-scm.com/download) and available on your PATH.</span></span> <span data-ttu-id="d7894-116">Bir komut isteminde `git --version` yazarak ve **ENTER**tuşuna basarak, doğru şekilde yüklendiğini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7894-116">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

<span data-ttu-id="d7894-117">Sonra, [.NET Core SDK](https://dotnet.microsoft.com/download)' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="d7894-117">Next, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="d7894-118">Daha sonra [Visual Studio Code](https://code.visualstudio.com) yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7894-118">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="d7894-119">Sonra, uzantılar simgesine tıklayın ve "ıonıde" araması yapın:</span><span class="sxs-lookup"><span data-stu-id="d7894-119">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="d7894-120">Visual Studio Code ' de destek için F# gereken tek eklenti [ıonıde-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)' dir.</span><span class="sxs-lookup"><span data-stu-id="d7894-120">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="d7894-121">Ancak, [paket](https://fsprojects.github.io/Paket/) desteğini almak için [sahte](https://fake.build/) destek ve [ıonıde-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) sağlamak üzere [ıonıde-sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ' i de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7894-121">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="d7894-122">SAHTE ve paket, sırasıyla F# projeler oluşturmaya ve bağımlılıkları yönetmeye yönelik ek topluluk araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="d7894-122">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="d7894-123">Mac için Visual Studio F# ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="d7894-123">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="d7894-124">F#, seçtiğiniz yapılandırma bağımsız olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)varsayılan olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d7894-124">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="d7894-125">Yüklemesi tamamlandıktan sonra, "Visual Studio 'Yu Başlat" ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d7894-125">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="d7894-126">MacOS 'ta Finder aracılığıyla da başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7894-126">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="d7894-127">Derleme F# sunucusuna yüklensin</span><span class="sxs-lookup"><span data-stu-id="d7894-127">Install F# on a Build Server</span></span>

<span data-ttu-id="d7894-128">.NET Core veya .NET SDK aracılığıyla .NET Framework kullanıyorsanız, derleme sunucunuza .NET SDK 'yı yüklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="d7894-128">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="d7894-129">İhtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d7894-129">It has everything you need.</span></span>

<span data-ttu-id="d7894-130">.NET Framework kullanıyorsanız ve .NET **SDK kullanmıyorsanız,** [Visual Studio derleme araçları SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 'sunu Windows sunucunuza yüklemeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="d7894-130">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="d7894-131">Yükleyicide, **.net masaüstü derleme araçları** ' nı seçin ve ardından yükleyici menüsünün sağ tarafındaki  **F# derleyici** bileşenini seçin.</span><span class="sxs-lookup"><span data-stu-id="d7894-131">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
