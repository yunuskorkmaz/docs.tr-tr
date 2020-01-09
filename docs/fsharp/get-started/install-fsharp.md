---
title: F# yükleme
description: Farklı yollarla nasıl yükleneceğini F# öğrenin.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346562"
---
# <a name="install-f"></a><span data-ttu-id="36381-103">F\# 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="36381-103">Install F\#</span></span>

<span data-ttu-id="36381-104">Ortamınıza bağlı olarak F# birden çok şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36381-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="36381-105">Visual F# Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="36381-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="36381-106">[Visual Studio 'yu](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ilk kez indiriyorsanız, önce Visual Studio yükleyicisi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="36381-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="36381-107">Yükleyiciden uygun Visual Studio sürümünü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="36381-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="36381-108">Zaten Visual Studio yüklüyse, eklemek F# istediğiniz sürümün yanındaki **Değiştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="36381-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="36381-109">Iş yükleri sayfasında, ASP.NET Core projelerine yönelik ve .NET Core desteği içeren F# **ASP.net ve Web geliştirme** iş yükünü seçin.</span><span class="sxs-lookup"><span data-stu-id="36381-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="36381-110">Seçtiğiniz her şeyi yüklemek için sağ alt köşedeki **Değiştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="36381-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="36381-111">Ardından Visual Studio Yükleyicisi 'de **Başlat** ' ı seçerek F# Visual Studio 'yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36381-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="36381-112">Visual Studio Code F# ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="36381-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="36381-113">[Git](https://git-scm.com/download) ' in yüklü olduğundan ve yolunuzda kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="36381-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="36381-114">Bir komut istemine `git --version` girerek ve **ENTER**tuşuna basarak doğru şekilde yüklendiğini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36381-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="36381-115">[.NET Core SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Code](https://code.visualstudio.com)yükler.</span><span class="sxs-lookup"><span data-stu-id="36381-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="36381-116">Uzantılar simgesini seçin ve "ıonıde" araması yapın:</span><span class="sxs-lookup"><span data-stu-id="36381-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="36381-117">Visual Studio Code ' de destek için F# gereken tek eklenti [ıonıde-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)' dir.</span><span class="sxs-lookup"><span data-stu-id="36381-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="36381-118">Ancak, [paket](https://fsprojects.github.io/Paket/) desteğini almak için [sahte](https://fake.build/) destek ve [ıonıde-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) sağlamak üzere [ıonıde-sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ' i de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36381-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="36381-119">SAHTE ve paket, sırasıyla F# projeler oluşturmaya ve bağımlılıkları yönetmeye yönelik ek topluluk araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="36381-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="36381-120">Mac için Visual Studio F# ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="36381-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="36381-121">F#, seçtiğiniz yapılandırma bağımsız olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)varsayılan olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="36381-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="36381-122">Yüklemesi tamamlandıktan sonra **Visual Studio 'Yu Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="36381-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="36381-123">Ayrıca, macOS 'ta Finder aracılığıyla Visual Studio 'Yu açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36381-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="36381-124">Derleme F# sunucusuna yüklensin</span><span class="sxs-lookup"><span data-stu-id="36381-124">Install F# on a build server</span></span>

<span data-ttu-id="36381-125">.NET Core veya .NET SDK aracılığıyla .NET Framework kullanıyorsanız, derleme sunucunuza .NET SDK 'yı yüklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="36381-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="36381-126">İhtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="36381-126">It has everything you need.</span></span>

<span data-ttu-id="36381-127">.NET Framework kullanıyorsanız ve .NET **SDK kullanmıyorsanız,** [Visual Studio derleme araçları SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 'sunu Windows Server 'a yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36381-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="36381-128">Yükleyicide, **.net masaüstü derleme araçları**' nı seçin ve ardından yükleyici menüsünün sağ tarafındaki  **F# derleyici** bileşenini seçin.</span><span class="sxs-lookup"><span data-stu-id="36381-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
