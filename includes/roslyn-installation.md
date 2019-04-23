---
ms.openlocfilehash: 72acd0029d0189de1c724856572957f111b9d18f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805316"
---
## <a name="installation-instructions"></a><span data-ttu-id="4c649-101">Yükleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4c649-101">Installation instructions</span></span> 

<span data-ttu-id="4c649-102">Bulmak için iki farklı yolu vardır **.NET derleyici Platformu SDK'sı** içinde **Visual Studio yükleyicisi**:</span><span class="sxs-lookup"><span data-stu-id="4c649-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-workloads-view"></a><span data-ttu-id="4c649-103">İş yükleri görünümünü kullanarak yükleme</span><span class="sxs-lookup"><span data-stu-id="4c649-103">Install using the Workloads view</span></span>

<span data-ttu-id="4c649-104">.NET derleyici Platformu SDK'sı, Visual Studio uzantısı geliştirme iş yükünün parçası otomatik olarak seçili değildir.</span><span class="sxs-lookup"><span data-stu-id="4c649-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="4c649-105">İsteğe bağlı bir bileşen seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4c649-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="4c649-106">Çalıştırma **Visual Studio yükleyicisi**</span><span class="sxs-lookup"><span data-stu-id="4c649-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="4c649-107">Seçin **değiştirme**</span><span class="sxs-lookup"><span data-stu-id="4c649-107">Select **Modify**</span></span> 
1. <span data-ttu-id="4c649-108">Denetleme **Visual Studio uzantısı geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="4c649-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="4c649-109">Açık **Visual Studio uzantısı geliştirme** Özet ağaç düğümü.</span><span class="sxs-lookup"><span data-stu-id="4c649-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="4c649-110">İçin kutuyu **.NET derleyici Platformu SDK'sı**.</span><span class="sxs-lookup"><span data-stu-id="4c649-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="4c649-111">Bu son isteğe bağlı bileşenler altında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c649-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="4c649-112">Bunu Ayrıca isteğe bağlı olarak, istersiniz **DGML düzenleyici** görselleştiricisindeki grafikleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="4c649-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="4c649-113">Açık **tek tek bileşenler** Özet ağaç düğümü.</span><span class="sxs-lookup"><span data-stu-id="4c649-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="4c649-114">İçin kutuyu **DGML Düzenleyici**</span><span class="sxs-lookup"><span data-stu-id="4c649-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-individual-components-tab"></a><span data-ttu-id="4c649-115">Bağımsız bileşenler sekmesinde kullanarak yükleme</span><span class="sxs-lookup"><span data-stu-id="4c649-115">Install using the Individual components tab</span></span>

1. <span data-ttu-id="4c649-116">Çalıştırma **Visual Studio yükleyicisi**</span><span class="sxs-lookup"><span data-stu-id="4c649-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="4c649-117">Seçin **değiştirme**</span><span class="sxs-lookup"><span data-stu-id="4c649-117">Select **Modify**</span></span> 
1. <span data-ttu-id="4c649-118">Seçin **tek tek bileşenler** sekmesi</span><span class="sxs-lookup"><span data-stu-id="4c649-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="4c649-119">İçin kutuyu **.NET derleyici Platformu SDK'sı**.</span><span class="sxs-lookup"><span data-stu-id="4c649-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="4c649-120">Üst altında bulabilirsiniz **derleyiciler, derleme araçları ve çalışma zamanları** bölümü.</span><span class="sxs-lookup"><span data-stu-id="4c649-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="4c649-121">Bunu Ayrıca isteğe bağlı olarak, istersiniz **DGML düzenleyici** görselleştiricisindeki grafikleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="4c649-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="4c649-122">İçin kutuyu **DGML düzenleyici**.</span><span class="sxs-lookup"><span data-stu-id="4c649-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="4c649-123">Bunun altında bulabilirsiniz **kod Araçları** bölümü.</span><span class="sxs-lookup"><span data-stu-id="4c649-123">You'll find it under the **Code tools** section.</span></span>
