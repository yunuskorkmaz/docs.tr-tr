---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526782"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="8be3b-101">Yükleme yönergeleri-Visual Studio Yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="8be3b-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="8be3b-102">**Visual Studio Yükleyicisi** **.net Compiler Platform SDK 'sını** bulmanın iki farklı yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="8be3b-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="8be3b-103">Visual Studio Yükleyicisi Iş yükleri görünümünü kullanarak yükler</span><span class="sxs-lookup"><span data-stu-id="8be3b-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="8be3b-104">.NET Compiler Platform SDK, Visual Studio uzantısı geliştirme iş yükünün bir parçası olarak otomatik olarak seçilmemiş.</span><span class="sxs-lookup"><span data-stu-id="8be3b-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="8be3b-105">Bunu isteğe bağlı bir bileşen olarak seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8be3b-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="8be3b-106">**Visual Studio yükleyicisi** Çalıştır</span><span class="sxs-lookup"><span data-stu-id="8be3b-106">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="8be3b-107">**Değiştir** 'i seçin</span><span class="sxs-lookup"><span data-stu-id="8be3b-107">Select **Modify**</span></span>
1. <span data-ttu-id="8be3b-108">**Visual Studio uzantısı geliştirme** iş yükünü denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8be3b-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="8be3b-109">Özet ağacında **Visual Studio uzantısı geliştirme** düğümünü açın.</span><span class="sxs-lookup"><span data-stu-id="8be3b-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="8be3b-110">**.Net Compiler Platform SDK 'sı**kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="8be3b-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="8be3b-111">En son isteğe bağlı bileşenler altında bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8be3b-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="8be3b-112">İsteğe bağlı olarak, **dgml düzenleyicisinin** grafikleri görselleştiricide görüntülemesini de istersiniz:</span><span class="sxs-lookup"><span data-stu-id="8be3b-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="8be3b-113">Özet ağacındaki **bireysel bileşenler** düğümünü açın.</span><span class="sxs-lookup"><span data-stu-id="8be3b-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="8be3b-114">**Dgml Düzenleyicisi** kutusunu işaretleyin</span><span class="sxs-lookup"><span data-stu-id="8be3b-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="8be3b-115">Visual Studio Yükleyicisi bireysel bileşenler sekmesini kullanarak yükler</span><span class="sxs-lookup"><span data-stu-id="8be3b-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="8be3b-116">**Visual Studio yükleyicisi** Çalıştır</span><span class="sxs-lookup"><span data-stu-id="8be3b-116">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="8be3b-117">**Değiştir** 'i seçin</span><span class="sxs-lookup"><span data-stu-id="8be3b-117">Select **Modify**</span></span>
1. <span data-ttu-id="8be3b-118">**Ayrı bileşenler** sekmesini seçin</span><span class="sxs-lookup"><span data-stu-id="8be3b-118">Select the **Individual components** tab</span></span>
1. <span data-ttu-id="8be3b-119">**.Net Compiler Platform SDK 'sı**kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="8be3b-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="8be3b-120">Bu dosyayı **derleyiciler, derleme araçları ve çalışma zamanları** bölümünün altında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8be3b-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="8be3b-121">İsteğe bağlı olarak, **dgml düzenleyicisinin** grafikleri görselleştiricide görüntülemesini de istersiniz:</span><span class="sxs-lookup"><span data-stu-id="8be3b-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="8be3b-122">**Dgml Düzenleyicisi**kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="8be3b-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="8be3b-123">Bunu **kod araçları** bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8be3b-123">You'll find it under the **Code tools** section.</span></span>
