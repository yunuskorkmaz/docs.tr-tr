---
title: F# yükleme
description: "F # ' i çeşitli yollarla nasıl yükleyeceğinizi öğrenin."
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224284"
---
# <a name="install-f"></a><span data-ttu-id="f2cc2-103">F 'yi yükler\#</span><span class="sxs-lookup"><span data-stu-id="f2cc2-103">Install F\#</span></span>

<span data-ttu-id="f2cc2-104">F # ' ı ortamınıza bağlı olarak birden çok şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="f2cc2-105">Visual Studio ile F # 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="f2cc2-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="f2cc2-106">[Visual Studio 'yu](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ilk kez indiriyorsanız, önce Visual Studio yükleyicisi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="f2cc2-107">Yükleyiciden uygun Visual Studio sürümünü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="f2cc2-108">Zaten Visual Studio yüklüyse, F # eklemek istediğiniz sürümün yanındaki **Değiştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="f2cc2-109">Iş yükleri sayfasında, ASP.NET Core projelerine yönelik F # ve .NET Core desteğini içeren **ASP.net ve Web geliştirme** iş yükünü seçin.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="f2cc2-110">Seçtiğiniz her şeyi yüklemek için sağ alt köşedeki **Değiştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="f2cc2-111">Daha sonra, Visual Studio Yükleyicisi 'de **Başlat** ' ı seçerek Visual Studio 'yu F # ile açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="f2cc2-112">Visual Studio Code ile F # 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="f2cc2-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="f2cc2-113">[Git](https://git-scm.com/download) ' in yüklü olduğundan ve yolunuzda kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="f2cc2-114">`git --version`Bir komut istemine girip **ENTER**tuşuna basarak doğru şekilde yüklendiğini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="f2cc2-115">[.NET Core SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Code](https://code.visualstudio.com)yükler.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="f2cc2-116">Uzantılar simgesini seçin ve "ıonıde" araması yapın:</span><span class="sxs-lookup"><span data-stu-id="f2cc2-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="f2cc2-117">Visual Studio Code 'de F # desteği için gereken tek eklenti [ıonıde-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)' dir.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="f2cc2-118">Ancak, [paket](https://fsprojects.github.io/Paket/) desteğini almak için [sahte](https://fake.build/) destek ve [ıonıde-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) sağlamak üzere [ıonıde-sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ' i de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="f2cc2-119">SAHTE ve paket, sırasıyla projeler oluşturmaya ve bağımlılıkları yönetmeye yönelik ek F # topluluk araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="f2cc2-120">Mac için Visual Studio ile F # 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="f2cc2-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="f2cc2-121">F #, seçtiğiniz yapılandırma bağımsız olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)varsayılan olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="f2cc2-122">Yüklemesi tamamlandıktan sonra **Visual Studio 'Yu Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="f2cc2-123">Ayrıca, macOS 'ta Finder aracılığıyla Visual Studio 'Yu açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="f2cc2-124">Yapı sunucusuna F # yükler</span><span class="sxs-lookup"><span data-stu-id="f2cc2-124">Install F# on a build server</span></span>

<span data-ttu-id="f2cc2-125">.NET Core veya .NET SDK aracılığıyla .NET Framework kullanıyorsanız, derleme sunucunuza .NET SDK 'yı yüklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="f2cc2-126">İhtiyacınız olan her şeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-126">It has everything you need.</span></span>

<span data-ttu-id="f2cc2-127">.NET Framework kullanıyorsanız ve .NET **SDK kullanmıyorsanız,** [Visual Studio derleme araçları SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 'sunu Windows Server 'a yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="f2cc2-128">Yükleyicide, **.net masaüstü derleme araçları**' nı seçin ve ardından yükleyici menüsünün sağ tarafındaki **F # derleyici** bileşenini seçin.</span><span class="sxs-lookup"><span data-stu-id="f2cc2-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
