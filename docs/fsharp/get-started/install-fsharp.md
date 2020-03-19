---
title: F# yükleme
description: F#'yi farklı şekillerde nasıl yükleyin öğrenin.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400248"
---
# <a name="install-f"></a><span data-ttu-id="398aa-103">F Yükle\#</span><span class="sxs-lookup"><span data-stu-id="398aa-103">Install F\#</span></span>

<span data-ttu-id="398aa-104">Ortamınıza bağlı olarak F#'yi birden çok şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="398aa-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="398aa-105">Visual Studio ile F# yükle</span><span class="sxs-lookup"><span data-stu-id="398aa-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="398aa-106">[Visual Studio'yu](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ilk kez indiriyorsanız, ilk olarak Visual Studio Installer'ı yükler.</span><span class="sxs-lookup"><span data-stu-id="398aa-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="398aa-107">Yükleyiciden Visual Studio'nun uygun sürümünü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="398aa-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="398aa-108">Visual Studio zaten yüklüyse, F# eklemek istediğiniz sürümün yanında **Değiştir'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="398aa-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="398aa-109">İş Yükleri sayfasında, ASP.NET Core projeleri için F# ve .NET Core desteğini içeren **ASP.NET ve web geliştirme** iş yükünü seçin.</span><span class="sxs-lookup"><span data-stu-id="398aa-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="398aa-110">Seçtiğiniz her şeyi yüklemek için sağ alt köşede **Değiştir'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="398aa-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="398aa-111">Daha sonra Visual Studio Installer **başlat'ı** seçerek F# ile Visual Studio'u açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="398aa-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="398aa-112">Visual Studio Code ile F# yükle</span><span class="sxs-lookup"><span data-stu-id="398aa-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="398aa-113">[Git'in](https://git-scm.com/download) path'inizde yüklü ve kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="398aa-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="398aa-114">Komut istemine girerek `git --version` ve **Enter**tuşuna basarak doğru yüklenmiş olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="398aa-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="398aa-115">[.NET Core SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Kodunu](https://code.visualstudio.com)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="398aa-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="398aa-116">Uzantılar simgesini seçin ve "Ionide" araması yapın:</span><span class="sxs-lookup"><span data-stu-id="398aa-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="398aa-117">Visual Studio Code'da F# desteği için gerekli olan tek eklenti [Ionide-fsharp'dır.](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)</span><span class="sxs-lookup"><span data-stu-id="398aa-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="398aa-118">Ancak, PAKET [desteği](https://fsprojects.github.io/Paket/) almak için [FAKE](https://fake.build/) desteği ve [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [ionide-FAKE'yi](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="398aa-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="398aa-119">FAKE ve Paket, sırasıyla proje oluşturma ve bağımlılıkları yönetmek için ek F# topluluk araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="398aa-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="398aa-120">Mac için Visual Studio ile F# yükleyin</span><span class="sxs-lookup"><span data-stu-id="398aa-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="398aa-121">F# varsayılan olarak [Mac için Visual Studio'da](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), hangi yapılandırmayı seçerseniz seçin yüklüdür.</span><span class="sxs-lookup"><span data-stu-id="398aa-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="398aa-122">Yükleme tamamlandıktan sonra **Görsel Stüdyoyu Başlat'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="398aa-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="398aa-123">Visual Studio'u macOS'ta Finder aracılığıyla da açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="398aa-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="398aa-124">Yapı sunucusuna F# yükleme</span><span class="sxs-lookup"><span data-stu-id="398aa-124">Install F# on a build server</span></span>

<span data-ttu-id="398aa-125">.NET SDK üzerinden .NET Core veya .NET Framework kullanıyorsanız, yapı sunucunuza .NET SDK'yı yüklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="398aa-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="398aa-126">İhtiyacın olan her şey var.</span><span class="sxs-lookup"><span data-stu-id="398aa-126">It has everything you need.</span></span>

<span data-ttu-id="398aa-127">.NET Framework kullanıyorsanız ve .NET SDK kullanmıyorsanız, [Visual Studio Build Tools SKU'yu](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) Windows Server'ınıza yüklemeniz gerekir. **not**</span><span class="sxs-lookup"><span data-stu-id="398aa-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="398aa-128">Yükleyicide **.NET masaüstü oluşturma araçlarını**seçin ve ardından yükleyici menüsünün sağ tarafındaki **F# derleyici** bileşenini seçin.</span><span class="sxs-lookup"><span data-stu-id="398aa-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
