---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72526782"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="0e82f-101">Yükleme yönergeleri-Visual Studio Yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="0e82f-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="0e82f-102">**Visual Studio Yükleyicisi** **.net Compiler Platform SDK 'sını** bulmanın iki farklı yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="0e82f-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="0e82f-103">Visual Studio Yükleyicisi Iş yükleri görünümünü kullanarak yükler</span><span class="sxs-lookup"><span data-stu-id="0e82f-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="0e82f-104">.NET Compiler Platform SDK, Visual Studio uzantısı geliştirme iş yükünün bir parçası olarak otomatik olarak seçilmemiş.</span><span class="sxs-lookup"><span data-stu-id="0e82f-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="0e82f-105">Bunu isteğe bağlı bir bileşen olarak seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e82f-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="0e82f-106">**Visual Studio yükleyicisi** Çalıştır</span><span class="sxs-lookup"><span data-stu-id="0e82f-106">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="0e82f-107">**Değiştir** 'i seçin</span><span class="sxs-lookup"><span data-stu-id="0e82f-107">Select **Modify**</span></span>
1. <span data-ttu-id="0e82f-108">**Visual Studio uzantısı geliştirme** iş yükünü denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0e82f-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="0e82f-109">Özet ağacında **Visual Studio uzantısı geliştirme** düğümünü açın.</span><span class="sxs-lookup"><span data-stu-id="0e82f-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="0e82f-110">**.Net Compiler Platform SDK 'sı**kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="0e82f-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="0e82f-111">En son isteğe bağlı bileşenler altında bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0e82f-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="0e82f-112">İsteğe bağlı olarak, **dgml düzenleyicisinin** grafikleri görselleştiricide görüntülemesini de istersiniz:</span><span class="sxs-lookup"><span data-stu-id="0e82f-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="0e82f-113">Özet ağacındaki **bireysel bileşenler** düğümünü açın.</span><span class="sxs-lookup"><span data-stu-id="0e82f-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="0e82f-114">**Dgml Düzenleyicisi** kutusunu işaretleyin</span><span class="sxs-lookup"><span data-stu-id="0e82f-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="0e82f-115">Visual Studio Yükleyicisi bireysel bileşenler sekmesini kullanarak yükler</span><span class="sxs-lookup"><span data-stu-id="0e82f-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="0e82f-116">**Visual Studio yükleyicisi** Çalıştır</span><span class="sxs-lookup"><span data-stu-id="0e82f-116">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="0e82f-117">**Değiştir** 'i seçin</span><span class="sxs-lookup"><span data-stu-id="0e82f-117">Select **Modify**</span></span>
1. <span data-ttu-id="0e82f-118">**Ayrı bileşenler** sekmesini seçin</span><span class="sxs-lookup"><span data-stu-id="0e82f-118">Select the **Individual components** tab</span></span>
1. <span data-ttu-id="0e82f-119">**.Net Compiler Platform SDK 'sı**kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="0e82f-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="0e82f-120">Bu dosyayı **derleyiciler, derleme araçları ve çalışma zamanları** bölümünün altında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e82f-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="0e82f-121">İsteğe bağlı olarak, **dgml düzenleyicisinin** grafikleri görselleştiricide görüntülemesini de istersiniz:</span><span class="sxs-lookup"><span data-stu-id="0e82f-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="0e82f-122">**Dgml Düzenleyicisi**kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="0e82f-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="0e82f-123">Bunu **kod araçları** bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e82f-123">You'll find it under the **Code tools** section.</span></span>
